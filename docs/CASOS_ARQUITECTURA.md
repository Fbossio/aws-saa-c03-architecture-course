# Casos de arquitectura

No existe un proyecto técnico transversal. Los casos son escenarios acumulativos de arquitectura para practicar lectura de requisitos, comparación de alternativas y evolución de decisiones.

No se diseña todavía la solución final de cada caso.

## Caso A — Comercio electrónico regional

- Contexto: tienda regional con tráfico variable, catálogo, pagos externos y operaciones administrativas.
- Usuarios: clientes finales, equipo de operaciones y administradores de catálogo.
- Restricciones: evitar prácticas con recursos reales; razonar con diagramas y decisiones.
- Requisitos funcionales: navegación, compra, persistencia de pedidos, contenido estático y procesamiento asíncrono.
- Requisitos no funcionales: alta disponibilidad, recuperación ante desastres, seguridad perimetral y costos razonables.
- Estado inicial: escenario base sin arquitectura definitiva.
- Decisiones que podrán incorporarse: Route 53, CloudFront, AWS WAF, ALB, Auto Scaling, EC2, ECS, Lambda, RDS, Aurora, ElastiCache, SQS, S3, alta disponibilidad y recuperación ante desastres.
- Módulos relacionados: 7, 8, 9, 10, 12, 14, 15, 17, 18, 19, 20, 22, 23, 24.
- Historial de evolución: sin decisiones incorporadas todavía.

## Caso B — Procesamiento documental asíncrono

- Contexto: flujo backend empresarial para recibir, validar, procesar y auditar documentos.
- Usuarios: sistemas internos, operadores y clientes que consultan estado.
- Restricciones: no usar SDK ni desplegar recursos; trabajar con escenarios y decisiones.
- Requisitos funcionales: recepción de documentos, procesamiento diferido, notificaciones, estado de proceso y auditoría.
- Requisitos no funcionales: idempotencia, reintentos, DLQ, seguridad, trazabilidad y control de costos.
- Estado inicial: escenario base sin arquitectura definitiva.
- Decisiones que podrán incorporarse: API Gateway, Lambda, S3, SQS, SNS, EventBridge, Step Functions, DynamoDB, RDS cuando corresponda, idempotencia, reintentos, DLQ, seguridad, auditoría y costos.
- Módulos relacionados: 5, 6, 9, 12, 14, 16, 18, 22, 25, 26.
- Historial de evolución: sin decisiones incorporadas todavía.

## Caso C — Plataforma global de contenido

- Contexto: distribución global de contenido con usuarios en múltiples regiones.
- Usuarios: consumidores globales, editores de contenido y equipos de operación.
- Restricciones: análisis conceptual sin publicar ni replicar recursos reales.
- Requisitos funcionales: servir contenido, enrutar tráfico, replicar datos y mantener continuidad.
- Requisitos no funcionales: baja latencia, consistencia adecuada, recuperación, control de transferencia y costos.
- Estado inicial: escenario base sin arquitectura definitiva.
- Decisiones que podrán incorporarse: CloudFront, Global Accelerator, Route 53, replicación, Multi-Region, latencia, consistencia, recuperación y costos de transferencia.
- Módulos relacionados: 4, 14, 18, 19, 20, 21, 24, 26.
- Historial de evolución: sin decisiones incorporadas todavía.

## Caso D — Migración de aplicación empresarial

- Contexto: aplicación heredada con datos, dependencias internas y conectividad corporativa.
- Usuarios: personal interno, sistemas empresariales y equipo de migración.
- Restricciones: no ejecutar migraciones reales ni usar herramientas operativas.
- Requisitos funcionales: mover datos, conectar redes, mantener operación y reducir riesgo.
- Requisitos no funcionales: continuidad, baja interrupción, seguridad, compatibilidad y modernización gradual.
- Estado inicial: escenario base sin arquitectura definitiva.
- Decisiones que podrán incorporarse: Site-to-Site VPN, Direct Connect, Storage Gateway, DataSync, DMS, Application Migration Service, estrategias de DR y modernización gradual.
- Módulos relacionados: 7, 19, 21, 23, 24, 26, 27.
- Historial de evolución: sin decisiones incorporadas todavía.
