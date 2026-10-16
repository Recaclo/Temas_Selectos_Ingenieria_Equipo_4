# ADR-04: Índice de potencial de plusvalía con variables normalizadas y pesos por PCA

**Estado:** Propuesto · **Fecha:** 15/10/2026 · **Responsable:** Laura Reyes Carrillo (Data Scientist)

## Contexto

N4 pide que cada zona tenga una puntuación comparable. El cliente necesita entender de dónde sale la calificación, así que el método debe ser explicable y sus pesos, ajustables.

## Decisión

1. Se eligen indicadores por colonia en cuatro dimensiones: **dinámica inmobiliaria** (permisos y nuevos desarrollos), **accesibilidad** (transporte y equipamiento), **perfil sociodemográfico** (cambio en escolaridad, densidad, servicios de la vivienda) y **valor actual** (valor de suelo).
2. Cada indicador se normaliza de 0 a 100 (mín–máx, recortando valores extremos al percentil 1 y 99).
3. Los pesos iniciales salen de un **análisis de componentes principales (PCA)**; después se ajustan con el cliente.
4. Índice = suma ponderada de los indicadores, en escala de 0 a 100.

## Alternativas consideradas

| Alternativa | Por qué no |
|---|---|
| Pesos iguales | Simple, pero ignora que algunas variables se repiten (por ejemplo, densidad y servicios) |
| Usar solo la predicción del modelo | Es una caja negra para el cliente y depende de una sola variable objetivo |

## Consecuencias

- El cliente debe aprobar los pesos antes del 11/11/2026.
- La fórmula y los pesos se publican en el reporte final.
- Se hace un análisis de sensibilidad: cuánto cambia el ranking si se mueve cada peso ±10%.
