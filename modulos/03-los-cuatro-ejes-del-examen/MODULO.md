# Módulo 03 — Los cuatro ejes del examen

## Metadatos

- Estado del documento: Completado
- Estado académico: Completado
- Versión: 1.0
- Duración estimada: 45 a 90 minutos
- Fase: Fase 0 — Orientación y contexto
- Dominio SAA-C03: Transversal a los cuatro dominios
- Tareas oficiales cubiertas: Ninguna tarea se considera formalmente cubierta; el módulo introduce de forma transversal los cuatro dominios del examen.
- Módulos previos: 01 — Mapa de una arquitectura AWS; 02 — Cómo piensa un Solutions Architect
- Archivos relacionados: `docs/PROGRESO.md`, `docs/CRITERIOS_EVALUACION.md`, `docs/PLANTILLA_MODULO.md`, `docs/MAPA_EXAMEN.md`, `docs/MATRIZ_COBERTURA.md`, `casos/procesamiento-documental.md`, `registros/CONCEPTOS_DEBILES.md`, `registros/ERRORES.md`
- Caso: procesamiento documental asíncrono
- Fecha de última revisión: 2026-11-22
- Resultado evaluación conceptual: 6/6 — 100 %
- Resultado evaluación arquitectónica: 4/4 — 100 %
- Resultado formal total: 10/10 — 100 %
- Estado: Completado

## 1. Por qué importa

El SAA-C03 evalúa arquitecturas desde cuatro dimensiones: seguridad, resiliencia, alto rendimiento y optimización de costos. El eje dominante cambia según la decisión; las ponderaciones del examen no constituyen una prioridad universal de diseño.

Una arquitectura no debe maximizar indiscriminadamente los cuatro ejes. Debe cumplir primero las restricciones obligatorias y después optimizar entre las alternativas válidas. Este módulo aplicó esa interpretación didáctica a decisiones conceptuales, antes de seleccionar servicios.

## 2. Vista desde la arquitectura completa

El Caso B se analizó desde el flujo completo:

```text
sistema cliente
→ recepción
→ aceptación/persistencia durable
→ procesamiento
→ estado
→ efectos secundarios/notificaciones
```

Sobre la misma arquitectura se aplicaron simultáneamente cuatro preguntas:

- Seguridad: quién accede, qué puede hacer y cómo se protegen los datos.
- Resiliencia: qué ocurre ante fallos y cómo se conserva el trabajo aceptado.
- Rendimiento: si satisface carga, latencia y throughput.
- Costo: si existe desperdicio o sobreaprovisionamiento para lograr esos requisitos.

Los ejes cruzan todas las responsabilidades del flujo. Una mejora puede beneficiar varios a la vez o introducir un trade-off que debe justificarse.

## 3. Objetivos evaluables

El participante demostró poder:

- reconocer los cuatro dominios;
- identificar el eje dominante de una decisión;
- separar requisito obligatorio de preferencia;
- descartar soluciones que violan restricciones;
- analizar trade-offs entre ejes;
- detectar sobrearquitectura;
- diferenciar costo mínimo de solución rentable;
- evitar elegir automáticamente la solución más potente;
- analizar una arquitectura antes de seleccionar servicios.

## 4. Requisitos previos

- Módulo 01 — Mapa de una arquitectura AWS.
- Módulo 02 — Cómo piensa un Solutions Architect.
- Requisito dominante.
- Restricciones duras y preferencias blandas.
- Solución válida frente a solución óptima.
- SPOF, blast radius y desacoplamiento conceptual.

## 5. Resultado demostrable

El participante puede aplicar esta secuencia reutilizable:

1. Leer requisitos.
2. Identificar restricciones obligatorias.
3. Detectar el eje dominante.
4. Eliminar soluciones inválidas.
5. Comparar alternativas válidas.
6. Evaluar trade-offs.
7. Elegir la mejor opción.

> No elegir la arquitectura máxima, sino la arquitectura que cumple correctamente los requisitos y optimiza el criterio restante.

## 6. Mapa del módulo

1. Visión transversal de los cuatro ejes.
2. Seguridad.
3. Resiliencia.
4. Rendimiento.
5. Optimización de costos.
6. Interacción entre ejes.
7. Caso guiado.
8. Evaluación conceptual.
9. Evaluación arquitectónica.

## 7. Mapa mental

```text
requisitos
→ restricciones
→ eje dominante
→ alternativas válidas
→ trade-offs
→ decisión
```

Seguridad, resiliencia, rendimiento y costo son lentes aplicadas a la misma arquitectura, no arquitecturas independientes. Se conectan con el método del Módulo 02: primero comprobar validez y después comparar el ajuste de cada alternativa.

## 8. Conceptos esenciales

### Seguridad

> ¿Quién puede hacer qué, sobre qué recursos y cómo se protegen los datos?

La identidad identifica al actor; la autenticación comprueba quién es y la autorización determina qué acciones puede realizar sobre qué recursos. El mínimo privilegio limita los permisos a los necesarios para cada responsabilidad y reduce el blast radius de permisos excesivos.

La exposición describe qué interfaces o recursos son alcanzables. La protección de datos incluye cifrado en tránsito, mientras circulan entre componentes, y cifrado en reposo, cuando están almacenados. Cifrar no sustituye autorizar correctamente el acceso.

En la arquitectura documental, estos controles protegen la recepción, la consulta de estado y los documentos confidenciales. Se eligen según actores, acciones, recursos y sensibilidad; se descartan permisos administrativos por comodidad y controles de infraestructura que no resuelven un requisito. El trade-off es mantener políticas y controles precisos frente a la facilidad operativa de permisos amplios.

Señales de examen: «solo sistemas autorizados», «documentos confidenciales» o «acceso únicamente a recursos necesarios». Confusiones habituales: autenticación frente a autorización, mínimo privilegio frente a comodidad y controles necesarios frente a infraestructura innecesaria. La conexión con módulos previos es limitar el blast radius desde las responsabilidades del flujo.

AWS Identity and Access Management (IAM), AWS Key Management Service (AWS KMS), Amazon VPC, AWS Secrets Manager y otros servicios se estudiarán posteriormente; este módulo no los desarrolla en profundidad ni los selecciona para el caso.

### Resiliencia

> ¿Qué ocurre cuando algo falla?

Un single point of failure (SPOF) interrumpe una función crítica si falla sin alternativa efectiva. La redundancia aporta componentes alternativos; el desacoplamiento reduce dependencias directas y temporales. La persistencia durable permite que el trabajo aceptado sobreviva al fallo de un procesador. Un fallo parcial puede afectar una función sin detener todo el sistema; su blast radius indica el alcance del daño.

La alta disponibilidad (HA) busca continuidad ante los fallos previstos por el diseño. La recuperación ante desastres (DR) prepara la recuperación ante interrupciones de mayor alcance. Un backup permite restaurar datos, pero por sí solo no mantiene el servicio disponible.

```text
RTO = tiempo tolerable de interrupción.
RPO = pérdida tolerable de datos.
```

Son objetivos diferentes: mejorar el tiempo de recuperación no demuestra que se reduzca la pérdida de datos. Tampoco duplicar procesadores demuestra que el trabajo esté persistido de forma durable.

Se eligen mecanismos según fallo que debe tolerarse, RTO y RPO. Se descartan backups como sustituto automático de HA o redundancia sin protección del estado. Más redundancia y recuperación más rápida pueden aumentar costo y coordinación; el nivel de resiliencia debe responder al requisito.

Señales de examen: «un trabajo aceptado no puede perderse», «fallo de un procesador», «interrupción tolerable» o «pérdida de datos tolerable». Las confusiones decisivas son HA frente a DR, RTO frente a RPO, redundancia frente a desacoplamiento y backup frente a alta disponibilidad. Se conecta con la aceptación durable, SPOF y fallos parciales de los módulos previos.

### Alto rendimiento

> ¿Puede el sistema hacer el trabajo requerido al volumen y dentro de los tiempos requeridos?

La latencia mide cuánto tarda una operación; el throughput mide cuánto trabajo se completa por unidad de tiempo. La capacidad expresa los recursos o volumen de trabajo que puede soportar un componente. El rendimiento describe su comportamiento bajo carga; la escalabilidad describe su capacidad para adaptarse al crecimiento.

El cuello de botella limita el sistema completo. El escalado vertical aumenta recursos de una unidad; el horizontal añade unidades. La elasticidad adapta la capacidad a la demanda, creciendo y reduciéndose. La caché, como patrón conceptual, reutiliza resultados para reducir trabajo repetido, con trade-offs de frescura e invalidación.

Se elige una mejora después de localizar el componente limitado y medir carga, latencia y throughput. Se descarta añadir capacidad en un componente que no es el cuello de botella. El escalado horizontal exige poder repartir el trabajo; el vertical tiene límites de tamaño. Una caché se considera ante accesos reutilizables y se descarta como respuesta automática a cualquier lentitud.

Señales de examen: «picos de carga», «documentos por hora», «tiempo máximo de procesamiento» o «dependencia saturada». Las confusiones habituales son rendimiento frente a escalabilidad y latencia frente a throughput. Se conecta con backlog, antigüedad del trabajo y observabilidad del resultado empresarial.

> Escalar el componente limitado, no el componente más familiar.

### Optimización de costos

> ¿Estamos pagando más de lo necesario para cumplir los requisitos?

La capacidad ociosa y el sobreaprovisionamiento son fuentes de desperdicio. El right-sizing ajusta recursos al trabajo real; la elasticidad adapta capacidad a variaciones. Deben evaluarse costo de infraestructura, costo operativo y costo de transferencia, además del precio unitario.

Los patrones de acceso condicionan cuánto cuesta almacenar, consultar o recuperar datos. Un compromiso de uso puede reducir precio a cambio de flexibilidad; mantener capacidad fija puede ser adecuado para carga estable, pero caro ante picos ocasionales. Un nivel de resiliencia mayor al requerido también puede añadir costo y complejidad.

Se eligen ajustes que mantienen seguridad, disponibilidad y rendimiento exigidos. Se descartan ahorros que eliminan capacidad necesaria o violan restricciones. El costo mínimo aislado no garantiza una solución rentable: el ahorro de infraestructura puede aumentar operación o incumplimientos. Optimizar exige comparar el costo total de alternativas válidas.

Señales de examen: «evitar capacidad ociosa», «carga variable», «menor esfuerzo operativo» o «sin reducir disponibilidad». Las confusiones habituales son precio unitario frente a costo operativo, costo mínimo frente a solución rentable y optimización frente a degradación. Se conecta con solución suficiente, sobrearquitectura y restricciones duras del Módulo 02.

> Optimizar costos significa eliminar desperdicio, no capacidad necesaria.

## 9. Comparaciones decisivas

| Comparación | Criterio de decisión |
|---|---|
| Requisito obligatorio frente a optimización | Lo obligatorio invalida opciones; la optimización ordena las que cumplen. |
| Autenticación frente a autorización | Comprobar identidad frente a permitir acciones sobre recursos. |
| Mínimo privilegio frente a comodidad | Permisos necesarios frente a amplitud que facilita operar pero aumenta exposición. |
| HA frente a DR | Continuidad ante fallos previstos frente a recuperación ante desastres. |
| RTO frente a RPO | Interrupción tolerable frente a pérdida tolerable de datos. |
| Redundancia frente a desacoplamiento | Alternativas de componentes frente a reducción de dependencias. |
| Backup frente a alta disponibilidad | Restaurar una copia no garantiza continuidad del servicio. |
| Rendimiento frente a escalabilidad | Comportamiento bajo carga frente a capacidad para adaptarse al crecimiento. |
| Latencia frente a throughput | Tiempo por operación frente a trabajo completado por unidad de tiempo. |
| Escalado vertical frente a horizontal | Más recursos por unidad frente a más unidades, según límites y reparto del trabajo. |
| Capacidad fija frente a elasticidad | Capacidad mantenida frente a adaptación a la demanda. |
| Costo mínimo frente a solución rentable | Menor gasto aislado frente a costo total adecuado para cumplir requisitos. |
| Arquitectura suficiente frente a sobrearquitectura | Capacidades justificadas frente a complejidad y costo sin requisito que los exija. |

> Primero descartar las opciones que incumplen requisitos obligatorios. Después optimizar entre las alternativas que sí cumplen.

## 10. Caso guiado

Caso B — Procesamiento documental asíncrono.

Contexto usado durante el módulo:

- documentos confidenciales;
- solo sistemas autorizados pueden enviarlos y consultar resultados;
- un trabajo aceptado no puede perderse aunque falle un procesador;
- carga normal aproximada de 500 documentos/hora;
- picos aproximados de 40 000 documentos/hora;
- procesamiento dentro de 20 minutos;
- una notificación puede retrasarse sin invalidar el procesamiento;
- evitar mantener capacidad sobredimensionada permanentemente;
- no existe todavía un requisito de continuidad frente a pérdida completa de una región.

Conclusiones conceptuales derivadas de esos requisitos:

- seguridad exige controlar identidades, permisos y protección de datos;
- resiliencia exige que el trabajo aceptado sobreviva al fallo de un procesador: la durabilidad es una restricción obligatoria;
- el procesamiento diferido permite desacoplamiento temporal;
- el backlog puede ser deliberado y saludable mientras respete el SLA de procesamiento;
- rendimiento debe analizar throughput, latencia y cuello de botella;
- la capacidad de procesamiento puede necesitar elasticidad;
- elasticidad puede beneficiar rendimiento y costo simultáneamente;
- permisos administrativos completos para workers contradicen mínimo privilegio;
- efectos secundarios como notificaciones deben poder fallar sin necesariamente invalidar el proceso principal;
- no existe todavía justificación para Multi-Region activo-activo;
- la arquitectura futura debe satisfacer primero restricciones y optimizar después.

No se seleccionó ningún servicio concreto como decisión definitiva. Amazon SQS, Amazon SNS, Amazon EventBridge, AWS Lambda, Amazon API Gateway, Amazon S3, Amazon DynamoDB, Amazon RDS, AWS Step Functions, Amazon EC2 Auto Scaling, Amazon ECS y AWS Fargate son contenido futuro para módulos especializados, al igual que cualquier otra selección de servicios.

## 11. Mini retos de decisión

Se completaron 12 mini retos, todos correctamente: 12/12 — 100 %.

Se comprobaron requisito dominante, restricciones obligatorias, mínimo privilegio, cifrado en tránsito, SPOF, RTO/RPO, cuello de botella, throughput, elasticidad, optimización de costos e interacción entre los cuatro ejes. Las preguntas de respuesta múltiple fueron interpretadas correctamente, incluida la cantidad de respuestas solicitada.

## 12. Evaluación conceptual

Registro posterior al intento: 6 preguntas — 6/6 — 100 %.

| Pregunta | Tipo / dificultad | Tema | Correcta | Respondida | Resultado |
|---:|---|---|---|---|---|
| 1 | C1 / D1 | Identificación del eje de resiliencia | B | B | Correcta |
| 2 | C2 / D2 | Rendimiento frente a escalabilidad | B | B | Correcta |
| 3 | C3 / D2 | RTO/RPO y optimización de costos | B y C | B y C | Correcta |
| 4 | C4 / D3 | SPOF y persistencia durable | B | B | Correcta |
| 5 | C5 / D3 | Elasticidad y right-sizing | B | B | Correcta |
| 6 | C6 / D4 | Desacoplamiento durable y elasticidad | A y C | A y C | Correcta |

- Resultado: 6/6.
- Puntuación: 100 %.
- Confusiones críticas: ninguna.
- Dificultad máxima: D4.

## 13. Evaluación arquitectónica

Registro posterior al intento: 4 preguntas — 4/4 — 100 %.

| Pregunta | Tipo / dificultad | Tema | Correcta | Respondida | Resultado |
|---:|---|---|---|---|---|
| 7 | C3 / D3 | Right-sizing sin reducir disponibilidad | B | B | Correcta |
| 8 | C4 / D3 | Acoplamiento temporal innecesario | A | A | Correcta |
| 9 | C5 / D4 | Mínimo privilegio y política de escalado | A y B | A y B | Correcta |
| 10 | C6 / D4 | Selección por RTO, RPO y costo | A y C | A y C | Correcta |

- Resultado: 4/4.
- Puntuación: 100 %.
- Confusiones críticas: ninguna.

Resultado formal total del módulo: 10/10 — 100 %. Los mini retos se registran por separado. El puntaje interno del curso no equivale al puntaje escalado oficial de AWS.

## 14. Feedback y refuerzo

Fortalezas demostradas:

- identificación del requisito dominante;
- restricciones obligatorias;
- seguridad y mínimo privilegio;
- HA frente a DR;
- RTO frente a RPO;
- detección de SPOF;
- desacoplamiento temporal;
- rendimiento frente a escalabilidad;
- latencia frente a throughput;
- identificación del cuello de botella;
- elasticidad;
- right-sizing;
- optimización de costos;
- detección de sobrearquitectura;
- análisis de trade-offs entre varios ejes.

No se registró ningún concepto débil nuevo ni se requiere refuerzo adicional. La lectura de instrucciones en preguntas de respuesta múltiple queda Dominado: a las seis oportunidades sin reincidencia del Módulo 02 se suma la interpretación correcta de todas las preguntas de respuesta múltiple del Módulo 03, sin errores en la cantidad seleccionada.

Las tablas conservan la clave y la respuesta de cada pregunta ya contestada. Este cierre sintetiza los criterios y resultados aportados; no reconstruye enunciados, distractores ni feedback por opción que no fueron proporcionados para el registro.

## 15. Errores frecuentes

Como riesgos generales de razonamiento, conviene evitar:

- usar las ponderaciones del examen como prioridad universal de diseño;
- elegir la opción más potente antes de comprobar restricciones;
- confundir autenticación con autorización o cifrado con permisos;
- equiparar HA, DR y backup, o intercambiar RTO y RPO;
- considerar todo backlog un fallo aunque respete el SLA;
- añadir capacidad donde no está el cuello de botella;
- reducir costo eliminando capacidad o disponibilidad necesarias;
- justificar Multi-Region activo-activo sin un requisito explícito.

No son errores cometidos por el participante: no hubo respuestas incorrectas en el Módulo 03. `registros/ERRORES.md` conserva sin cambios el error histórico del Módulo 01.

## 16. Checklist de razonamiento

1. ¿Qué exige el negocio?
2. ¿Qué requisito es obligatorio y cuál es deseable?
3. ¿Qué eje domina esta decisión?
4. ¿Qué opciones incumplen una restricción?
5. ¿Dónde está el cuello de botella o SPOF?
6. ¿La solución arregla el problema correcto?
7. ¿Estoy sobrearquitecturando?
8. ¿Qué trade-off introduce?
9. ¿Existe una alternativa válida con menos complejidad o costo?
10. ¿Hay algún requisito explícito que todavía no he utilizado?

```text
Requisitos
→ restricción dominante
→ eliminar inválidas
→ comparar trade-offs
→ elegir
```

## 17. Criterio de aprobación

- Umbral provisional introductorio: 75 %, según `docs/CRITERIOS_EVALUACION.md`.
- Resultado formal: 10/10 — 100 %.
- Evaluación conceptual: 6/6 — 100 %.
- Evaluación arquitectónica: 4/4 — 100 %.
- Mini retos: 12/12 — 100 %.
- Dificultad máxima alcanzada: D4.
- Confusiones críticas: ninguna.
- Criterio satisfecho.

El participante aprobó explícitamente el cierre como Completado. No se modifica el umbral global propuesto ni se equipara este resultado al puntaje escalado oficial de AWS.

## 18. Resultado del módulo

- Estado: Completado
- Fecha de cierre: 2026-11-22
- Aprobación explícita del participante: sí
- Resultado formal: 10/10 — 100 %
- Mini retos: 12/12 — 100 %
- Refuerzo adicional requerido: no

Conceptos dominados: cuatro ejes del examen, requisito dominante, restricciones obligatorias, análisis de trade-offs, mínimo privilegio, HA vs DR, RTO vs RPO, SPOF, desacoplamiento, rendimiento vs escalabilidad, latencia vs throughput, cuello de botella, elasticidad, right-sizing, optimización de costos y sobrearquitectura.

Conceptos débiles nuevos: Ninguno.

## 19. Recursos oficiales

- Guía oficial vigente SAA-C03: referencia de alcance del examen.
- Documentación oficial AWS: referencia de comportamiento de servicios para los módulos especializados.
- AWS Well-Architected Framework: referencia para criterios y trade-offs de arquitectura.
- Diapositivas aportadas al proyecto: únicamente apoyo temático, sin copia extensa ni redistribución de material comercial.

Se conserva la jerarquía de `docs/FUENTES.md`. La fecha de este cierre acredita la revisión del registro académico, no una nueva verificación externa de versiones de fuentes. Las explicaciones son síntesis didácticas; las conclusiones del caso son inferencias a partir de sus requisitos y las decisiones de cobertura son propias del curso.

## 20. Entregables

Archivos creados o modificados:

- `modulos/03-los-cuatro-ejes-del-examen/MODULO.md`
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
- `modulos/02-como-piensa-un-solutions-architect/MODULO.md`

La cobertura es introductoria y transversal. Ninguna tarea oficial 1.x, 2.x, 3.x o 4.x se considera formalmente cubierta, evaluada o revisada por este módulo; su cobertura profunda queda pendiente de los módulos correspondientes. La matriz permanece sin cambios.

## 21. Retrospectiva

Funcionó especialmente bien:

- razonar desde requisitos antes que servicios;
- cambiar de eje dominante según el escenario;
- eliminar alternativas inválidas antes de optimizar;
- usar el caso documental sin adelantar decisiones de servicios;
- comparar soluciones suficientes frente a soluciones máximas.

No hubo errores en evaluación. El concepto débil histórico de respuesta múltiple queda considerado Dominado por evidencia acumulada de los módulos 02 y 03; el historial del error original se conserva.

## 22. Instrucciones para actualizar Git

No hacer commit automáticamente.
No hacer push automáticamente.
El participante debe revisar `git diff` y `git status` antes de registrar los cambios.

El módulo nuevo debe revisarse también como archivo sin seguimiento, pues `git diff` por sí solo no muestra su contenido hasta que se incorpore a Git.

Mensaje de commit recomendado:

```text
completado modulo 3
```

## 23. Resumen de continuidad

- Módulo finalizado: 03 — Los cuatro ejes del examen
- Estado: Completado
- Puntuación formal: 100 % (10/10)
- Mini retos: 12/12
- Confusiones críticas: ninguna
- Conceptos débiles nuevos: ninguno
- Concepto previo de respuesta múltiple: Dominado
- Caso actualizado: procesamiento documental asíncrono
- Servicios concretos seleccionados: ninguno; decisiones diferidas a módulos especializados
- Siguiente módulo: 04 — Infraestructura global y alcance de los servicios
- Fase: Fase 0 — Orientación y contexto
- Hito 1: sigue Pendiente hasta completar el Módulo 04

Decisiones globales pendientes:

- DEC-013 — Umbral definitivo de aprobación
- DEC-014 — Duración definitiva de módulos
- DEC-016 — Calendario definitivo de repetición espaciada

La rama `main` seguirá siendo la fuente de verdad para el siguiente chat. El cierre queda preparado localmente para revisión del participante, sin commit ni push automáticos.
