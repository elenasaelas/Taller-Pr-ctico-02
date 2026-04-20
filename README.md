
1:
for $item in /RetroGamingVault/Item
where $item/@categoria = "Hardware" 
      and xs:integer($item/AnioLanzamiento) < 1985
order by xs:integer($item/AnioLanzamiento)
return
    <Catalogo>
        <Nombre>{data($item/Nombre)}</Nombre>
        <Fabricante>{data($item/Fabricante)}</Fabricante>
        <Anio>{data($item/AnioLanzamiento)}</Anio>
        <Valor>{data($item/ValorEstimado)} {data($item/ValorEstimado/@moneda)}</Valor>
    </Catalogo>

2:
for $item in /RetroGamingVault/Item
where xs:integer($item/EstadoConservacion) = 5
order by xs:decimal($item/ValorEstimado) descending
return
    <ItemMenta>
        <Nombre>{data($item/Nombre)}</Nombre>
        <Categoria>{data($item/@categoria)}</Categoria>
        <ValorEstimado moneda="{data($item/ValorEstimado/@moneda)}">
            {data($item/ValorEstimado)}
        </ValorEstimado>
    </ItemMenta>

3. 
declare variable $serial as xs:string := "SN-000085#NI";
for $item in /RetroGamingVault/Item
where $item/SerialNumber = $serial
return
    <CertificadoAutenticidad>
        <SerialNumber>{data($item/SerialNumber)}</SerialNumber>
        <Nombre>{data($item/Nombre)}</Nombre>
        <Categoria>{data($item/@categoria)}</Categoria>
        <Fabricante>{data($item/Fabricante)}</Fabricante>
        <AnioLanzamiento>{data($item/AnioLanzamiento)}</AnioLanzamiento>
        <EstadoConservacion>{data($item/EstadoConservacion)}</EstadoConservacion>
        <ValorEstimado moneda="{data($item/ValorEstimado/@moneda)}">
            {data($item/ValorEstimado)}
        </ValorEstimado>
        <Certificacion>Auténtico</Certificacion>
    </CertificadoAutenticidad>
