# Registro de decisiones de arquitectura (ADR)

Cada ADR documenta una decisión técnica: el contexto, qué decidimos, qué alternativas descartamos y qué consecuencias tiene. Si una decisión cambia, se crea un ADR nuevo que reemplaza al anterior; los viejos no se borran.

| ADR | Decisión | Estado |
|---|---|---|
| [ADR-01](ADR-01-almacenamiento.md) | Almacenamiento en S3 con Parquet y consultas con DuckDB | Propuesto |
| [ADR-02](ADR-02-unidad-geografica.md) | La colonia como unidad geográfica de análisis | Propuesto |
| [ADR-03](ADR-03-variable-objetivo.md) | Valor unitario de suelo catastral como variable objetivo | Propuesto |
| [ADR-04](ADR-04-metodo-indice.md) | Índice con variables normalizadas y pesos por PCA | Propuesto |
| [ADR-05](ADR-05-modelo-validacion.md) | Regresión lineal y Gradient Boosting con validación temporal | Propuesto |

Los ADR pasan a **Aceptado** cuando el cliente los aprueba en el hito 0 (16/10/2026).
