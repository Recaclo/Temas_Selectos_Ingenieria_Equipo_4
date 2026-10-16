# ADR-02: La colonia como unidad geográfica de análisis

**Estado:** Propuesto · **Fecha:** 15/10/2026 · **Responsable:** Héctor Manuel Salazar Rubí (GIS Developer)

## Contexto

El RFP permite trabajar por alcaldía, colonia, AGEB o código postal. Cada fuente viene en una geografía distinta: el censo de INEGI por AGEB, los valores de suelo por colonia y algunos datos de Datos Abiertos CDMX por punto (coordenadas) o por alcaldía.

## Decisión

- La unidad de análisis es la **colonia**, porque es como piensan los inversionistas y es la geografía de los valores catastrales de suelo.
- Los datos de AGEB se reparten a colonias por **intersección espacial ponderada por población**: si el 30% de la población de una AGEB vive dentro de una colonia, esa colonia recibe el 30% de sus conteos.
- Los datos con coordenadas (permisos, establecimientos, estaciones) se asignan a la colonia que los contiene.
- Todo se proyecta a un mismo sistema de coordenadas antes de cruzar capas.

## Alternativas consideradas

| Alternativa | Por qué no |
|---|---|
| AGEB | Más detalle, pero el inversionista no la reconoce y los valores de suelo no vienen por AGEB |
| Código postal | Sus límites no son oficiales para estadística y cambian |
| Alcaldía | Solo 16 unidades: muy pocas para un modelo y oculta las diferencias dentro de cada alcaldía |

## Consecuencias

- Se necesita una tabla de equivalencias AGEB–colonia–alcaldía (entregable del hito 2).
- El reparto por población es una aproximación; se documenta como limitación.
- Si en el hito 1 la cobertura por colonia no alcanza, se cambia la unidad con aviso al cliente.
