# ADR 005: Adopción de AWS CloudFormation para Infraestructura como Código (IaC)

* **Estatus:** Aceptado
* **Fecha:** 2026-11-05
* **Autores:** Equipo 4

## Contexto y Problema

El proyecto requiere aprovisionar y gestionar múltiples recursos en AWS (buckets de S3, funciones Lambda, roles de IAM, políticas de seguridad y reglas de EventBridge). 

La creación manual de estos servicios mediante la consola web de AWS introduce riesgos de configuración inconsistente, falta de trazabilidad, imposibilidad de replicar entornos rápidamente y violaciones a las buenas prácticas de ingeniería de datos en producción. 

Se necesita definir una herramienta de Infraestructura como Código (IaC) estandarizada para definir y desplegar toda la infraestructura del proyecto.

## Opciones Evaluadas

1. **AWS CloudFormation (Nativo de AWS)**
2. **Terraform (HashiCorp)**
3. **AWS SAM (Serverless Application Model)**
4. **Aprovisionamiento manual mediante AWS Management Console**

## Análisis Comparativo de Opciones

| Criterio | AWS CloudFormation | Terraform | AWS SAM | Consola de AWS (Manual) |
| :--- | :--- | :--- | :--- | :--- |
| **Integración con AWS** | Nativa y sin estado externo | Requiere gestión de `tfstate` | Nativa (Extensión de CFN) | Directa |
| **Curva de Aprendizaje** | Baja (Sintaxis YAML/JSON estándar) | Media (Lenguaje HCL) | Baja (Enfocado a Serverless) | Nula |
| **Costo de Gestión** | $0 USD (Servicio gratuito) | $0 USD (Requiere bucket/backend para estado) | $0 USD | $0 USD |
| **Reproducibilidad y Rollback** | Reversión automática en caso de fallo | Manual o dependiente del script | Reversión automática | Propensa a errores humanos |
| **Portabilidad Multicloud** | Solo AWS | Multicloud | Solo AWS | N/A |

## Decisión

Se decide adoptar **AWS CloudFormation** (usando plantillas YAML en `infra/template.yaml`) como el estándar único e indiscutible para definir, aprovisionar y desplegar la infraestructura del proyecto.

### Regla de Proyecto:
**"Si un recurso de AWS no está declarado en la plantilla de CloudFormation, no existe en el proyecto."** Queda estrictamente prohibida la creación manual de recursos desde la consola de AWS para entornos finales.

## Justificación

1. **Gestión de Estado Nativa:** CloudFormation gestiona el estado de la infraestructura directamente en la cuenta de AWS sin requerir la administración de archivos de estado externos (a diferencia de `terraform.tfstate`).
2. **Despliegues Declarativos y Seguros:** Permite realizar despliegues repetibles y automatizados. En caso de error durante una actualización de infraestructura, CloudFormation realiza un *rollback* automático al último estado estable conocido.
3. **Control de Presupuesto y Límites:** Permite instanciar roles con privilegios mínimos (Principio de Menor Privilegio) y restringir configuraciones desde la primera fase (Hito 1) manteniendo la facturación dentro del presupuesto acotado ($1 USD).

## Consecuencias y Compromisos

* **Positivas:** 
  * Repositorio 100% auditable y reproducible.
  * Facilidad para destruir y recrear todo el entorno en minutos sin dejar recursos huérfanos cobrando en segundo plano.
* **Negativas / Mitigaciones:**
  * La sintaxis YAML de CloudFormation puede volverse extensa a medida que se agregan eventos y notificaciones de S3 a Lambda.
  * **Mitigación:** Estructurar el archivo `infra/template.yaml` de forma modular y documentar los bloques de parámetros y salidas (*Outputs*).