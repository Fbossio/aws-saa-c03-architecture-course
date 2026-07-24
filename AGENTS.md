# Instrucciones para agentes

## Fuente de verdad

- La rama `main` de este repositorio es la única fuente de verdad.
- No asumir el progreso desde conversaciones anteriores.
- No depender de memoria contextual cuando el repositorio pueda consultarse.

## Orden obligatorio de lectura

Antes de desarrollar un módulo, leer:

1. `docs/PROGRESO.md`
2. `docs/CURSO_MASTER.md`
3. `docs/DECISIONES.md`
4. `docs/PLANTILLA_MODULO.md`
5. `docs/CRITERIOS_EVALUACION.md`
6. El archivo del módulo, si ya existe.

Leer además:

- `docs/CASOS_ARQUITECTURA.md` cuando haya escenarios integradores.
- `docs/MAPA_EXAMEN.md` para verificar dominio y tareas.
- `docs/MATRIZ_COBERTURA.md` para evitar huecos o duplicación.
- `registros/CONCEPTOS_DEBILES.md` al crear repasos o evaluaciones adaptativas.

## Reglas de contenido

- Enseñanza top-down.
- Arquitectura antes que catálogo.
- Requisitos antes que servicios.
- Trade-offs antes que reglas absolutas.
- Explicación en español.
- Nombres oficiales de servicios AWS conservados.
- Términos examinables en inglés cuando sea útil.
- No crear prácticas de consola ni CLI.
- No presentar un servicio como respuesta automática sin analizar requisitos.
- Diferenciar hechos de fuentes, interpretación didáctica, inferencias y decisiones del curso.

## Evaluaciones

- Solo opción múltiple o respuesta múltiple.
- No mostrar las soluciones antes del intento.
- Incluir distractores plausibles.
- Evaluar razonamiento y no solo memoria.
- Proporcionar feedback por opción.
- Registrar errores recurrentes.
- No marcar un módulo como completado sin aprobación explícita del participante.

## Cambios documentales

Actualizar solo el archivo correspondiente:

- progreso -> `docs/PROGRESO.md`;
- decisión global -> `docs/DECISIONES.md`;
- alcance -> `docs/CURSO_MASTER.md`;
- formato -> `docs/PLANTILLA_MODULO.md`;
- cobertura -> `docs/MATRIZ_COBERTURA.md`;
- resultados -> `registros/`;
- contenido didáctico -> directorio del módulo.

## Restricciones de escritura

- No modificar múltiples documentos maestros sin necesidad.
- No marcar actividades omitidas como completadas.
- Usar estados diferenciados.
- No hacer push automáticamente.
- No hacer commit salvo instrucción explícita.
