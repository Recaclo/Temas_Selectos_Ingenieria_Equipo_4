# ADR-05: Regresión lineal y Gradient Boosting con validación temporal

**Estado:** Propuesto · **Fecha:** 15/10/2026 · **Responsable:** Laura Reyes Carrillo (Data Scientist)

## Contexto

N5 pide estimar el comportamiento del valor a 5 años y reportar métricas de validación. Hay pocos años de datos y unas 1,800 colonias, así que el riesgo de sobreajuste es alto.

## Decisión

- **Modelo base ingenuo:** cada colonia crece igual que su promedio histórico. Cualquier modelo debe superarlo.
- **Regresión lineal** (con regularización Ridge) como modelo principal explicable.
- **Gradient Boosting** (scikit-learn o LightGBM) como alternativa, si mejora claramente al lineal.
- **Validación temporal:** se entrena con los años anteriores y se prueba con los más recientes; nunca se mezclan años futuros en el entrenamiento.
- **Métricas:** MAE, RMSE y R², más un intervalo de predicción por colonia.

## Alternativas consideradas

| Alternativa | Por qué no |
|---|---|
| Validación cruzada aleatoria | Mezcla años y da métricas demasiado optimistas |
| Redes neuronales o modelos de series de tiempo complejos | Pocos datos y difíciles de explicar al cliente |

## Consecuencias

- Las estimaciones se muestran como rangos, no como un número exacto.
- Si ningún modelo supera al ingenuo, se reporta así y el índice (ADR-04) queda como entregable principal.
