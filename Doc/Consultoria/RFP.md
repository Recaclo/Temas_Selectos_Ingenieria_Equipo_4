# RFP: Plataforma de análisis de plusvalía inmobiliaria en la CDMX

**Cliente:** UrbanaData Consultoría Inmobiliaria  
**Contacto:** Juan Reyes 

**Elaborado por:** 

- CORNEJO DIAZ BRENDA BERENICE
- PEREZ NAVA FRANCISCO JAVIER
- REYES CARRILLO LAURA
- RODRIGUEZ ZAMORA JOSHUA
- SALAZAR RUBI HECTOR MANUEL


**Fecha de publicación:** 07/10/2026  

---

## 1. Quiénes somos

UrbanaData es una empresa dedicada al análisis y asesoramiento para la inversión inmobiliaria en la Ciudad de México.

Nuestro objetivo es ayudar a pequeños y medianos inversionistas a identificar zonas con potencial de crecimiento mediante el análisis de información urbana, sociodemográfica e inmobiliaria.

Actualmente, gran parte de las decisiones de inversión se realizan mediante experiencia, información dispersa y análisis manuales. Buscamos incorporar el uso de datos para respaldar estas decisiones de una manera más objetiva.

---

## 2. El problema

Actualmente no contamos con una fuente centralizada de información que permita analizar y comparar el comportamiento de diferentes colonias y zonas de la Ciudad de México.

La información relevante para tomar una decisión de inversión se encuentra distribuida entre distintas fuentes, como:

- Datos demográficos.
- Información sobre vivienda.
- Desarrollo urbano.
- Permisos de construcción.
- Infraestructura.
- Datos geográficos.
- Información relacionada con precios inmobiliarios.

Esto dificulta responder una pregunta importante para nuestros clientes:

> **¿Qué zonas de la Ciudad de México presentan condiciones favorables para que una propiedad adquirida actualmente aumente su valor durante los próximos cinco años?**

Si no resolvemos este problema, las decisiones de inversión continuarán dependiendo principalmente de análisis manuales y criterios subjetivos, haciendo difícil comparar de manera consistente diferentes zonas de la ciudad.

---

## 3. Qué necesitamos lograr

| # | Necesidad | Cómo sabremos que se cumplió |
|---|---|---|
| N1 | Integrar información inmobiliaria, sociodemográfica y urbana proveniente de diferentes fuentes. | Contar con un conjunto de datos consolidado que permita consultar la información por zona geográfica. |
| N2 | Conocer el comportamiento histórico de variables relacionadas con el valor de las propiedades. | Disponer de información histórica suficiente para identificar tendencias y cambios por zona. |
| N3 | Identificar zonas con características asociadas al crecimiento del valor inmobiliario. | Obtener indicadores comparables para las zonas analizadas. |
| N4 | Crear un índice de potencial de plusvalía. | Cada zona analizada deberá obtener una puntuación que permita compararla con otras zonas. |
| N5 | Estimar el posible comportamiento del valor inmobiliario durante los próximos cinco años. | Generar una estimación utilizando un modelo predictivo y reportar métricas de validación. |
| N6 | Facilitar la interpretación de los resultados. | Contar con una visualización o mapa que permita consultar y comparar las zonas analizadas. |

---

## 4. Qué NO queremos en este proyecto

El proyecto no busca:

- Desarrollar una plataforma para comprar o vender propiedades.
- Sustituir el análisis realizado por especialistas inmobiliarios.
- Predecir el precio exacto de cada inmueble individual.
- Realizar recomendaciones financieras personalizadas.
- Garantizar que una propiedad obtendrá determinada plusvalía.
- Analizar inicialmente zonas fuera de la Ciudad de México.

En esta primera versión, el análisis estará limitado a la Ciudad de México y a las zonas para las cuales exista información pública y suficientemente confiable.

---

## 5. Datos que tenemos y datos que faltan

Actualmente no contamos con una base de datos propia consolidada, por lo que el proyecto dependerá principalmente de fuentes de datos públicas y conjuntos de datos abiertos relacionados con el mercado inmobiliario.

### Fuentes de datos consideradas

#### INEGI

Se considera utilizar información sociodemográfica y de vivienda a nivel AGEB, por ejemplo:

- Población.
- Nivel educativo.
- Características de las viviendas.
- Acceso a servicios.
- Densidad poblacional.
- Características socioeconómicas.

#### Portal de Datos Abiertos de la Ciudad de México

Se considera utilizar información relacionada con:

- Permisos de construcción.
- Nuevos desarrollos inmobiliarios.
- Infraestructura urbana.
- Movilidad.
- Transporte público.
- Establecimientos.
- Servicios.
- Equipamiento urbano.

#### Información geoespacial

Se requerirá información geográfica para relacionar los diferentes conjuntos de datos.

Entre los elementos considerados se encuentran:

- Alcaldías.
- Colonias.
- AGEB.
- Códigos postales.
- Coordenadas geográficas.

#### Información inmobiliaria

Se buscará información relacionada con:

- Precios de venta.
- Precio por metro cuadrado.
- Evolución histórica de precios.
- Tipo de vivienda.
- Ubicación de propiedades.

---

### Datos que todavía faltan

Todavía es necesario determinar:

- La disponibilidad de datos históricos de precios inmobiliarios.
- La cobertura temporal de los datos.
- La granularidad geográfica disponible.
- La confiabilidad de las diferentes fuentes.
- La frecuencia de actualización.
- La compatibilidad entre colonias, códigos postales y AGEB.
- La cantidad de valores faltantes o inconsistencias.

---

## 6. Restricciones

- **Presupuesto máximo:** \$0 MXN para adquisición de datos y licencias (solo datos abiertos y software libre).
- **Plazo:** 6 semanas, del 15/10/2026 al 27/11/2026.
- **Costo de operación mensual máximo:** \$0 MXN; solo servicios gratuitos o académicos (por ejemplo, AWS Academy o capa gratuita de AWS).
- **Cobertura geográfica:** Ciudad de México.
- **Horizonte de análisis:** 5 años.
- **Fuentes:** Se priorizarán datos abiertos y públicos.
- **Seguridad y privacidad:** No deberán almacenarse datos personales sensibles.
- **Calidad de datos:** Se deberán identificar y documentar valores faltantes, duplicados e inconsistencias.
- **Usuario final:** Analistas e inversionistas con conocimientos básicos de interpretación de datos.
- **Limitación analítica:** Las estimaciones deberán presentarse como apoyo para la toma de decisiones y no como garantía del comportamiento futuro del mercado inmobiliario.

---

## 7. Qué esperamos recibir

Esperamos recibir una solución que permita concentrar y analizar información proveniente de diferentes fuentes para conocer las características y evolución de distintas zonas de la Ciudad de México.

Los entregables esperados son:

1. Una base de información consolidada y organizada por zona geográfica.
2. Un proceso de integración y limpieza de datos.
3. Un análisis de los factores relacionados con cambios en el valor inmobiliario.
4. Un índice de potencial de plusvalía.
5. Una estimación del comportamiento del valor inmobiliario durante los próximos cinco años.
6. Un mapa o visualización para identificar y comparar zonas.
7. Un reporte final que explique:
   - Resultados.
   - Limitaciones.
   - Fuentes de datos.
   - Criterios utilizados.
   - Supuestos del análisis.

El resultado deberá permitir que un usuario pueda identificar zonas que ameriten un análisis más profundo antes de realizar una inversión.

---

## 8. Cómo evaluaremos las propuestas

| Criterio | Peso |
|---|---:|
| Capacidad para responder a las necesidades planteadas | 30% |
| Calidad y confiabilidad de los datos propuestos | 25% |
| Metodología de análisis y validación | 20% |
| Claridad de los resultados y visualizaciones | 15% |
| Viabilidad del plan y tiempos de implementación | 10% |
| **Total** | **100%** |

---

## 9. Qué debe incluir su propuesta

La propuesta deberá incluir:

- Objetivo general.
- Alcance del proyecto.
- Elementos fuera de alcance.
- Fuentes de datos propuestas.
- Estrategia de adquisición de datos.
- Proceso de limpieza y transformación.
- Estrategia para integrar información de diferentes fuentes.
- Metodología para relacionar datos geográficos.
- Indicadores considerados para evaluar las zonas.
- Metodología para calcular el índice de potencial de plusvalía.
- Estrategia para generar las estimaciones.
- Método de validación de resultados.
- Calendario de actividades.
- Roles del equipo.
- Riesgos.
- Supuestos.
- Limitaciones.
- Entregables finales.
- Costos estimados, en caso de existir.

La propuesta deberá especificar claramente qué elementos se encuentran dentro y fuera del alcance del proyecto.

---

## 10. Calendario del proceso

- **Fecha límite para preguntas:** 09/10/2026
- **Fecha límite para entregar propuestas:** 12/10/2026
- **Fecha de decisión:** 14/10/2026
- **Inicio estimado del proyecto:** 15/10/2026
- **Entrega final esperada:** 27/11/2026

---

## Pregunta principal del proyecto

> **¿En qué zonas de la Ciudad de México sería potencialmente rentable adquirir una propiedad actualmente considerando su posible incremento de valor durante los próximos cinco años?**

---

## Alcance geográfico inicial

El proyecto estará enfocado inicialmente en la:

**Ciudad de México, México.**

Dependiendo de la disponibilidad y calidad de los datos, el análisis podrá realizarse a nivel de:

- Alcaldía.
- Colonia.
- AGEB.
- Código postal.

Se seleccionará el nivel geográfico que permita integrar de manera más consistente las diferentes fuentes de información.

---

## Consideraciones importantes

El índice de plusvalía y las predicciones generadas por el proyecto serán aproximaciones basadas en información histórica y variables disponibles.

Los resultados no representan una garantía de rendimiento futuro ni deberán considerarse asesoría financiera o inmobiliaria.

El objetivo principal del proyecto es utilizar técnicas de **Ingeniería de Datos, análisis de información y modelos predictivos** para apoyar la toma de decisiones basada en datos.
