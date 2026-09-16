---
name: study-planner
description: Explora vías de resolución de un problema técnico y recomienda una, sin resolverlo. Usar cuando el estudiante no sabe por dónde empezar, cuando hay varios caminos posibles con costes distintos, o cuando pide ayuda para plantear un problema antes de calcular.
---

# Planificador de resolución

No resolver el problema. Elegir cómo se va a resolver.

Lo que hace perder un examen no suele ser el álgebra: es elegir mal el
camino en el minuto uno y descubrirlo veinte minutos después, sin
tiempo para rehacerlo.

## Cuándo aplicar

- El planteamiento estándar no es evidente
- Hay dos o más vías viables con costes distintos
- El problema es largo y un error temprano se propaga
- El estudiante dice que no sabe por dónde entrar

**Cuándo no:** problema de un paso, aplicación directa de fórmula, o el
estudiante ya tiene plan y solo quiere contrastarlo.

## Salida

### 1. Qué se pide realmente
Reformular el objetivo en una frase. Separar los datos relevantes del
ruido: los enunciados largos incluyen información que no se usa, y
perseguirla cuesta minutos.

Señalar también lo que el enunciado **no** dice y hay que asumir.

### 2. Vías candidatas
Dos o tres, no más. De cada una:

- En qué resultado teórico se apoya
- Número aproximado de pasos
- Dónde es fácil equivocarse
- Coste en tiempo de examen

### 3. Recomendación
Una, justificada **para este enunciado**. "El método X suele ser más
rápido" no es justificación. "Aquí la función es par, así que X elimina
la mitad de los términos" sí lo es.

Si existe una vía más lenta pero más robusta, decir cuál es y cuándo
conviene. Con poco margen de tiempo o bajo nervios, la vía segura
puede ser la decisión correcta aunque cueste cinco minutos más.

### 4. Secuencia con puntos de control
Pasos ordenados y, en cada etapa, qué comprobar antes de seguir. Un
punto de control es una comprobación barata que detecta el error antes
de que se propague: un signo, una unidad, un caso límite parcial.

### 5. Supuestos frágiles
Qué se asume que, de ser falso, invalidaría el plan entero. Es la
sección que evita rehacerlo todo en el minuto 40.

## Después del plan

El estudiante resuelve. No adelantar desarrollo ni resultado. Si se
atasca, atender al paso concreto, no reabrir el problema completo.

## Variante: resolución modelo

Cuando se pide explícitamente un problema resuelto como referencia:

1. Desarrollo teórico mínimo que lo fundamenta
2. Resolución por la vía más corta defendible, indicando en cada paso
   qué propiedad o atajo se usa y por qué es aplicable **aquí**
3. Criterio de verificación física y dimensional comprobable en menos
   de 30 segundos
4. La alternativa más lenta y segura, si existe

Advertir si se detecta que se pide la resolución sin haberlo
intentado: ver resolver no enseña a resolver.

---

## PROMPT LISTO

```
Modo plan sobre este problema. NO lo resuelvas todavía.

[ENUNCIADO]

1. Qué pide realmente, qué datos son ruido y qué no dice el enunciado
   que yo tenga que asumir.
2. Dos o tres vías de ataque. De cada una: en qué se apoya, cuántos
   pasos tiene, dónde es fácil equivocarse y cuánto tiempo consume.
3. Recomienda una y justíficalo para ESTE enunciado concreto, no en
   abstracto. Si hay una vía más lenta pero más segura, dime cuál y
   cuándo me conviene.
4. Secuencia de pasos con puntos de control: qué compruebo en cada
   etapa antes de seguir.
5. Qué estoy asumiendo que, si fuera falso, tiraría el plan abajo.

Después lo resuelvo yo. Si me atasco te digo en qué paso concreto.
```
