# ADR-01: Almacenamiento en S3 con Parquet y consultas con DuckDB

**Estado:** Propuesto · **Fecha:** 15/10/2026 · **Responsable:** Francisco Javier Pérez Nava (Data Engineer)

## Contexto

El RFP fija \$0 MXN de operación mensual y pide una base consolidada que se pueda consultar por zona. Los datos son pequeños (decenas o cientos de MB) y se actualizan pocas veces al año. La materia pide usar los servicios gratuitos de AWS.

## Decisión

- **Amazon S3** guarda los datos en tres zonas: `raw/` (descarga original, sin tocar), `clean/` (limpio por fuente) y `curated/` (base consolidada por colonia).
- Los datos limpios y consolidados se guardan en **Parquet**, un formato por columnas, comprimido y con tipos de dato.
- **DuckDB** ejecuta las consultas SQL leyendo el Parquet directamente, sin un servidor de base de datos.

## Alternativas consideradas

| Alternativa | Por qué no |
|---|---|
| Amazon RDS (PostgreSQL + PostGIS) | Instancia encendida todo el tiempo; consume crédito o capa gratuita sin necesidad |
| Amazon Athena + Glue Data Catalog | Cobra por datos escaneados y suma configuración; queda como opción para demostrar servicios AWS si sobra tiempo |
| Solo archivos CSV locales | Sin versionado compartido ni tipos de dato; difícil de reproducir en equipo |

## Consecuencias

- Costo prácticamente \$0 y nada que apagar al terminar.
- Cualquier integrante puede reproducir la base con el mismo comando.
- No hay escrituras concurrentes; no se necesitan para este proyecto.
- Hay que configurar una alerta de presupuesto en AWS desde el hito 0.
