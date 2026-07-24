# Decisiones

Estados permitidos: Propuesta, Aprobada, Reemplazada, Descartada.

## Formato

Cada decisión debe incluir identificador, fecha, estado, contexto, decisión, motivo, impacto y condiciones de revisión.

## DEC-001 — Nombre y orientación del curso

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Se requiere una fuente de verdad para un curso personal SAA-C03.
- Decisión: El curso se llama AWS Solutions Architect Associate SAA-C03 — Arquitectura y preparación para el examen.
- Motivo: El nombre refleja certificación, arquitectura y preparación práctica.
- Impacto: Ordena documentos, prompts y seguimiento.
- Condiciones de revisión: Cambio explícito de objetivo del curso.

## DEC-002 — GitHub como única fuente de verdad

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Las conversaciones pueden perder continuidad.
- Decisión: La rama `main` será la única fuente de verdad al publicarse.
- Motivo: Permite trazabilidad y evita dependencia de memoria contextual.
- Impacto: Todo avance consolidado debe quedar registrado en Git.
- Condiciones de revisión: Cambio de plataforma de versionado.

## DEC-003 — Exclusión de prácticas con recursos AWS

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El curso debe evitar costos, credenciales y operaciones reales.
- Decisión: No habrá creación de recursos reales en AWS.
- Motivo: El objetivo es razonamiento arquitectónico y preparación del examen.
- Impacto: Las prácticas serán escenarios, diagramas y decisiones.
- Condiciones de revisión: Solo por decisión explícita del participante.

## DEC-004 — Aprendizaje top-down

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El participante prefiere entender el sistema completo primero.
- Decisión: Cada módulo partirá de arquitectura y requisitos antes de servicios.
- Motivo: Favorece comprensión, atención y transferencia práctica.
- Impacto: Se evita un catálogo aislado de servicios.
- Condiciones de revisión: Evidencia de que el enfoque no ayuda al avance.

## DEC-005 — Evaluaciones de opción múltiple

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El examen usa selección de una o varias respuestas.
- Decisión: Las evaluaciones calificadas serán opción múltiple o respuesta múltiple.
- Motivo: Alinea práctica, feedback y distractores con el estilo de examen.
- Impacto: No se usarán tareas abiertas calificadas.
- Condiciones de revisión: No aplica para evaluaciones calificadas.

## DEC-006 — Casos de arquitectura recurrentes

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Se necesita integración progresiva.
- Decisión: Se usarán cuatro casos acumulativos de arquitectura.
- Motivo: Permiten reutilizar problemas y comparar decisiones.
- Impacto: Los módulos referenciarán casos cuando sea útil.
- Condiciones de revisión: Aparición de un caso más relevante para el participante.

## DEC-007 — Organización por chats

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Se requiere continuidad entre sesiones.
- Decisión: Existirá un chat de gobierno y chats separados por módulo.
- Motivo: Reduce mezcla entre decisiones globales y contenido didáctico.
- Impacto: El protocolo de chats debe seguirse antes de desarrollar módulos.
- Condiciones de revisión: Dificultad operativa demostrada.

## DEC-008 — Actualización mediante Codex CLI

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El repositorio local debe actualizarse con instrucciones controladas.
- Decisión: Codex actualizará archivos locales siguiendo prompts e instrucciones.
- Motivo: Mantiene trazabilidad entre conversación y repositorio.
- Impacto: ChatGPT produce instrucciones; Codex edita archivos.
- Condiciones de revisión: Cambio de herramienta de edición.

## DEC-009 — Jerarquía de fuentes

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Puede haber discrepancias entre materiales.
- Decisión: La guía oficial define alcance y la documentación oficial define comportamiento.
- Motivo: Evita basarse en material desactualizado.
- Impacto: `docs/FUENTES.md` registra prioridad y verificación.
- Condiciones de revisión: Nueva versión oficial del examen.

## DEC-010 — Protección de material de terceros

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El participante puede aportar diapositivas comerciales.
- Decisión: No se copiará ni redistribuirá material protegido.
- Motivo: Respetar derechos de autor y licencias.
- Impacto: Solo se registran referencias y síntesis originales.
- Condiciones de revisión: Ninguna sin autorización expresa verificable.

## DEC-011 — Revisiones acumulativas

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: El examen exige retención y transferencia.
- Decisión: Habrá repasos acumulativos y espaciados.
- Motivo: Fortalece conceptos débiles y reduce olvido.
- Impacto: Las evaluaciones futuras revisarán módulos anteriores.
- Condiciones de revisión: Ajuste del calendario de repaso.

## DEC-012 — Avance adaptable y cierre con alcance reducido

- Fecha: 2026-07-23
- Estado: Aprobada
- Contexto: Las sesiones pueden ocurrir después de la jornada laboral.
- Decisión: Un módulo puede cerrarse con alcance reducido por decisión del participante.
- Motivo: Mantener avance sin registrar dominio falso.
- Impacto: El estado debe diferenciarse de `Completado`.
- Condiciones de revisión: Si se acumulan cierres reducidos sin refuerzo.

## DEC-013 — Umbral definitivo de aprobación

- Fecha: 2026-07-23
- Estado: Propuesta
- Contexto: Se necesita criterio consistente.
- Decisión: Propuesta inicial: 80 % por módulo.
- Motivo: Busca evidencia suficiente sin fingir equivalencia con puntaje AWS.
- Impacto: Guía revisiones y refuerzos.
- Condiciones de revisión: Primeros resultados de evaluación.

## DEC-014 — Duración definitiva de módulos

- Fecha: 2026-07-23
- Estado: Propuesta
- Contexto: El participante estudia en sesiones cortas.
- Decisión: Propuesta inicial: 45 a 90 minutos.
- Motivo: Balance entre profundidad y energía disponible.
- Impacto: Puede dividir módulos extensos.
- Condiciones de revisión: Fatiga o módulos inconclusos recurrentes.

## DEC-015 — Repositorio público o privado

- Fecha: 2026-07-23
- Estado: Propuesta
- Contexto: El repositorio puede incluir desempeño personal.
- Decisión: Propuesta inicial: privado.
- Motivo: Protege registros académicos y referencias privadas.
- Impacto: Publicación requiere revisión de contenido sensible.
- Condiciones de revisión: Decisión explícita antes de publicar.

## DEC-016 — Calendario definitivo de repetición espaciada

- Fecha: 2026-07-23
- Estado: Propuesta
- Contexto: Se requiere repaso acumulativo.
- Decisión: Propuesta inicial: después de 2 módulos, a los 7 días y antes de simulacros.
- Motivo: Refuerza memoria sin saturar cada sesión.
- Impacto: Afecta evaluaciones acumulativas.
- Condiciones de revisión: Evidencia de olvido o sobrecarga.

## Decisiones pendientes

- DEC-013 — Umbral definitivo de aprobación.
- DEC-014 — Duración definitiva de módulos.
- DEC-015 — Repositorio público o privado.
- DEC-016 — Calendario definitivo de repetición espaciada.
