# Datos

Esta carpeta se llena con los archivos derivados que usa el análisis final (celdas de la Parte 6 del cuaderno).

## Qué se publica

| Archivo | Contenido | Origen |
|---|---|---|
| `base_modelo_442.csv` | Una fila por artículo con las variables del equipo y las citas a tres años | Parte 5 del cuaderno |
| `equipos_personas_por_articulo.csv` | Personas por artículo (identificador de OpenAlex/ORCID, no nombres completos si se prefiere anonimizar) | Parte 2 |
| `openalex_revistas_442.csv` | Citación media a dos años de las revistas | Parte 5 |
| `openalex_match_442.csv`, `resultado_citas_442.csv`, `personid_openalex.csv` | Emparejamiento con OpenAlex y citas por año | Parte 5 |
| `corpus_principal_442.csv` (**versión reducida**) | Solo `SR`, `year`, `document_type`, DOI y las banderas `ismain_wos`, `ismain_scopus` | Ver abajo |

Los datos de OpenAlex son de dominio público (CC0).

## Qué NO se publica

Las exportaciones originales de Web of Science y Scopus y el corpus con títulos, resúmenes, palabras clave y referencias, porque las licencias de Clarivate y Elsevier restringen su redistribución. Quien quiera reproducir el corpus desde cero debe ejecutar las ecuaciones de `search/equations.md` con su propio acceso institucional y cargar los archivos en la Parte 1 del cuaderno.

## Cómo crear el corpus reducido

En el cuaderno, después de la Parte 2:

```python
cols = ["SR", "year", "document_type", "__doi_norm", "ismain_wos", "ismain_scopus"]
M[cols].to_csv(OUT/"corpus_principal_442.csv", index=False)
```

(El análisis final solo usa `SR`, `year` y las dos banderas de procedencia.)
