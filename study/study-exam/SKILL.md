---
name: study-exam
description: Genera simulacros de examen y los corrige con rúbrica distinguiendo error de concepto, método y cálculo; clasifica el temario por nivel de riesgo para priorizar el repaso; y genera cuestionarios de repaso activo. Usar en las semanas previas a un examen o cuando el estudiante pregunta qué repasar.
---

# Preparación de examen

Calendario del tramo final en [`calendar.md`](calendar.md).

## A — Simulacro con rúbrica

### Generación

Enunciados y nada más. Sin pistas, sin soluciones, sin indicar el
método esperado. Formato y duración realistas.

Un simulacro con ayudas no mide nada. Y debe cronometrarse: sin reloj
se pierde su función principal, que es comprobar si el método elegido
cabe en el tiempo disponible. Un procedimiento correcto que no entra en
el tiempo es un procedimiento equivocado para ese examen.

Distribuir la dificultad como un examen real, no todo al mismo nivel:
normalmente hay un problema asequible, dos medios y uno que separa.

### Corrección

Rúbrica por apartados con reparto de puntos explícito.

Clasificar cada fallo y decirlo:

| Tipo | Qué es | Remedio |
|---|---|---|
| **Concepto** | No entiende el modelo o lo aplica fuera de su dominio | Volver a la teoría |
| **Método** | Entiende el modelo pero elige mal la vía o el orden | Más `study-planner` |
| **Cálculo** | Planteamiento correcto, aritmética o álgebra mal | Más `study-drill` y comprobaciones |
| **Tiempo** | Sabía hacerlo y no llegó | Cambiar de vía, no estudiar más |

Esta clasificación es el valor central de la corrección. Confundir un
fallo de concepto con uno de cálculo hace perder semanas estudiando lo
que no era. Y el cuarto tipo suele pasar desapercibido: se interpreta
como falta de conocimiento cuando es un problema de elección de vía.

**Arrastre:** un error inicial propagado correctamente hasta el final
no es un cero. Marcarlo como arrastre y puntuar el resto por su mérito.

**Lo que sí estaba bien:** señalarlo. Una corrección que solo marca
fallos no informa de qué conservar.

Cerrar con la nota y las dos acciones concretas que más puntos
ganarían.

## B — Mapa de riesgo

```
BAJO   se resuelve con seguridad, método claro, poco margen de error
MEDIO  se sabe hacer, pero hay pasos donde se tropieza
ALTO   no se domina, o el método tiene trampas no controladas
```

Basarse en la evidencia disponible —soluciones vistas, libro de
errores, simulacros corregidos— no en suposiciones. Si no hay
evidencia sobre un tema, decirlo en lugar de clasificarlo a ciegas: un
tema sin evidencia es un riesgo desconocido, que es peor que un riesgo
alto.

Ante la duda entre dos niveles, asignar el más alto.

Para cada MEDIO y ALTO: la comprobación concreta que reduce el riesgo y
el tiempo de repaso que merece.

Esto es lo contrario de "repasar todo", que concentra las horas en lo
que ya se sabía porque es lo cómodo.

## C — Repaso activo

Para material que hay que retener, no razonar.

Cuestionarios con distractores plausibles —no obviamente falsos— y
explicación de por qué la respuesta correcta lo es. Recuperar
activamente fija mucho más que releer.

Cubrir todo lo acumulado, no solo lo último visto: el sesgo hacia el
tema reciente es el fallo habitual del repaso propio.

Los buenos distractores son los errores reales de la materia. El libro
de errores del estudiante es la mejor fuente de distractores
personalizados.

---

## PROMPT LISTO

**Generar**

```
Genera un examen de [ASIGNATURA], tema [X], para [90] minutos.
[N] problemas y [N] cuestiones teóricas, con dificultad distribuida
como un examen real (uno asequible, dos medios, uno que separa).
Dame los enunciados y NADA MÁS. Sin pistas ni soluciones.
```

**Corregir**

```
Aquí van mis respuestas: [TUS RESPUESTAS]

Corrige con rúbrica por apartados y reparto de puntos.
Clasifica cada fallo como CONCEPTO, MÉTODO, CÁLCULO o TIEMPO, y dime
cuál es cada uno: el remedio es distinto para cada tipo.
Si un fallo inicial se arrastra bien hasta el final, márcalo como
arrastre y puntúa el resto.
Señala también lo que sí estaba bien.
Cierra con la nota y las dos cosas que más puntos me harían ganar.
```

**Mapa de riesgo**

```
Clasifica los tipos de problema de [ASIGNATURA] en BAJO / MEDIO / ALTO
según lo que hayas visto de mis soluciones y errores, no supongas.
Si no tienes evidencia de algún tema, dilo en vez de clasificarlo a
ciegas.
Para cada MEDIO y ALTO: la comprobación que reduce el riesgo y cuánto
tiempo de repaso merece. Ante la duda, el nivel más alto.
```

**Repaso activo**

```
Cuestionario de [N] preguntas sobre [TEMA], cubriendo todo lo
acumulado y no solo lo último. Distractores plausibles basados en
errores reales de la materia. Explicación de por qué cada respuesta
correcta lo es.
```
