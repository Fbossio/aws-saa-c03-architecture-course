# Plataforma global de contenido

## Propósito didáctico

Practicar decisiones de latencia global, CDN, enrutamiento, replicación, consistencia, recuperación y costos de transferencia.

## Contexto empresarial

Una plataforma distribuye contenido a usuarios en múltiples regiones del mundo.

## Usuarios

Consumidores globales, editores de contenido y equipo de operaciones.

## Requisitos funcionales

Servir contenido, enrutar tráfico, publicar actualizaciones y mantener continuidad.

## Requisitos no funcionales

Baja latencia, disponibilidad, consistencia adecuada, recuperación y costos sostenibles.

## Restricciones

El análisis será documental; no se publicará contenido ni infraestructura real.

## Estado inicial

Caso base sin arquitectura definitiva.

## Preguntas abiertas

- Qué contenido es estático o dinámico.
- Qué consistencia requiere cada dato.
- Qué latencia es aceptable por región.

## Decisiones futuras

Evaluar CloudFront, Global Accelerator, Route 53, replicación, Multi-Region y costos de transferencia.

## Módulos relacionados

4, 14, 18, 19, 20, 21, 24 y 26.

## Historial de evolución

### 2026-11-24 — Módulo 04: Infraestructura global y alcance de los servicios

Evolución conceptual del Caso C, con arquitectura definitiva pendiente.

1. Filtrar la ubicación del backend por las restricciones obligatorias de residencia de datos y por la disponibilidad de los servicios requeridos.
2. Comparar latencia y costos entre las regiones viables.
3. Evaluar Amazon CloudFront para distribuir contenido reutilizable desde un origen existente y evitar duplicar toda la aplicación por motivos de latencia.
4. Identificar qué componentes críticos comparten un mismo dominio de fallo.
5. Considerar Multi-AZ para mitigar fallos zonales cuando los componentes, los datos y los mecanismos de failover estén preparados para mantener el servicio.
6. La justificación de Multi-Region activo-activo sigue pendiente de un requisito de continuidad o latencia que compense su complejidad.
7. Amazon CloudFront puede aliviar la carga del origen mediante caché. La recuperación completa del backend exige una estrategia propia.
8. Profundizar en AWS Global Accelerator, replicación, consistencia, recuperación y costos de transferencia en los módulos posteriores.

#### Decisiones pendientes

- Región definitiva y arquitectura definitiva del backend.
- Servicio de almacenamiento definitivo.
- Estrategias de replicación y Multi-Region.
- Objetivos RPO y RTO.
- Políticas de consistencia.
- Costos reales de transferencia.
- Estrategia completa de failover.

Las alternativas se conservan para el análisis acumulativo del caso. La selección de servicios para producción queda pendiente.
