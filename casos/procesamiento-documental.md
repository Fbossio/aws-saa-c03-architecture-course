# Procesamiento documental asíncrono

## Propósito didáctico

Practicar arquitectura backend empresarial cercana a APIs, eventos, colas, workflows, idempotencia, auditoría y costos.

## Contexto empresarial

Una plataforma recibe documentos, valida datos, procesa resultados y expone estado a otros sistemas.

## Usuarios

Sistemas internos, operadores y clientes que consultan el estado del procesamiento.

## Requisitos funcionales

Recibir documentos, almacenarlos, procesarlos de forma diferida, notificar cambios y consultar estado.

## Requisitos no funcionales

Idempotencia, reintentos, DLQ, trazabilidad, seguridad, auditoría y costo controlado.

## Restricciones

No se usarán SDK, CLI, consola ni despliegues reales.

## Estado inicial

Caso base evolucionado conceptualmente en el Módulo 01, todavía sin arquitectura definitiva.

## Preguntas abiertas

- Qué eventos deben ser confiables.
- Qué operaciones requieren orden.
- Qué datos deben auditarse.

## Decisiones futuras

Evaluar API Gateway, Lambda, S3, SQS, SNS, EventBridge, Step Functions, DynamoDB y RDS cuando corresponda.

Estos servicios no han sido seleccionados como decisión final; se mantienen pendientes para módulos posteriores.

## Módulos relacionados

5, 6, 9, 12, 14, 16, 18, 22, 25 y 26.

## Historial de evolución

- 2026-07-28 — Módulo 01: recepción y procesamiento se separan conceptualmente; el trabajo aceptado debe persistirse antes de confirmarse; se requiere estado observable del procesamiento; backlog y antigüedad son señales operativas relevantes; todavía no se seleccionan API Gateway, S3, SQS, Lambda, DynamoDB, RDS, SNS, EventBridge ni Step Functions; las decisiones concretas quedan pendientes de módulos posteriores.
- 2026-08-08 — Módulo 02: recepción y procesamiento pertenecen a caminos temporales distintos; un trabajo no debe considerarse aceptado hasta que exista evidencia durable; los reintentos requieren idempotencia; debe existir un identificador estable para reconocer la misma operación lógica; fallos transitorios y permanentes deben tratarse de forma diferente; el estado del procesamiento necesita una fuente autoritativa; backlog y antigüedad del trabajo son señales operativas relevantes; efectos secundarios, como notificaciones, no deben necesariamente invalidar el proceso principal; el escalado debe responder al cuello de botella real; una CPU baja no demuestra por sí sola que el sistema esté sano; recepción durable, procesamiento, estado y efectos secundarios deben evaluarse como responsabilidades distintas; todavía no se seleccionan Amazon API Gateway, Amazon S3, Amazon SQS, AWS Lambda, Amazon DynamoDB, Amazon RDS, Amazon SNS, Amazon EventBridge ni AWS Step Functions; las decisiones concretas quedan pendientes de módulos posteriores.
- 2026-11-22 — Módulo 03: la misma arquitectura se evalúa desde seguridad, resiliencia, rendimiento y costo; que un trabajo aceptado no pueda perderse convierte la durabilidad en restricción obligatoria; el procesamiento diferido permite desacoplamiento temporal; backlog no equivale automáticamente a fallo si respeta el SLA; elasticidad puede beneficiar rendimiento y costo; los permisos de workers deben seguir mínimo privilegio; efectos secundarios pueden aislarse del proceso principal; Multi-Region activo-activo no está justificado sin un requisito que lo exija; primero se satisfacen restricciones y después se optimiza; siguen pendientes las decisiones sobre servicios concretos para módulos posteriores.
