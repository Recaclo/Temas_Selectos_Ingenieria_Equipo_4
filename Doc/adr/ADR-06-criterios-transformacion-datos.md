# ADR 006: Selección de AWS Lambda sobre AWS Glue para procesamiento Bronze a Silver

* **Estatus:** Aceptado
* **Fecha:** 2026-11-05
* **Autores:** Equipo 4

## Contexto y Problema
Para la capa de transformación de datos (de `bronze/` a `silver/`), necesitamos procesar e integrar conjuntos de datos públicos de la CDMX (INEGI, Datos Abiertos CDMX y valores catastrales de suelo). 

Debemos justificar técnicamente la elección de la herramienta de procesamiento sin respaldar la decisión únicamente en "ahorro de costos" o gratuidad, evaluando volumetría, límites de ejecución y arquitectura del proyecto.

## Opciones Evaluadas
1. **AWS Lambda (Python sin servidor)**
2. **AWS Glue (ETL administrado / PySpark)**

## Análisis Comparativo de Parámetros

| Criterio | Datos del Proyecto (Estimación Real) | Limitación AWS Lambda | AWS Glue (Spark) |
| :--- | :--- | :--- | :--- |
| **Volumen de datos por corrida** | ~50 MB a 250 MB (CSV / GeoJSON comprimido) | Hasta 10 GB de memoria en ejecución | Diseñado para GBs / TBs de datos masivos |
| **Tiempo estimado de ejecución** | ~45 segundos a 2 minutos por ingesta | Límite estricto de 15 minutos (900s) | Mínimo de arranque ~1-2 min (Glue Jobs) |
| **Modelado de datos** | GeoPandas + Parquet + DuckDB local | Soporta paquetes ligeros mediante Lambda Layers / Container Image | Diseñado para cómputo distribuido (Spark) |
| **Facturación / Costo** | Micro-ejecuciones por milisegundo (nivel gratuito de 1M invocaciones/mes) | ~$0.0000166667 por GB-segundo | Mínimo 1 DPU (Data Processing Unit) cobrado por segundo (mín. 1 min) |

## Decisión
Se decide utilizar **AWS Lambda** para el pipeline de ingesta y transformación de `bronze/` a `silver/`.

### Justificación:
1. **Volumetría acotada:** El volumen total diario o periódico no excede los 300 MB. Lambda maneja este tamaño en memoria en menos de 2 minutos, muy lejos del límite de 15 minutos.
2. **Sin necesidad de cómputo distribuido:** El dataset cabe perfectamente en memoria RAM para procesarse con `pandas`/`geopandas` y convertirse a formato `Parquet`. Añadir el sobrecosto de inicialización de clusters de PySpark en AWS Glue añade latencia innecesaria (~2 minutos solo en levantar el worker).
3. **Arquitectura basada en eventos (Event-Driven):** Lambda encaja de manera nativa con las notificaciones de S3 cuando se sube un nuevo objeto a `bronze/`.

## ¿En qué punto migraríamos a AWS Glue? (Puntos de Cierre / Break-even)
Migraremos la arquitectura de Lambda a AWS Glue únicamente si se cumple cualquiera de las siguientes condiciones:
* **Volumen > 10 GB por archivo:** Si la ingesta de datos crece 100x o requiere procesar históricos completos en paralelo.
* **Tiempo de ejecución > 12 minutos:** Si el cálculo geométrico de colonias y polígonos sobrepasa el límite prudente del timeout de Lambda (15 min).
* **Necesidad de procesado distribuido en memoria (Apache Spark):** Si la transformación requiere `joins` masivos distribuidos que superen la capacidad de la memoria asignada a la Lambda.