# Glosario de señales de decisión

Este glosario no es alfabético. Agrupa señales que suelen aparecer en requisitos de arquitectura y preguntas estilo examen. Cada entrada evita reglas automáticas.

## Menor esfuerzo operativo

- Qué suele indicar: preferencia por servicios administrados.
- Opciones que deben considerarse: serverless, servicios administrados, automatización nativa.
- Posibles distractores: administrar EC2 sin necesidad, soluciones autogestionadas.
- Preguntas previas: quién opera, qué se puede delegar, qué control se pierde.
- Advertencia: menor esfuerzo operativo no siempre significa menor costo.

## Escalado impredecible

- Qué suele indicar: elasticidad automática y desacoplamiento.
- Opciones que deben considerarse: Auto Scaling, Lambda, colas, servicios administrados.
- Posibles distractores: capacidad fija sobredimensionada.
- Preguntas previas: patrón de tráfico, latencia tolerable, estado de sesión.
- Advertencia: escalar no corrige una dependencia stateful mal ubicada.

## Carga tolerante a interrupciones

- Qué suele indicar: posibilidad de usar capacidad interrumpible.
- Opciones que deben considerarse: Spot Instances, colas, procesamiento batch.
- Posibles distractores: Spot para procesos críticos sin tolerancia.
- Preguntas previas: se puede reintentar, hay checkpoints, hay SLA estricto.
- Advertencia: tolerante a interrupciones no significa sin control de fallos.

## Baja latencia global

- Qué suele indicar: acercar contenido o entrada de tráfico al usuario.
- Opciones que deben considerarse: CloudFront, Global Accelerator, Route 53, Multi-Region.
- Posibles distractores: una sola región sin edge o replicación.
- Preguntas previas: contenido estático o dinámico, TCP o HTTP, consistencia requerida.
- Advertencia: latencia global no implica automáticamente Multi-Region activo-activo.

## Desacoplar productor y consumidor

- Qué suele indicar: cola o evento entre componentes.
- Opciones que deben considerarse: SQS, EventBridge, SNS.
- Posibles distractores: llamadas síncronas directas.
- Preguntas previas: orden, fan-out, retención, reintentos.
- Advertencia: desacoplar no elimina la necesidad de idempotencia.

## Varios consumidores independientes

- Qué suele indicar: fan-out o pub/sub.
- Opciones que deben considerarse: SNS, EventBridge, múltiples colas SQS.
- Posibles distractores: una sola cola compartida si todos necesitan recibir todo.
- Preguntas previas: cada consumidor necesita copia propia, filtros, orden.
- Advertencia: varios consumidores no siempre requieren streaming.

## Procesamiento ordenado

- Qué suele indicar: semántica FIFO por grupo o partición.
- Opciones que deben considerarse: SQS FIFO, diseño de claves, streaming con particiones.
- Posibles distractores: cola estándar cuando el orden es requisito estricto.
- Preguntas previas: orden global o por entidad, throughput, duplicados.
- Advertencia: orden estricto suele tener trade-off de rendimiento.

## Alta disponibilidad relacional

- Qué suele indicar: base relacional con redundancia administrada.
- Opciones que deben considerarse: Amazon RDS Multi-AZ, Amazon Aurora.
- Posibles distractores: backups como sustituto de alta disponibilidad.
- Preguntas previas: failover, lecturas, región, RPO y RTO.
- Advertencia: HA y DR no son lo mismo.

## Escalar lecturas

- Qué suele indicar: réplicas o caché.
- Opciones que deben considerarse: read replicas, ElastiCache, CloudFront según acceso.
- Posibles distractores: escalar escritura cuando el cuello es lectura.
- Preguntas previas: frescura requerida, patrón de consultas, tolerancia a stale data.
- Advertencia: caché no resuelve todas las consultas ni elimina invalidación.

## Consistencia fuerte

- Qué suele indicar: lecturas que deben reflejar escrituras recientes.
- Opciones que deben considerarse: diseño relacional, lectura consistente en servicios que la soporten.
- Posibles distractores: replicación eventual cuando el requisito no la tolera.
- Preguntas previas: qué entidad requiere consistencia y con qué latencia.
- Advertencia: consistencia fuerte puede reducir disponibilidad o rendimiento.

## Datos de acceso infrecuente

- Qué suele indicar: clases de almacenamiento más económicas con trade-offs de acceso.
- Opciones que deben considerarse: clases de S3 para acceso infrecuente o archivo.
- Posibles distractores: almacenamiento caliente por costumbre.
- Preguntas previas: frecuencia, latencia de recuperación, tamaño, duración.
- Advertencia: menor costo de almacenamiento puede aumentar costo de recuperación.

## Recuperación en horas

- Qué suele indicar: DR menos inmediato que activo-activo.
- Opciones que deben considerarse: backup and restore, pilot light.
- Posibles distractores: Multi-Region activo-activo sin necesidad.
- Preguntas previas: RTO, RPO, criticidad, presupuesto.
- Advertencia: un backup sin prueba de restauración es una suposición.

## Acceso privado a servicios

- Qué suele indicar: evitar tráfico público para consumir servicios.
- Opciones que deben considerarse: VPC endpoints, PrivateLink cuando aplique.
- Posibles distractores: NAT Gateway si el requisito es privado hacia servicios soportados.
- Preguntas previas: servicio destino, dirección de tráfico, DNS, región.
- Advertencia: privado no siempre significa conectividad híbrida.

## Evitar exposición a internet

- Qué suele indicar: subredes privadas, endpoints y controles de borde.
- Opciones que deben considerarse: subred privada, security groups, NACLs, VPC endpoints.
- Posibles distractores: IP pública por conveniencia.
- Preguntas previas: quién inicia conexión, qué debe ser público, cómo se administra.
- Advertencia: una subred privada mal enrutada puede exponer dependencias.

## Conectividad híbrida estable

- Qué suele indicar: enlace dedicado o VPN según necesidad.
- Opciones que deben considerarse: Direct Connect, Site-to-Site VPN, Transit Gateway.
- Posibles distractores: internet público para tráfico corporativo sensible.
- Preguntas previas: ancho de banda, latencia, cifrado, tiempo de provisión.
- Advertencia: estable no siempre significa dedicado si el presupuesto manda.

## RPO cercano a cero

- Qué suele indicar: replicación continua o arquitectura activa.
- Opciones que deben considerarse: replicación, Multi-AZ, Multi-Region según alcance.
- Posibles distractores: backups periódicos.
- Preguntas previas: pérdida de datos tolerable, región, escritura.
- Advertencia: RPO bajo suele costar más y complica consistencia.

## RTO de minutos

- Qué suele indicar: recuperación automatizada o entorno ya preparado.
- Opciones que deben considerarse: warm standby, Multi-AZ, automatización de failover.
- Posibles distractores: restaurar manualmente desde backup.
- Preguntas previas: cuánto tarda detectar, conmutar y validar.
- Advertencia: RTO no mide pérdida de datos.

## Menor costo posible

- Qué suele indicar: optimizar capacidad, almacenamiento y transferencia.
- Opciones que deben considerarse: serverless, reservas, clases de almacenamiento, evitar transferencia innecesaria.
- Posibles distractores: máxima disponibilidad sin requisito.
- Preguntas previas: requisito mínimo aceptable, patrón de uso, compromiso temporal.
- Advertencia: menor costo posible no debe violar requisitos críticos.

## Sin cambios en la aplicación heredada

- Qué suele indicar: migración compatible o envoltorios de infraestructura.
- Opciones que deben considerarse: rehost, Storage Gateway, conectividad híbrida.
- Posibles distractores: refactorización completa.
- Preguntas previas: qué cambios están prohibidos, ventana de migración, dependencias.
- Advertencia: no cambiar aplicación puede trasladar complejidad a infraestructura.

## Tráfico HTTP por rutas

- Qué suele indicar: balanceo de capa 7.
- Opciones que deben considerarse: Application Load Balancer, API Gateway según caso.
- Posibles distractores: Network Load Balancer para reglas HTTP.
- Preguntas previas: path-based routing, host-based routing, autenticación, serverless.
- Advertencia: HTTP no siempre implica API pública.

## Tráfico TCP de alto rendimiento

- Qué suele indicar: balanceo de capa 4.
- Opciones que deben considerarse: Network Load Balancer.
- Posibles distractores: ALB si se requiere TCP puro o muy baja latencia.
- Preguntas previas: protocolo, latencia, IP estática, TLS, targets.
- Advertencia: alto rendimiento no elimina controles de seguridad.
