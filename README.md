# Retro Gaming Vault - HTML y XQuery

## Descripción

Este proyecto utiliza XQuery para consultar un documento XML llamado `reto_vault.xml` y generar automáticamente un archivo HTML con los resultados formateados. El archivo resultante (`retro_vault.html`) puede abrirse directamente en un navegador.

Se implementan tres consultas principales:

1. Catálogo interactivo de ítems de tipo "Hardware" lanzados antes de 1985 (La era dorada).
2. Informe de valor de la colección: listado de objetos con estado de conservación 5 (Menta).
3. Buscador por Serial Number que genere una página de "Certificado de Autenticidad" con los datos del ítem.

---

## Consultas implementadas

### Consulta 1: Hardware anterior a 1985

Filtra los elementos cuya categoría sea "Hardware" y cuyo año de lanzamiento sea menor a 1985.
Ordena los resultados por año de lanzamiento de forma ascendente.

Campos mostrados:

* Nombre
* Fabricante
* Año de lanzamiento
* Valor estimado
* Moneda

---

### Consulta 2: Ítems en estado perfecto

Filtra los elementos con estado de conservación igual a 5.
Ordena los resultados por valor estimado de forma descendente.

Campos mostrados:

* Nombre
* Categoría
* Valor estimado

---

### Consulta 3: Búsqueda por número de serie

Busca un ítem específico utilizando una variable:

```xquery
declare variable $serial as xs:string := "SN-000085#NI";
```

Muestra todos los datos relevantes del ítem y añade una etiqueta visual de autenticidad.

Campos mostrados:

* Serial
* Nombre
* Categoría
* Fabricante
* Año de lanzamiento
* Estado de conservación
* Valor estimado
* Moneda

---

## Generación del HTML

El HTML se construye dinámicamente dentro de una variable en XQuery y se guarda utilizando la función `file:write`.

Configuración recomendada:

```xquery
file:write(
  "C:/ruta/proyecto/reto_vault.html",
  $html,
  map {
    "method": "html",
    "html-version": "5.0",
    "indent": "yes",
    "omit-xml-declaration": "yes",
    "encoding": "UTF-8"
  }
)
```

---
## Fuentes utilizadas:
[1] https://www.w3schools.com/

Además del Notebook de la asignatura proporcionada por el docente y el contenido en Classroom.
