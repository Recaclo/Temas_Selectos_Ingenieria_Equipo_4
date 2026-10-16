# Índice de potencial de plusvalía en la CDMX

Proyecto de **Temas Selectos de Ingeniería** (Ingeniería de Datos) — Equipo 4.

¿En qué colonias de la Ciudad de México tiene más potencial de aumentar su valor una propiedad comprada hoy, en un horizonte de cinco años? Este proyecto integra datos públicos de INEGI, Datos Abiertos CDMX y valores catastrales de suelo en una base por colonia. Con ella construye un índice de potencial de plusvalía (0–100), un modelo predictivo a 5 años y un mapa interactivo, usando servicios gratuitos de AWS.

> Los resultados son aproximaciones con fines académicos y de apoyo a la decisión. No son asesoría financiera ni garantía de plusvalía.

## Documentos

| Documento | Descripción |
|---|---|
| [RFP](Doc/Consultoria/RFP.md) | Solicitud de propuesta del cliente (caso de estudio) |
| [SOW](Doc/Consultoria/SOW.md) | Nuestra propuesta: alcance, entregables, plan, riesgos y presupuesto |
| [ADR](Doc/adr/) | Decisiones de arquitectura |

## Equipo

| Integrante | Rol |
|---|---|
| Joshua Rodríguez Zamora | Project Manager |
| Laura Reyes Carrillo | Data Scientist / ML Engineer |
| Francisco Javier Pérez Nava | Data Engineer |
| Héctor Manuel Salazar Rubí | GIS Developer / Backend Engineer |
| Brenda Berenice Cornejo Díaz | Frontend Developer / QA Engineer |

## Calendario

Del 15/10/2026 al 27/11/2026 (6 semanas). Detalle por hito en la [sección 6 del SOW](Doc/Consultoria/SOW.md#6-plan-por-hitos).

## Stack previsto

Python (Pandas, GeoPandas, scikit-learn) · Amazon S3 · Parquet · DuckDB · Streamlit + Folium
