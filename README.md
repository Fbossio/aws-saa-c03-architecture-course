# AWS Solutions Architect Associate SAA-C03 — Arquitectura y preparación para el examen

## Propósito

Este repositorio organiza un curso personal para preparar la certificación AWS Certified Solutions Architect - Associate SAA-C03. El foco es aprender a razonar arquitecturas, interpretar requisitos, comparar alternativas, reconocer trade-offs y descartar distractores plausibles.

## Perfil del participante

El participante es desarrollador backend con experiencia profesional en Node.js, TypeScript, NestJS, APIs REST, SQL, AWS y arquitecturas serverless. El curso asume preferencia por aprendizaje top-down, sesiones cortas después de la jornada laboral y necesidad de variedad didáctica.

## Principios del curso

- Arquitectura antes que catálogo de servicios.
- Requisitos antes que productos.
- Trade-offs antes que reglas absolutas.
- Evidencia antes que sensación de dominio.
- Repaso espaciado y avance adaptable.
- Ejercicios sin cuenta AWS, consola, CLI ni creación de recursos reales.

## Qué contiene este repositorio

- Documentos maestros de gobierno del curso.
- Seguimiento académico y decisiones.
- Plantillas para módulos.
- Casos de razonamiento arquitectónico.
- Evaluaciones de opción múltiple y respuesta múltiple.
- Registros de errores, conceptos débiles e historial.
- Prompts operativos para ChatGPT y Codex.

## Qué no contiene

- Recursos reales en AWS.
- Infraestructura como código.
- Comandos AWS CLI, SDK, CDK, Terraform, CloudFormation o Serverless Framework.
- Copias de diapositivas comerciales o material protegido.
- Preguntas reales del examen oficial.

## Fuente de verdad

Una vez publicado, GitHub y específicamente la rama `main` serán la única fuente de verdad. Las conversaciones con ChatGPT sirven para desarrollar contenido, pero solo se consideran consolidadas cuando quedan registradas en Git.

## Flujo de trabajo

1. ChatGPT consulta GitHub.
2. ChatGPT desarrolla el módulo.
3. ChatGPT evalúa al participante.
4. ChatGPT genera instrucciones para Codex.
5. Codex actualiza el repositorio local.
6. El participante revisa, hace commit y push.

## Cómo iniciar un módulo

Usar el prompt de `prompts/INICIAR_MODULO.md`. El agente debe leer los documentos maestros, detectar el primer módulo no completado y esperar confirmación antes de desarrollar contenido.

## Documentos maestros

- `docs/CURSO_MASTER.md`
- `docs/PROGRESO.md`
- `docs/DECISIONES.md`
- `docs/PLANTILLA_MODULO.md`
- `docs/CRITERIOS_EVALUACION.md`
- `docs/CASOS_ARQUITECTURA.md`
- `docs/MAPA_EXAMEN.md`
- `docs/MATRIZ_COBERTURA.md`
- `docs/GLOSARIO_DECISIONES.md`
- `docs/FUENTES.md`

## Estado inicial

Repositorio inicializado para gobierno documental del curso. Los 30 módulos están pendientes; no se han creado carpetas individuales de módulos.

## Aviso sobre material de terceros

Este repositorio no almacena copias de diapositivas comerciales. Las fuentes externas se registran por referencia en `docs/FUENTES.md`. El curso no necesita una cuenta AWS para sus ejercicios.
