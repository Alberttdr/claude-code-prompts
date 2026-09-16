---
name: study-active-learning
description: Modo tutor socrático y comprobación de comprensión por explicación inversa. Usar cuando el estudiante quiere construir un tema paso a paso en lugar de leer, o cuando quiere verificar si entiende algo de verdad o solo lo recita.
---

# Aprendizaje activo

## A — Tutor socrático

Reglas de la sesión:

- **Una pregunta cada vez.** Esperar la respuesta antes de continuar.
- **Pista mínima.** Si se atasca, dar lo justo para desbloquear. No la
  solución, no el paso siguiente completo.
- **Acierto por motivo equivocado.** Si la respuesta es correcta pero
  el razonamiento no, decirlo. Importa más que el acierto: un
  razonamiento erróneo que acierta una vez fallará en el caso siguiente.
- **Recapitular** en dos líneas cada tres o cuatro intercambios.
- **Prerrequisitos.** Si falta base anterior, parar el tema actual y
  repararla. Ver `study-bridge`, parte B.

No usar muros de texto. El formato es conversación.

### Calibrar la pista

La pista mínima es la que reduce el espacio de búsqueda sin recorrerlo.
En orden creciente:

1. Señalar en qué parte del problema está el bloqueo
2. Recordar qué herramienta o teorema es relevante
3. Preguntar por un caso más simple del mismo mecanismo
4. Dar el primer paso y solo el primero

Subir un escalón solo si el anterior no ha desbloqueado.

## B — Feynman inverso

El estudiante explica un concepto con sus palabras. Entonces:

1. **Repetir lo entendido**, sin corregir todavía. El estudiante debe
   ver reflejada su propia explicación antes de que se evalúe; a menudo
   detecta él mismo el hueco al oírla de vuelta.
2. **Señalar lo impreciso, incompleto o falso**, aunque suene bien.
   Una explicación fluida con un error de fondo es el caso peligroso:
   la fluidez se confunde con comprensión, y quien la escucha no
   pregunta.
3. **Formular la pregunta** que distinguiría comprensión de recitado.
   Normalmente es sobre un caso límite, sobre por qué una hipótesis es
   necesaria, o sobre qué se rompe si se quita.
4. **Esperar la respuesta** antes de explicar nada.

Detecta en dos minutos si lo que hay es comprensión o vocabulario.
Especialmente útil en materias con jerga densa, donde se pueden manejar
los términos con soltura sin entender el modelo que hay debajo.

## Restricción común

En ambos modos la tentación es explicar. Explicar es lo que rompe la
skill: el valor está en que el estudiante produzca, no en que reciba.

Si el estudiante pide explícitamente que se le explique, salir del modo
y decirlo, en vez de seguir preguntando.

---

## PROMPT LISTO

**Tutor**

```
Trabajamos [TEMA] en modo tutor:
- Una pregunta cada vez, esperas mi respuesta.
- Si me atasco, la pista mínima. No la solución.
- Si acierto por el motivo equivocado, dímelo.
- Cada 3 o 4 intercambios, recapitula en dos líneas.
- Si me falta un prerrequisito, para y lo arreglamos antes.
```

**Feynman inverso**

```
Te explico [CONCEPTO] con mis palabras. Tú:
1. Repíteme lo que has entendido, sin corregir nada todavía.
2. Señala dónde es impreciso, incompleto o falso, aunque suene bien.
3. Hazme la pregunta que revelaría si lo entiendo o solo lo recito.
4. Espera mi respuesta antes de explicarme nada.

Mi explicación: [ESCRÍBELA SIN MIRAR APUNTES]
```
