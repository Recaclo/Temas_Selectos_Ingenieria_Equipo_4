# ADR-03: Valor unitario de suelo catastral como variable objetivo

**Estado:** Propuesto · **Fecha:** 15/10/2026 · **Responsable:** Laura Reyes Carrillo (Data Scientist)

## Contexto

Para estimar la plusvalía se necesita una serie histórica del valor por zona. El RFP menciona precios de venta y precio por m², pero no hay una fuente pública y gratuita con historia de precios comerciales por colonia. Los portales inmobiliarios no ofrecen historia y sus términos de uso suelen prohibir el scraping.

## Decisión

- La variable a predecir es el **cambio porcentual a 5 años del valor unitario de suelo catastral por colonia** (MXN por m²), publicado cada año en la Gaceta Oficial de la CDMX.
- Si en el hito 1 aparece una fuente abierta de precios de mercado con historia suficiente, se usa para validar que el valor catastral siga la misma tendencia.

## Alternativas consideradas

| Alternativa | Por qué no |
|---|---|
| Precios de portales inmobiliarios | Sin historia, sin permiso de uso y fuera del presupuesto de \$0 |
| Índice de precios de vivienda de SHF | Solo llega a nivel ciudad o alcaldía, no a colonia |
| Sin variable objetivo (solo índice) | No cumpliría N5, que pide un modelo predictivo con métricas |

## Consecuencias

- El valor catastral puede ir rezagado frente al de mercado; se reporta como limitación.
- La estimación se presenta como tendencia relativa entre colonias, no como precio de venta.
- Se debe revisar que los años de valores catastrales usen la misma clasificación de colonias.
