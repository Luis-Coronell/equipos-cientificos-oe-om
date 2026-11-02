# ¿Diversidad, familiaridad o liderazgo? Diseño de equipos científicos e impacto futuro de la investigación en la interfaz entre orientación emprendedora y orientación al mercado

Código, datos derivados y resultados de replicación del artículo cienciométrico de Coronell Quintero, Montoya Restrepo y Cordero (2026), enviado a *DecisionTech Review*.

**Resumen en inglés.** Replication package for a scientometric study of 442 articles (Web of Science + Scopus, 2000–2026) at the interface between entrepreneurial orientation and market orientation. Author histories are rebuilt with OpenAlex using only information available before publication, and three-year citations are modeled for 257 articles with Poisson and OLS estimators.

## Qué contiene

```
notebooks/BibFusion_depurado.ipynb   Cuaderno de Colab completo, en 6 partes
search/equations.md                  Ecuaciones exactas de WoS y Scopus
data/                                Datos derivados (ver data/README.md)
results/tables/                      Los cinco modelos anidados (Poisson y MCO)
results/figures/                     Figuras F1–F7 del artículo (300 dpi)
```

Correspondencia de las figuras con el artículo: `F1` = Figura 1; `F2` = Figura 2; `F5` = Figura 3; `F6` = Figura 4; `F7` = Figura 5; `F3` y `F4` = Figuras S1 y S2 del material suplementario.

## Diseño del análisis

1. **Corpus.** Búsqueda en WoS y Scopus (7 de octubre de 2026), fusión con BibFusion y revisión manual de duplicados: 442 artículos únicos.
2. **Autores.** Identificador único por persona (ORCID, luego OpenAlex, luego nombre normalizado) y descarga de 83.700 trabajos previos desde OpenAlex.
3. **Regla de no información futura.** Los predictores usan trabajos hasta *t*−1; las citas se cuentan de *t*+1 a *t*+3; la ventana debe estar completa (*t*+3 ≤ 2025).
4. **Modelos.** Cinco modelos anidados; el principal es el 4 (N = 257). Poisson con errores robustos y MCO sobre log(1 + citas). Robustez: N = 241 (instituciones) y N = 212 (equipos totalmente identificados).

## Cómo reproducirlo

### Opción A: Google Colab (recomendada)

1. Copie su carpeta de trabajo a Drive con esta estructura: `MyDrive/BibFusion/trabajo_limpio/` con los archivos de `data/`.
2. Abra `notebooks/BibFusion_depurado.ipynb` en Colab (Archivo → Abrir cuaderno → GitHub, o súbalo).
3. Para solo reproducir el análisis final, ejecute las celdas de la **Parte 6** (R, T, K3, U, V) en orden. No llaman a ninguna API.
4. Para reconstruir todo desde cero, ejecute las Partes 1 a 5 con sus propias exportaciones de WoS y Scopus. La Parte 5 consulta la API de OpenAlex y pide un correo para el *polite pool*.

### Opción B: en local

```bash
git clone https://github.com/Luis-Coronell/equipos-cientificos-oe-om.git
cd equipos-cientificos-oe-om
python -m venv .venv && source .venv/bin/activate   # en Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/BibFusion_depurado.ipynb
```

Cambie las rutas de Drive (`/content/drive/MyDrive/BibFusion/...`) por la carpeta local con los datos.

## Resultados clave que debe reproducir

| Resultado (modelo 4, Poisson) | Valor |
|---|---|
| Calidad de la revista, por DE | 1,96 (1,67–2,31) |
| Equipo multinacional | 1,34 (1,04–1,72) |
| Concentración del liderazgo, por DE | 1,17 (1,02–1,34) |
| Proporción de equipos con vínculo previo: solo corpus → con OpenAlex | 11 % → 72 % |

## Licencias

- Código: MIT (`LICENSE`).
- Datos derivados y figuras: CC BY 4.0. Los datos de OpenAlex son CC0.
- No se redistribuyen registros de WoS ni de Scopus.

## Cómo citar

Ver `CITATION.cff`. Cuando el artículo esté publicado, añada el DOI aquí.

## Contacto

Luis Daniel Coronell Quintero · lcoronell@unal.edu.co · ORCID 0009-0009-3294-8502
