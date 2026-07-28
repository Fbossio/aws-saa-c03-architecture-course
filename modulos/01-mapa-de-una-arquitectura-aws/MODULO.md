# Módulo 01 — Mapa de una arquitectura AWS

## Metadatos

- Estado del documento: Cerrado
- Estado académico: Completado
- Versión: 1.0
- Duración estimada: 45 a 90 minutos
- Fase: Fase 0 — Orientación y contexto
- Dominio SAA-C03: Introducción transversal a los dominios 1, 2, 3 y 4
- Tareas oficiales cubiertas: Ninguna tarea se considera formalmente cubierta; el módulo establece fundamentos transversales.
- Módulos previos: Ninguno
- Archivos relacionados: `docs/PROGRESO.md`, `docs/CRITERIOS_EVALUACION.md`, `docs/PLANTILLA_MODULO.md`, `docs/DECISIONES.md`, `casos/procesamiento-documental.md`, `registros/ERRORES.md`, `registros/CONCEPTOS_DEBILES.md`
- Fecha de última revisión: 2026-07-28
- Resultado de evaluación formal: 13/14 — 92,9 %
- Resultado global con mini retos: 21/22 — 95,5 %

## 1. Por qué importa

El examen SAA-C03 evalúa decisiones de arquitectura, no la memorización de un catálogo aislado de servicios. Una pregunta suele describir requisitos, restricciones, fallos, costos o cambios de carga; la respuesta correcta depende de interpretar el sistema antes de elegir nombres de servicios.

Este módulo proporciona un mapa inicial para ubicar posteriormente los servicios AWS dentro de funciones arquitectónicas: entrada, cómputo, datos, integración, controles transversales y operación. La intención didáctica es construir criterio antes de entrar al detalle de cada producto.

## 2. Vista desde la arquitectura completa

Una arquitectura se leyó como un flujo completo:

- Usuarios: personas, sistemas internos, operadores o clientes que originan o consultan operaciones.
- Entrada y distribución: puntos que reciben solicitudes, enrutan tráfico y protegen el acceso.
- Cómputo: componentes que ejecutan lógica de negocio, validaciones o procesamiento.
- Datos y almacenamiento: lugares donde se conserva estado, documentos, resultados, configuraciones o auditoría.
- Integración y procesamiento asíncrono: mecanismos para desacoplar productores y consumidores cuando el resultado no necesita ser inmediato.
- Dependencias externas: pagos, sistemas corporativos, servicios de terceros o procesos que afectan disponibilidad y recuperación.
- Controles transversales: identidad, seguridad de red, protección de datos, observabilidad, resiliencia, rendimiento y costos.

La lectura arquitectónica parte de las funciones y relaciones. Los servicios concretos se seleccionan después, cuando el requisito dominante y los trade-offs son claros.

## 3. Objetivos evaluables

Al cerrar el módulo, el participante pudo:

- distinguir requisitos funcionales, no funcionales y restricciones;
- identificar el requisito dominante de una decisión;
- reconocer flujos síncronos y asíncronos;
- distinguir componentes stateless y stateful;
- identificar puntos únicos de falla;
- evaluar observabilidad, resiliencia, rendimiento y costo como controles de diseño;
- justificar una decisión sin convertir un servicio en respuesta automática.

## 4. Requisitos previos

Se requieren fundamentos generales de cliente-servidor, API, persistencia y procesos síncronos/asíncronos. No hay módulos previos obligatorios.

## 5. Resultado demostrable

El participante puede interpretar una arquitectura general y explicar por qué existe cada función antes de seleccionar servicios. También puede separar problema, requisito, restricción, riesgo y decisión, lo que prepara la lectura de preguntas estilo examen.

## 6. Mapa del módulo

El recorrido del módulo fue:

1. requisitos;
2. flujo;
3. componentes;
4. dependencias;
5. riesgos;
6. controles transversales;
7. trade-offs;
8. decisión.

Este orden evita empezar por la herramienta y obliga a justificar cada elección desde la arquitectura.

## 7. Mapa mental

El mapa mental usado conecta:

- requisitos: qué necesita lograr el sistema y bajo qué condiciones;
- flujo: cómo entra, avanza, espera o termina una operación;
- componentes: qué función cumple cada parte de la solución;
- controles transversales: seguridad, resiliencia, rendimiento, observabilidad y costo;
- decisiones: elección justificada según requisito dominante y restricciones.

## 8. Conceptos esenciales

- Requisitos funcionales: describen lo que el sistema debe hacer, como recibir documentos, consultar estado o notificar cambios.
- Requisitos no funcionales: describen cómo debe comportarse el sistema, por ejemplo disponibilidad, latencia, durabilidad, seguridad o costo.
- Restricciones: límites explícitos de diseño, operación, presupuesto, tecnología o cumplimiento.
- Requisito dominante: criterio que más pesa en una decisión concreta; puede cambiar entre preguntas del mismo escenario.
- Flujo síncrono: el solicitante espera una respuesta directa dentro de la misma interacción.
- Flujo asíncrono: el trabajo se acepta y continúa después, normalmente con estado, cola, evento o mecanismo equivalente.
- Acoplamiento: grado de dependencia directa entre componentes; menor acoplamiento suele facilitar resiliencia y escalado, pero agrega coordinación.
- Stateless: componente que no depende de estado local duradero para atender solicitudes.
- Stateful: componente o capa que conserva estado necesario para continuidad, consistencia o auditoría.
- Single Point of Failure: elemento cuya caída interrumpe una función crítica sin alternativa efectiva.
- Identidad: control sobre quién puede actuar y con qué permisos.
- Seguridad de red: control sobre rutas, exposición, segmentación y tráfico permitido.
- Protección de datos: confidencialidad, integridad, durabilidad y manejo adecuado de datos en tránsito o reposo.
- Observabilidad: capacidad de entender salud, errores, latencia, backlog, antigüedad y resultado real del proceso.
- Resiliencia: capacidad de seguir operando o recuperarse ante fallos.
- Rendimiento: tiempo de respuesta, throughput o eficiencia bajo una carga determinada.
- Escalabilidad: capacidad de adaptarse a cambios de carga sin rediseño desproporcionado.
- Costos: impacto económico de capacidad, transferencia, almacenamiento, operación y complejidad.
- Camino crítico de una operación: secuencia mínima que debe funcionar para cumplir el resultado esperado.

## 9. Comparaciones decisivas

- Funcional frente a no funcional: "procesar un documento" define una función; "procesarlo de forma durable y observable" define condiciones de calidad.
- Síncrono frente a asíncrono: síncrono favorece respuesta inmediata; asíncrono favorece desacoplamiento, absorción de picos y reintentos cuando el resultado puede demorarse.
- Stateless frente a stateful: stateless simplifica escalado horizontal; stateful exige diseñar ubicación, persistencia, consistencia y recuperación del estado.
- Rendimiento frente a escalabilidad: rendimiento mide comportamiento bajo carga; escalabilidad mide la capacidad de crecer o reducirse frente a variación de carga.
- Redundancia parcial frente a resiliencia integral: duplicar una pieza no elimina todos los puntos únicos de falla si persisten dependencias críticas no redundantes.
- Resiliencia frente a complejidad y costo: mayor tolerancia a fallos puede requerir más componentes, coordinación, pruebas y gasto.

## 10. Caso guiado

Caso usado: Caso B — Procesamiento documental asíncrono.

Durante este módulo no se seleccionaron servicios definitivos. Las decisiones registradas fueron conceptuales:

- separar recepción y procesamiento;
- persistir el trabajo aceptado antes de confirmarlo;
- registrar el estado del procesamiento;
- observar backlog y antigüedad del trabajo pendiente;
- mantener pendientes las decisiones de servicios concretos.

Esta evolución prepara módulos posteriores sobre integración, almacenamiento, cómputo, observabilidad y resiliencia, sin convertir todavía API Gateway, S3, SQS, Lambda, DynamoDB, RDS, SNS, EventBridge ni Step Functions en decisiones aprobadas.

## 11. Mini retos de decisión

Se completaron 8 de 8 mini retos.

Los mini retos evaluaron identificación de requisito dominante, separación entre función y calidad, reconocimiento de flujos síncronos/asíncronos, ubicación del estado, detección de puntos únicos de falla, medición del resultado real y descarte de soluciones sobredimensionadas.

## 12. Evaluación conceptual

Evaluación de 8 preguntas.

- Resultado: 7/8.
- Puntuación: 87,5 %.
- Único error: pregunta de respuesta múltiple contestada con una sola opción cuando se solicitaban dos.

El error no se registra como desconocimiento técnico de observabilidad asíncrona, porque una de las dos señales correctas sí fue seleccionada. El seguimiento se concentra en verificar la cantidad de respuestas solicitada.

## 13. Evaluación arquitectónica

Evaluación de 6 preguntas.

- Resultado: 6/6.
- Puntuación: 100 %.

La evaluación confirmó razonamiento suficiente para leer requisitos, detectar riesgos, separar decisiones conceptuales de servicios concretos y justificar trade-offs sin seleccionar soluciones automáticas.

## 14. Feedback y refuerzo

No se detectaron debilidades conceptuales críticas.

Punto de refuerzo: antes de responder, verificar si la pregunta es de opción múltiple o respuesta múltiple y seleccionar exactamente la cantidad solicitada.

## 15. Errores frecuentes

- Elegir servicios antes de requisitos.
- Confundir redundancia parcial con alta disponibilidad.
- Confirmar una operación antes de persistir el trabajo aceptado.
- Asumir que asíncrono siempre es mejor.
- Confundir stateless con ausencia de datos.
- Medir solo la entrada de un flujo asíncrono.
- Sobrearquitecturar cargas no críticas.
- Ignorar dependencias de arranque o recuperación.
- Seleccionar una cantidad incorrecta de respuestas.

## 16. Checklist de razonamiento

- Identificar el tipo de pregunta.
- Verificar la cantidad de respuestas solicitadas.
- Encontrar el requisito dominante.
- Separar restricciones de preferencias.
- Confirmar si se necesita resultado inmediato.
- Comprobar durabilidad antes de confirmar aceptación.
- Ubicar dónde vive el estado.
- Buscar puntos únicos de falla.
- Definir métricas del resultado empresarial, no solo de entrada.
- Evaluar si resiliencia y costo son proporcionales a la criticidad.

## 17. Criterio de aprobación

- Umbral provisional introductorio: 75 %.
- Resultado formal: 92,9 %.
- Sin confusiones críticas.
- Criterio satisfecho.

Este resultado interno no se interpreta como equivalencia con el puntaje escalado oficial de AWS.

## 18. Resultado del módulo

- Estado: Completado.
- Fecha de cierre: 2026-07-28.
- Aprobación explícita del participante registrada.
- Conceptos dominados: lectura top-down de arquitectura, requisito dominante, flujo síncrono/asíncrono, stateless/stateful, puntos únicos de falla, observabilidad y trade-offs.
- Punto de atención: selección incompleta en preguntas de respuesta múltiple.

## 19. Recursos oficiales

- Guía oficial vigente SAA-C03.
- Documentación oficial AWS.
- AWS Well-Architected Framework.
- Materiales aportados como apoyo temático sin redistribución.

## 20. Entregables

Archivos modificados por esta actualización:

- `modulos/01-mapa-de-una-arquitectura-aws/MODULO.md`
- `docs/PROGRESO.md`
- `docs/DECISIONES.md`
- `docs/CRITERIOS_EVALUACION.md`
- `docs/PLANTILLA_MODULO.md`
- `casos/procesamiento-documental.md`
- `registros/ERRORES.md`
- `registros/CONCEPTOS_DEBILES.md`

## 21. Retrospectiva

Funcionó el enfoque top-down: permitió razonar desde requisitos y riesgos antes de nombrar servicios. También funcionaron los escenarios progresivos, porque el Caso B permitió tomar decisiones conceptuales sin adelantar módulos posteriores.

Debe evitarse que ejemplos de formato revelen la respuesta. Los ejemplos deben ser neutrales, aleatorios y explícitamente no relacionados con la solución.

## 22. Instrucciones para actualizar Git

La actualización fue preparada mediante Codex.

No hacer commit ni push automáticamente. El participante revisará el diff y decidirá cuándo registrar los cambios.

Mensaje de commit recomendado:

```text
docs: completar módulo 01 y registrar reglas de evaluación
```

## 23. Resumen de continuidad

Módulo 01 completado. Puntuación formal registrada: 92,9 %. Resultado global con mini retos: 95,5 %. Siguiente módulo: 02 — Cómo piensa un Solutions Architect.

No hay debilidad conceptual crítica. Vigilar selección incompleta en respuestas múltiples.
