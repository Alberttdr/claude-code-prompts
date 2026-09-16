# study/ — Skills de estudio técnico

Adaptación de los patrones de este repositorio al estudio de ingeniería.
Los prompts originales están escritos para agentes de código; estos
aplican la misma disciplina (verificación adversarial, planificación
previa, memoria estructurada) a resolver problemas y estudiar teoría.

Contexto de origen: 2º de Ingeniería en Tecnologías de la
Telecomunicación, UC3M. Los métodos son generales; lo específico de
las asignaturas está aislado en `subjects/`.

## Skills

| Skill | Para qué | Prioridad |
|---|---|---|
| `study-verifier/` | Auditar una solución propia. Verificación numérica ejecutando código. | **Alta** |
| `study-planner/` | Elegir la vía de ataque antes de calcular. | Alta |
| `study-notes/` | Redactar teoría a fondo y analizar los errores que induce el método. | Media |
| `study-consolidation/` | Ordenar una sesión caótica. Libro de errores personal. | Alta |
| `study-lab/` | Traducir código de simulación, medidas y esquemáticos a teoría. | Media |
| `study-exam/` | Simulacro con rúbrica y mapa de riesgo pre-examen. | Media |
| `study-active-learning/` | Tutor socrático, Feynman inverso, repaso activo. | Media |

`subjects/uc3m-gitt-2.md` mapea cada asignatura a las skills que más
rinden en ella y a sus errores estructurales.

## Cómo usarlas

**En Cursor:** copiar las carpetas a `~/.cursor/skills-cursor/`.

**En chat:** pedir que se lea el archivo vía GitHub MCP, o pegar
directamente el bloque de prompt.

## Principio de diseño

Una regla gobierna todo lo demás:

> El asistente no confirma que un resultado es correcto. Lo comprueba
> por una vía independiente y enseña la salida.

En matemáticas e ingeniería el asistente puede equivocarse igual que
el estudiante. La verificación numérica es el mecanismo que caza
ambos errores. Un desarrollo analítico largo sin comprobación
independiente no es una respuesta terminada.

## Antipatrones que estas skills evitan

- **Prompt de N apartados en un mensaje.** Produce N secciones
  mediocres. Las tareas se encadenan, no se apilan.
- **Pedir datos que el modelo no tiene.** "Los errores más comunes en
  los exámenes de [universidad]" produce invención con apariencia de
  dato. Se piden errores estructurales de la materia, que son
  verificables.
- **Dar la solución corregida entera.** Elimina el aprendizaje. Se
  señala el primer paso que se rompe y nada más.
