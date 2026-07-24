# Curso Master

Versión inicial: 0.1

## 1. Identidad del curso

Nombre: AWS Solutions Architect Associate SAA-C03 — Arquitectura y preparación para el examen.

Tipo: curso personal de preparación conceptual, arquitectónica y evaluativa.

## 2. Perfil del participante

Desarrollador backend con experiencia en Node.js, TypeScript, NestJS, APIs REST, SQL, AWS y arquitecturas serverless. El diseño considera diagnóstico de TDAH, preferencia top-down, sesiones cortas y necesidad de material aplicable.

## 3. Propósito

Preparar al participante para aprobar el examen SAA-C03 y, sobre todo, razonar como Solutions Architect: interpretar requisitos, comparar servicios, detectar riesgos, evaluar costos y descartar distractores.

## 4. Resultado final esperado

El participante debe poder explicar y elegir arquitecturas seguras, resilientes, de alto rendimiento y rentables, justificando decisiones con requisitos explícitos y trade-offs.

## 5. Principios del curso

- Arquitectura antes que catálogo de servicios.
- Requisitos antes que productos.
- Trade-offs antes que reglas absolutas.
- Evidencia antes que sensación de dominio.
- Distractores antes que memorización aislada.
- Integración progresiva.
- Repaso espaciado.
- GitHub como fuente de verdad.
- Avance adaptable.
- Entretenimiento y variedad didáctica.

## 6. Adaptación top-down y TDAH

Cada bloque comienza con la interacción de componentes dentro de una arquitectura completa. Los servicios se estudian después de entender el problema que resuelven. Las sesiones pueden cerrarse con alcance reducido cuando el cansancio, la disponibilidad o la dificultad lo requieran.

## 7. Alcance

El alcance lo define la guía oficial vigente del examen SAA-C03. La documentación oficial de AWS define el comportamiento actual de los servicios. El curso cubre seguridad, resiliencia, rendimiento, costos, conectividad, cómputo, datos, integración, migración y preparación para preguntas estilo examen.

## 8. Exclusiones

- Crear recursos reales en AWS.
- Usar AWS Management Console.
- Usar AWS CLI.
- Usar SDK, CDK, Terraform, CloudFormation o Serverless Framework.
- Redistribuir material comercial o protegido.
- Copiar preguntas reales del examen.

## 9. Modalidad y duración

- Módulos normales: 45 a 90 minutos.
- Módulos integradores: 90 a 120 minutos.
- Sesiones cortas permitidas.
- El participante puede cerrar un módulo con alcance reducido.

## 10. Estrategia de aprendizaje

La estrategia combina mapas de arquitectura, comparación de alternativas, casos recurrentes, mini retos de decisión, evaluaciones con distractores plausibles, feedback por opción y repaso espaciado.

## 11. Estructura del curso

La estructura inicial tiene 30 módulos y puede ajustarse mediante decisiones registradas.

### Fase 0 — Orientación y contexto

1. Mapa de una arquitectura AWS
2. Cómo piensa un Solutions Architect
3. Los cuatro ejes del examen
4. Infraestructura global y alcance de los servicios

### Fase 1 — Fundamentos de protección y conectividad

5. Identidad, políticas y roles
6. Protección de datos, cifrado y secretos
7. VPC, subredes, rutas y conectividad
8. Seguridad de red y protección perimetral

### Fase 2 — Cómputo y escalabilidad

9. Selección de cómputo: EC2, Lambda, contenedores y Fargate
10. Elastic Load Balancing y Auto Scaling
11. Arquitecturas stateless, stateful y multinivel
12. Desacoplamiento, colas, eventos y workflows

### Fase 3 — Datos y almacenamiento

13. Almacenamiento de objetos, bloques y archivos
14. Amazon S3: protección, ciclo de vida y patrones
15. Bases de datos relacionales y Amazon Aurora
16. Amazon DynamoDB, NoSQL y patrones de acceso
17. Caché, réplicas y rendimiento de datos

### Fase 4 — Resiliencia y alcance global

18. Alta disponibilidad y tolerancia a fallos
19. Backups, RPO, RTO y recuperación ante desastres
20. Route 53, CloudFront y Global Accelerator
21. Arquitecturas Multi-Region e híbridas

### Fase 5 — Rendimiento, costos y datos

22. Optimización de cómputo y modelos de compra
23. Optimización de almacenamiento y bases de datos
24. Costos de red y transferencia
25. Ingesta, streaming, análisis y transformación

### Fase 6 — Integración y preparación

26. Revisión integral de arquitecturas
27. Patrones y anti-patrones del examen
28. Simulacro por dominio
29. Simulacro integral
30. Plan final de refuerzo

## 12. Casos de arquitectura

Los casos son escenarios acumulativos, no un proyecto técnico transversal. Evolucionan por decisiones registradas durante los módulos.

## 13. Sistema de evaluación

Las evaluaciones calificadas usan opción múltiple o respuesta múltiple. Deben medir razonamiento, incluir distractores plausibles y ocultar soluciones hasta después del intento.

## 14. Criterio de finalización

Un módulo se completa solo con aprobación explícita del participante y evidencia suficiente: evaluación, feedback, registro de errores y actualización de progreso.

## 15. Estrategia de fuentes

La guía oficial define alcance. La documentación oficial de AWS define comportamiento. AWS Well-Architected Framework aporta criterios. Materiales de preparación sirven como base temática sin copia ni redistribución.

## 16. Flujo entre ChatGPT, Codex y GitHub

ChatGPT consulta `main`, desarrolla y evalúa. Luego genera instrucciones para Codex. Codex actualiza el repositorio local. El participante revisa, commitea y publica cuando corresponda.

## 17. Artefactos finales

- Módulos documentados.
- Evaluaciones y resultados personales.
- Casos de arquitectura evolucionados.
- Matriz de cobertura.
- Registro de errores y conceptos débiles.
- Plan final de refuerzo.

## 18. Decisiones pendientes

Las decisiones pendientes se registran en `docs/DECISIONES.md`: umbral definitivo de aprobación, duración definitiva de módulos, visibilidad del repositorio y calendario definitivo de repetición espaciada.
