# study/ — Skills de estudio técnico

Adaptación de los patrones de este repositorio al estudio de ingeniería.
Los prompts originales están escritos para agentes de código; estos
aplican la misma disciplina —verificación adversarial, planificación
previa, memoria estructurada— a resolver problemas y estudiar teoría.

**Empieza por [`INDEX.md`](INDEX.md):** enruta desde lo que necesitas
hasta la skill que lo cubre.

## Skills

| Skill | Para qué | Prioridad |
|---|---|---|
| [`study-verifier`](study-verifier/) | Auditar una solución propia. Verificación numérica y simbólica ejecutando código. | **Alta** |
| [`study-planner`](study-planner/) | Elegir la vía de ataque antes de calcular. | **Alta** |
| [`study-consolidation`](study-consolidation/) | Ordenar una sesión caótica. Libro de errores personal. | **Alta** |
| [`study-drill`](study-drill/) | Generar tandas de problemas graduados sobre un mismo mecanismo. | Alta |
| [`study-trace`](study-trace/) | Trazas paso a paso: ensamblador, caché, pipeline, protocolos, autómatas. | Alta |
| [`study-notes`](study-notes/) | Redactar teoría a fondo desde material esquemático. | Media |
| [`study-exam`](study-exam/) | Simulacro con rúbrica, mapa de riesgo, calendario de repaso. | Media |
| [`study-lab`](study-lab/) | Traducir simulaciones, medidas y esquemáticos a teoría. | Media |
| [`study-bridge`](study-bridge/) | Conectar asignaturas y diagnosticar prerrequisitos flojos. | Media |
| [`study-active-learning`](study-active-learning/) | Tutor socrático y Feynman inverso. | Media |

[`subjects/uc3m-gitt-2.md`](subjects/uc3m-gitt-2.md) mapea cada
asignatura a las skills que más rinden y a sus errores estructurales.

## Formato de cada skill

Cada `SKILL.md` sirve a dos lectores:

1. **Un agente** que lo carga como instrucciones — la parte de
   metodología.
2. **Una persona** que lo abre y copia — el bloque `PROMPT LISTO` del
   final, autosuficiente y pegable tal cual en cualquier chat.

Si solo quieres usarlo, salta al bloque del final.

## Cómo usarlas

**En Cursor:** copiar las carpetas a `~/.cursor/skills-cursor/`.

**En chat:** pedir que se lea el archivo vía GitHub MCP, o pegar
directamente el bloque `PROMPT LISTO`.

## Principio de diseño

Una regla gobierna todo lo demás:

> El asistente no confirma que un resultado es correcto. Lo comprueba
> por una vía independiente y enseña la salida.

En matemáticas e ingeniería el asistente se equivoca igual que el
estudiante, y con más fluidez. La verificación ejecutable es el
mecanismo que caza ambos errores. Un desarrollo analítico largo sin
comprobación independiente no es una respuesta terminada.

[`study-verifier/recipes.md`](study-verifier/recipes.md) contiene el
código de verificación por materia, probado y con su salida real.

## Antipatrones que estas skills evitan

- **Prompt de N apartados en un mensaje.** Produce N secciones
  mediocres. Las tareas se encadenan, no se apilan.
- **Pedir datos que el modelo no tiene.** "Los errores más comunes en
  los exámenes de [universidad]" produce invención con apariencia de
  dato. Se piden errores estructurales de la materia, que sí son
  verificables.
- **Dar la solución corregida entera.** Elimina el aprendizaje. Se
  señala el primer paso que se rompe y nada más.
- **Verificar leyendo.** "El desarrollo parece correcto" no es una
  verificación. Si no hay una salida que enseñar, no se ha verificado.
