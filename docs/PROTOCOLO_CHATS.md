# Protocolo de chats

## Chat de gobierno

Nombre:

`00 - Diseño y gobierno del curso`

Responsabilidades:

- alcance;
- decisiones;
- documentos maestros;
- reorganización;
- seguimiento global;
- sin contenido didáctico de módulos.

## Chats de módulos

Formato:

`NN - Nombre oficial del módulo`

Procedimiento:

1. Consultar `main`.
2. Leer documentos maestros.
3. Detectar primer módulo no completado.
4. Informar nombre exacto del chat.
5. Informar documentos consultados.
6. Informar dominio y tareas oficiales.
7. Informar decisiones pendientes.
8. Esperar confirmación del cambio de nombre.
9. Desarrollar el módulo.
10. Evaluar.
11. Generar instrucciones para Codex.
12. No actualizar el progreso sin aprobación.

## Prompt completo para iniciar un nuevo módulo

```text
Consulta la rama main del repositorio del curso AWS Solutions Architect Associate SAA-C03.

Lee, en este orden:
1. docs/PROGRESO.md
2. docs/CURSO_MASTER.md
3. docs/DECISIONES.md
4. docs/PLANTILLA_MODULO.md
5. docs/CRITERIOS_EVALUACION.md
6. docs/MAPA_EXAMEN.md
7. docs/MATRIZ_COBERTURA.md
8. registros/CONCEPTOS_DEBILES.md

Detecta el primer módulo no completado.

Responde inicialmente solo con:
- nombre exacto del chat;
- módulo;
- documentos consultados;
- dominio SAA-C03;
- tareas oficiales cubiertas;
- decisiones pendientes relevantes.

Espera mi confirmación de que cambié el nombre del chat.
Después desarrolla el módulo respetando enseñanza top-down, restricciones del repositorio y separación entre intento y soluciones.
```
