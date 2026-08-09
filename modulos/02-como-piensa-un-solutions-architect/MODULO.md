# Módulo 02 — Cómo piensa un Solutions Architect

## Metadatos

- Estado del documento: Completado
- Estado académico: Completado
- Versión: 1.0
- Duración estimada: 45 a 90 minutos
- Fase: Fase 0 — Orientación y contexto
- Dominio SAA-C03: Transversal a los cuatro dominios
- Tareas oficiales cubiertas: Ninguna tarea se considera formalmente cubierta; el módulo es metodológico y transversal.
- Módulos previos: 01 — Mapa de una arquitectura AWS
- Archivos relacionados: `docs/PROGRESO.md`, `docs/CRITERIOS_EVALUACION.md`, `docs/PLANTILLA_MODULO.md`, `docs/MAPA_EXAMEN.md`, `docs/MATRIZ_COBERTURA.md`, `casos/procesamiento-documental.md`, `registros/CONCEPTOS_DEBILES.md`, `registros/ERRORES.md`
- Caso: procesamiento documental asíncrono
- Fecha de última revisión: 2026-08-08
- Resultado de evaluación formal: 8/8 — 100 %
- Resultado global con mini retos: 16/16 — 100 %

## 1. Por qué importa

El examen SAA-C03 evalúa la capacidad de elegir la mejor arquitectura bajo requisitos, restricciones y trade-offs. Una solución puede ser técnicamente válida y aun así no ser óptima si ignora el requisito dominante, viola una restricción dura, aumenta complejidad sin necesidad o resuelve solo el síntoma.

Este módulo entrenó el método de razonamiento previo a elegir servicios: leer hechos, separar supuestos, identificar restricciones, comparar alternativas y justificar el ajuste. El objetivo fue pensar como Solutions Architect antes de pensar como catálogo de productos AWS.

## 2. Vista desde la arquitectura completa

La arquitectura se observó como un sistema con caminos temporales, responsabilidades y fallos parciales:

- recepción: punto donde una solicitud entra y debe validarse lo mínimo necesario;
- aceptación durable: evidencia persistente de que el trabajo existe antes de confirmar éxito;
- procesamiento: ejecución diferida que puede fallar, reintentarse o retrasarse;
- estado: fuente autoritativa para consultar avance, resultado y errores;
- efectos secundarios: notificaciones u operaciones derivadas que no siempre deben invalidar el proceso principal;
- observabilidad: señales sobre backlog, antigüedad, errores, latencia y resultado empresarial;
- límites: capacidad, elasticidad, costos, dependencias y blast radius.

El análisis mantuvo separadas las capacidades arquitectónicas de los productos concretos. API Gateway, S3, SQS, Lambda, DynamoDB, RDS, SNS, EventBridge y Step Functions permanecen pendientes para módulos especializados.

## 3. Objetivos evaluables

Al cerrar el módulo, el participante pudo:

- distinguir hechos, requisitos, restricciones y supuestos;
- identificar el requisito dominante de una decisión;
- separar restricciones duras de preferencias blandas;
- comparar requisitos mínimos frente a capacidades máximas;
- distinguir solución válida de solución óptima;
- detectar sobrearquitectura y distractores absolutos;
- razonar sobre riesgo por probabilidad e impacto;
- reconocer single point of failure, failure domain y blast radius;
- evaluar caminos síncronos y asíncronos;
- justificar retries, idempotencia, backpressure y estado autoritativo;
- comparar HA, DR, backup y replicación sin tratarlos como equivalentes.

## 4. Requisitos previos

Se requiere el Módulo 01 como base: lectura top-down, requisitos funcionales y no funcionales, flujos síncronos/asíncronos, stateless/stateful, puntos únicos de falla y controles transversales.

## 5. Resultado demostrable

El participante puede explicar y aplicar el método R²A²:

1. Requisitos.
2. Restricciones.
3. Alternativas.
4. Ajuste.

El método busca "la solución que satisface las restricciones obligatorias y optimiza el requisito dominante con trade-offs aceptables". Esta frase no se usa como regla absoluta: depende del contexto, la criticidad, el costo, la reversibilidad de la decisión y la evidencia disponible.

## 6. Mapa del módulo

El recorrido del módulo fue:

1. separar hechos, requisitos, restricciones y supuestos;
2. identificar requisito dominante;
3. distinguir restricciones duras y preferencias blandas;
4. comparar alternativas técnicamente válidas;
5. evaluar trade-offs, riesgo y sobrearquitectura;
6. analizar failure domains, blast radius y SPOF;
7. razonar sobre caminos síncronos/asíncronos;
8. aplicar idempotencia, retries, backpressure y observabilidad;
9. descartar distractores del examen.

## 7. Mapa mental

El mapa mental conecta:

- hechos: información explícita del escenario;
- requisitos: resultado que el sistema debe lograr;
- restricciones: límites que no deben violarse;
- supuestos: inferencias que deben mantenerse visibles;
- alternativas: opciones posibles con costos, complejidad y riesgos;
- ajuste: decisión que satisface lo obligatorio y optimiza lo más importante;
- señales de examen: absolutos, síntomas, incompletitud y sobrearquitectura.

## 8. Conceptos esenciales

- Hechos: datos explícitos del enunciado o del caso. No requieren inferencia.
- Requisitos: resultados funcionales o cualidades necesarias para que la solución sea aceptable.
- Restricciones: condiciones obligatorias que limitan las opciones.
- Supuestos: inferencias usadas para razonar, pero no confirmadas como hechos.
- Requisito dominante: criterio que más pesa en una decisión concreta.
- Restricción dura: límite que invalida una opción si se incumple.
- Preferencia blanda: criterio deseable que puede ceder ante una restricción o un requisito más importante.
- Requisito mínimo: nivel suficiente para cumplir el objetivo.
- Capacidad máxima: posibilidad técnica que puede exceder lo necesario y aumentar costo o complejidad.
- Solución técnicamente válida: opción que puede funcionar.
- Solución óptima: opción que mejor se ajusta al contexto, restricciones y trade-offs.
- Sobrearquitectura: diseño más complejo, caro o amplio de lo que el problema justifica.
- Trade-off: mejora en un eje a cambio de costo, complejidad, latencia, consistencia, operación o riesgo en otro.
- Riesgo: combinación de probabilidad e impacto.
- Single Point of Failure: componente cuya falla interrumpe una función crítica sin alternativa efectiva.
- Failure domain: ámbito dentro del cual un fallo puede afectar componentes relacionados.
- Blast radius: alcance del daño causado por un fallo o mala decisión.
- Camino crítico: pasos mínimos que deben funcionar para cumplir el resultado esperado.
- Synchronous vs asynchronous: respuesta inmediata frente a aceptación y procesamiento diferido.
- Fallos en cascada: propagación de fallos entre componentes acoplados.
- Retries: reintentos controlados ante fallos transitorios.
- Idempotencia: capacidad de procesar la misma operación lógica más de una vez sin efectos duplicados incorrectos.
- Backpressure: control para no aceptar o acelerar más trabajo del que el sistema puede procesar de forma saludable.
- Observabilidad orientada al resultado empresarial: medición de avance, éxito, antigüedad, errores y valor producido, no solo métricas técnicas aisladas.
- Decisiones reversibles: elecciones que pueden cambiarse con bajo costo relativo.
- Decisiones difíciles de revertir: elecciones que fijan datos, contratos, acoplamientos o costos de migración.
- Escalado vertical: aumentar capacidad de una instancia o componente.
- Escalado horizontal: agregar más unidades de procesamiento.
- Estado local: información conservada dentro de un componente concreto.
- Estado externo: información persistida fuera del componente para compartir, recuperar o escalar.
- Fallo parcial: degradación de una parte del sistema sin caída total.
- Source of truth: fuente autoritativa para decidir el estado real de una entidad o proceso.
- Consistencia y frescura: certeza y actualidad de los datos observados.
- Degradación controlada: mantener funciones críticas aunque funciones secundarias fallen.
- Capacidad, elasticidad y límites: tamaño disponible, adaptación a demanda y restricciones que impiden crecer indefinidamente.
- Cuello de botella: punto que limita el throughput o la latencia del sistema completo.
- Costo total frente a precio unitario: evaluación del gasto completo, incluyendo operación, transferencia, almacenamiento, fallos y complejidad.
- Redundancia frente a resiliencia: duplicar componentes no garantiza recuperación efectiva si el diseño sigue teniendo dependencias críticas.
- Backup frente a replicación: copia recuperable frente a duplicación continua o casi continua.
- Alta disponibilidad frente a recuperación ante desastres: continuidad ante fallos locales frente a recuperación ante eventos de mayor alcance.
- Métricas técnicas frente a objetivos de negocio: CPU, latencia o errores solo importan si explican impacto sobre aceptación, procesamiento, clientes o cumplimiento.

## 9. Comparaciones decisivas

- Requisito frente a solución: "procesar de forma durable" es requisito; nombrar un servicio es una posible solución.
- Restricción dura frente a preferencia blanda: una restricción invalida opciones; una preferencia ayuda a ordenar alternativas.
- Mínimo suficiente frente a máximo disponible: elegir la capacidad más alta puede ser sobrearquitectura si el requisito no la exige.
- Válido frente a óptimo: una opción puede resolver parte del problema y aun así perder por costo, riesgo, complejidad o incumplimiento de una restricción.
- Síncrono frente a asíncrono: síncrono simplifica respuesta inmediata; asíncrono mejora desacoplamiento y tolerancia a picos cuando el resultado puede diferirse.
- Escalado vertical frente a horizontal: vertical puede ser simple pero limitado; horizontal puede mejorar elasticidad si el estado y el acoplamiento lo permiten.
- Estado local frente a externo: local simplifica una instancia; externo favorece recuperación, escalado y source of truth.
- Backup frente a replicación: backup ayuda a restaurar; replicación reduce pérdida o demora, pero agrega costo y complejidad.
- HA frente a DR: HA busca continuidad ante fallos esperados dentro del diseño; DR busca recuperación ante interrupciones mayores.
- Redundancia frente a resiliencia: redundancia es un mecanismo; resiliencia es el resultado probado del sistema.

## 10. Caso guiado

Caso usado: Caso B — Procesamiento documental asíncrono.

La evolución del caso fue conceptual:

- recepción y procesamiento pertenecen a caminos temporales distintos;
- un trabajo no debe considerarse aceptado hasta que exista evidencia durable;
- los reintentos requieren idempotencia;
- debe existir un identificador estable para reconocer la misma operación lógica;
- fallos transitorios y permanentes deben tratarse de forma diferente;
- el estado del procesamiento necesita una fuente autoritativa;
- backlog y antigüedad del trabajo son señales operativas relevantes;
- efectos secundarios, como notificaciones, no deben necesariamente invalidar el proceso principal;
- el escalado debe responder al cuello de botella real;
- una CPU baja no demuestra por sí sola que el sistema esté sano;
- recepción durable, procesamiento, estado y efectos secundarios deben evaluarse como responsabilidades distintas.

No se seleccionaron servicios definitivos.

## 11. Mini retos de decisión

Se completaron 8 de 8 mini retos.

Los mini retos evaluaron requisito dominante, restricciones duras, solución óptima frente a solución válida, SPOF, caminos asíncronos, retries, idempotencia, respuesta múltiple y detección de distractores sobrearquitecturados.

Resultado: 8/8 correctos.

## 12. Evaluación conceptual

Evaluación formal de 8 preguntas.

| Pregunta | Tipo / dificultad | Tema | Correcta | Respondida | Resultado |
|---:|---|---|---|---|---|
| 1 | C1 / D1 | Requisito frente a solución | C | C | Correcta |
| 2 | C3 / D2 | Carga tolerante a interrupciones y optimización de costo | B | B | Correcta |
| 3 | C4 / D2 | Punto único de falla en base de datos | B | B | Correcta |
| 4 | C3 / D3 | Aceptación durable y procesamiento asíncrono | C | C | Correcta |
| 5 | C5 / D3 | Identificación del cuello de botella | B | B | Correcta |
| 6 | C4 / D3 | Respuesta múltiple: idempotencia e identificador estable | A y B | A y B | Correcta |
| 7 | C2 / D3 | Respuesta múltiple: alta disponibilidad frente a DR | A y C | A y C | Correcta |
| 8 | C6 / D4 | Selección por RTO, RPO, costo y complejidad | C | C | Correcta |

- Resultado: 8/8.
- Puntuación: 100 %.
- Dificultad máxima alcanzada: D4.
- Estado: aprobado según el criterio vigente para módulo introductorio.
- Confusiones críticas: ninguna.
- Refuerzo adicional requerido: no.

El puntaje interno del curso no equivale al puntaje escalado oficial del examen AWS.

## 13. Evaluación arquitectónica

La evaluación arquitectónica quedó integrada en los mini retos y en la evaluación formal. Se evaluaron selección de diseño, descarte de distractores, riesgos, trade-offs, idempotencia, HA frente a DR, RTO/RPO y complejidad proporcional al requisito.

Resultado integrado: 100 %, sin confusiones críticas.

## 14. Feedback y refuerzo

Fortalezas demostradas:

- identificación del requisito dominante;
- restricciones duras;
- desacoplamiento conceptual;
- detección de SPOF;
- identificación de cuellos de botella;
- idempotencia;
- HA frente a DR;
- evitar sobrearquitectura;
- análisis de trade-offs.

El concepto débil previo sobre lectura de instrucciones en preguntas de respuesta múltiple mostró mejora: hubo seis oportunidades sin reincidencia durante el Módulo 02.

## 15. Errores frecuentes

Se revisaron como riesgos de razonamiento:

- elegir servicios antes de capacidades;
- tratar preferencias como restricciones;
- confundir solución técnicamente posible con solución óptima;
- sobredimensionar por defecto;
- resolver el síntoma y no el cuello de botella;
- asumir que CPU baja implica salud del sistema;
- confundir redundancia con resiliencia;
- confundir backup, replicación, HA y DR;
- omitir idempotencia cuando hay retries;
- ignorar fallos parciales y efectos secundarios.

No hubo errores nuevos registrados en el Módulo 02.

## 16. Checklist de razonamiento

R²A²:

1. Requisitos: identificar hechos, objetivo, requisito dominante y resultado esperado.
2. Restricciones: separar restricciones duras, preferencias blandas, límites y supuestos.
3. Alternativas: comparar opciones técnicamente válidas, riesgos, costos y trade-offs.
4. Ajuste: elegir la opción que satisface lo obligatorio y optimiza lo dominante con trade-offs aceptables.

Señales para preguntas de examen:

- detectar palabras absolutas;
- descartar opciones técnicamente correctas pero incompletas;
- desconfiar de opciones que solo resuelven el síntoma;
- evitar opciones sobrearquitecturadas si el requisito no justifica costo o complejidad;
- verificar cantidad de respuestas solicitadas.

## 17. Criterio de aprobación

- Umbral provisional introductorio: 75 %.
- Resultado formal: 100 %.
- Mini retos: 8/8.
- Sin confusiones críticas.
- Criterio satisfecho.

Este resultado interno no se interpreta como equivalencia con el puntaje escalado oficial de AWS.

## 18. Resultado del módulo

- Estado: Completado.
- Fecha de cierre: 2026-08-08.
- Aprobación explícita del participante registrada.
- Resultado formal: 8/8 — 100 %.
- Mini retos: 8/8 correctos.
- Dificultad máxima alcanzada: D4.
- Refuerzo adicional requerido: no.
- Conceptos dominados: requisito dominante, restricciones, trade-offs, SPOF, failure domain, blast radius, idempotencia, backpressure, cuello de botella, HA frente a DR y descarte de distractores.

## 19. Recursos oficiales

- Guía oficial vigente SAA-C03.
- Documentación oficial AWS.
- AWS Well-Architected Framework.
- Materiales aportados como apoyo temático sin redistribución.

## 20. Entregables

Archivos creados o modificados por esta actualización:

- `modulos/02-como-piensa-un-solutions-architect/MODULO.md`
- `docs/PROGRESO.md`
- `casos/procesamiento-documental.md`
- `registros/CONCEPTOS_DEBILES.md`

Archivos leídos y validados sin cambios:

- `AGENTS.md`
- `docs/CURSO_MASTER.md`
- `docs/DECISIONES.md`
- `docs/PLANTILLA_MODULO.md`
- `docs/CRITERIOS_EVALUACION.md`
- `docs/MAPA_EXAMEN.md`
- `docs/MATRIZ_COBERTURA.md`
- `docs/CASOS_ARQUITECTURA.md`
- `docs/GLOSARIO_DECISIONES.md`
- `docs/FUENTES.md`
- `registros/ERRORES.md`
- `modulos/01-mapa-de-una-arquitectura-aws/MODULO.md`

## 21. Retrospectiva

Funcionó el enfoque de razonar por capacidades antes que por productos. El método R²A² permitió ordenar requisitos, restricciones, alternativas y ajuste sin convertir heurísticas en reglas absolutas.

La mejora en preguntas de respuesta múltiple fue observable: no hubo reincidencia en seis oportunidades. El concepto se considera en mejora, no dominado todavía.

## 22. Instrucciones para actualizar Git

La actualización fue preparada mediante Codex.

No hacer commit ni push automáticamente. El participante revisará el diff y decidirá cuándo registrar los cambios.

Mensaje de commit recomendado:

```text
completado modulo 2
```

## 23. Resumen de continuidad

Módulo 02 completado. Puntuación formal registrada: 100 %. Resultado global con mini retos: 100 %. Siguiente módulo: 03 — Los cuatro ejes del examen.

No hay confusiones críticas. Mantener en observación la lectura de instrucciones en preguntas de respuesta múltiple hasta una evaluación futura.
