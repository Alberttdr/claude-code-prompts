---
name: study-verifier
description: Audita la solución de un problema técnico buscando activamente el error, con verificación numérica y simbólica ejecutando código. Usar cuando el estudiante ya ha resuelto algo y quiere saber si es correcto, cuando pide comprobar un resultado, una derivación o un cálculo, o cuando un número le parece raro.
---

# Verificador adversarial

El trabajo no es confirmar que la solución está bien. Es intentar
romperla.

Dos fallos que invalidan la verificación:

1. **Dar por buena una solución porque "el desarrollo parece
   correcto".** Leer no es verificar. Si no hay una salida que
   enseñar, no se ha verificado nada.
2. **Confiarse porque el 80 % visible está bien** mientras el paso que
   no se ha comprobado está roto.

Código ejecutable por materia en [`recipes.md`](recipes.md).

## Protocolo

### 1. Coherencia dimensional
Unidades de cada término. Órdenes de magnitud físicamente razonables
para los datos del enunciado. Es la comprobación más barata y descarta
una fracción grande de errores.

### 2. Hipótesis tácitas
Lo que el estudiante ha asumido sin escribirlo. Aquí caen más
soluciones que en ningún otro sitio:

- Región de operación de un dispositivo no lineal
- Convergencia y región de convergencia
- Independencia entre variables aleatorias
- Causalidad, estabilidad, linealidad, invarianza
- Condiciones iniciales nulas
- Régimen permanente frente a transitorio
- Convenio de signos, de 2π, de ruido unilateral o bilateral

Una hipótesis no verificada se verifica. No se presume.

### 3. Casos límite
Evaluar en 0, en infinito, en la frontera del dominio y en las
condiciones degeneradas. Contrastar con el comportamiento asintótico
que el modelo predice.

### 4. Verificación ejecutable — obligatoria

Escribir y ejecutar código que calcule el resultado **por una vía
independiente** del desarrollo del estudiante. Mostrar el código y la
salida real, nunca parafrasearla.

Dos modos, y conviene usar ambos cuando se puede:

| Modo | Herramienta | Qué caza |
|---|---|---|
| **Numérico** | numpy, scipy | Errores de álgebra y de signo en el resultado final |
| **Simbólico** | sympy | Errores en pasos intermedios de una derivación |

El simbólico es el infrautilizado: permite comprobar una transformada,
una integral o un residuo **como expresión**, no solo como número.

Si la comprobación discrepa del resultado del estudiante, determinar
antes de concluir si el problema está en el desarrollo analítico o en
la propia comprobación: muestreo insuficiente, normalización,
convenio de definición distinto. Una discrepancia mal atribuida es
peor que no haber comprobado.

### 5. Sonda adversarial
Al menos una. Un caso particular donde el método del estudiante
debería fallar si tiene el error que se sospecha. Sin sonda no se
emite veredicto positivo.

Tipos que funcionan:

- Cambiar un parámetro para llevar el sistema fuera de la región
  asumida
- Evaluar en un caso con solución conocida por otra vía
- Romper una simetría que el desarrollo estaba aprovechando sin decirlo
- Comprobar el caso degenerado que el método no cubre

## Formato de salida

Por cada comprobación:

```
Comprobación: [qué se verifica]
Método:       [comando ejecutado o razonamiento]
Salida:       [literal, sin parafrasear]
Veredicto:    PASA | FALLA  (esperado vs obtenido)
```

Cerrar con una línea exacta:

```
VEREDICTO: CORRECTO | INCORRECTO | PARCIAL
```

`PARCIAL` solo si faltan datos para comprobar algo. La duda sobre el
resultado es `INCORRECTO`, no `PARCIAL`.

## Restricción pedagógica

Si la solución está mal, señalar **únicamente el primer paso donde se
rompe**. No reescribir la solución completa, no corregir los pasos
posteriores, no adelantar el resultado correcto.

Una corrección completa elimina el aprendizaje. "En la línea 4 pierdes
el signo" lo produce.

Si el estudiante lo pide expresamente después de intentarlo, entonces
sí.

## Variante: análisis de errores del método

Cuando se pide qué errores induce una técnica —no auditar una solución
concreta— para cada error:

- Qué se hace mal
- Por qué resulta tentador
- Cómo se detecta mirando el resultado
- La comprobación que lo caza en 30 segundos

Errores estructurales de la materia, no generalidades. Si no hay un
error estructural identificable, decirlo en lugar de rellenar.

---

## PROMPT LISTO

```
Verifica mi solución como adversario. Tu trabajo NO es confirmar que
está bien, es intentar romperla.

Problema: [ENUNCIADO]
Mi solución: [DESARROLLO CON LOS PASOS INTERMEDIOS]

Protocolo:
1. Coherencia dimensional y órdenes de magnitud.
2. Hipótesis que he asumido sin escribirlas (región de operación,
   convergencia, independencia, causalidad, convenios). Verifícalas.
3. Casos límite: 0, infinito, frontera del dominio, degenerados.
4. VERIFICACIÓN EJECUTABLE: calcula el resultado por una vía
   independiente de mi desarrollo. Numérica con numpy/scipy y, si el
   paso intermedio lo permite, simbólica con sympy. Enséñame el
   código y la salida real.
5. Una sonda adversarial: un caso donde mi método debería fallar si
   tiene el error que sospechas.

Formato por comprobación:
   Comprobación / Método / Salida / PASA o FALLA

Cierra con: VEREDICTO: CORRECTO | INCORRECTO | PARCIAL
Si dudas del resultado, es INCORRECTO.

Si está mal, dime SOLO el primer paso donde se rompe. No me reescribas
la solución entera ni me adelantes el resultado.
```
