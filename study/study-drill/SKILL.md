---
name: study-drill
description: Genera tandas de problemas graduados sobre un mismo mecanismo, con variaciones controladas y dificultad creciente, para automatizar un tipo de ejercicio. Usar cuando el estudiante ya entiende un método y necesita repetirlo, o cuando pide más problemas de un tipo concreto.
---

# Generador de tandas

Un problema resuelto enseña el método. Ocho problemas del mismo
mecanismo con una variable cambiando lo automatizan.

Esto no es un simulacro de examen —eso es `study-exam`— ni un problema
suelto. Es entrenamiento dirigido a **un** mecanismo.

## Requisito previo

El estudiante debe entender ya el mecanismo. Repetir sin comprender
fija el error, no el método. Si hay señales de que no lo entiende,
parar y derivar a `study-active-learning` o `study-notes`.

## Diseño de la tanda

### Estructura

```
1-2   Mecanismo desnudo. Sin complicaciones. Fijar el procedimiento.
3-5   Una variable cambia cada vez. Aislar qué la afecta.
6-7   El caso que rompe la receta: hay que decidir algo.
8     Caso límite o degenerado. Donde el método estándar no vale.
```

La progresión importa más que la cantidad. Ocho problemas graduados
valen más que veinte del mismo nivel.

### Variaciones controladas

Cambiar **una cosa** por problema, y que el estudiante pueda ver cuál:

- Un parámetro que cruza un umbral y cambia el régimen
- Una hipótesis que deja de cumplirse
- El dato que se da y el que se pide, invertidos
- Una simetría presente en unos casos y ausente en otros
- Datos que llevan a un resultado imposible (y hay que detectarlo)

El último tipo es el más valioso y el que menos aparece en las hojas de
ejercicios: un problema cuyo enunciado es incoherente o cuya solución
no tiene sentido físico, para entrenar la comprobación final.

### Formato

Enunciados numerados, **sin soluciones**. Al final, solo la respuesta
numérica de cada uno para autocorregir —no el desarrollo.

El desarrollo solo si el estudiante lo pide tras intentarlo, y
entonces siguiendo la restricción de `study-verifier`: primer paso que
se rompe, no solución completa.

### Coherencia de los datos

Los problemas generados deben tener solución y datos físicamente
razonables, salvo los que deliberadamente no la tengan. Verificar
ejecutando código antes de entregarlos: un generador que produce
ejercicios imposibles por descuido hace perder el tiempo y mina la
confianza en el resto.

## Variante: casos límite y cuestiones teóricas

Cuando lo que se necesita no es cálculo sino comprensión del modelo:

1. **Análisis de casos límite:** evaluación en la frontera, condiciones
   nulas, comportamiento asintótico en tiempo y en frecuencia, qué pasa
   cuando un parámetro tiende a 0 o a infinito.
2. **Tres cuestiones de desarrollo** de dificultad creciente, del tipo
   que se pregunta para distinguir aplicación mecánica de comprensión:
   por qué una hipótesis es necesaria, qué se rompe si se quita, qué
   pasa en el caso degenerado.
3. **No resolver hasta recibir la respuesta del estudiante.** Al
   corregir, indicar si el fallo es de concepto o de ejecución.

---

## PROMPT LISTO

```
Genera una tanda de 8 problemas sobre [MECANISMO] de [ASIGNATURA],
con dificultad creciente:
- 1-2: el mecanismo desnudo, sin complicaciones
- 3-5: una sola variable cambiando cada vez, para aislar qué afecta
- 6-7: el caso donde la receta estándar no basta y hay que decidir
- 8: caso límite o degenerado

Incluye al menos uno cuyos datos lleven a un resultado imposible, para
que tenga que detectarlo.

Dame solo los enunciados. Al final, las respuestas numéricas para
autocorregir, sin desarrollo.

Verifica ejecutando código que todos tienen solución coherente antes de
dármelos (salvo el que no debe tenerla).
```

```
A partir de este material de [ASIGNATURA]:
1. Una sección de análisis de casos límite: frontera, condiciones
   nulas, comportamiento asintótico, parámetros tendiendo a 0 o a inf.
2. Tres cuestiones teóricas de desarrollo, dificultad creciente.
3. NO me des la resolución hasta que te mande mi respuesta. Cuando te
   la mande, dime si el fallo es de concepto o de ejecución.

[MATERIAL]
```
