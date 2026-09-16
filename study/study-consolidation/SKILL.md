---
name: study-consolidation
description: Ordena una sesión de ejercicios en formulario, teoría, mapa de atajos y soluciones limpias, y extrae los errores recurrentes como memoria duradera. Usar al cerrar una sesión de estudio, cuando el estudiante tiene un desorden de borradores, o cuando quiere saber en qué falla sistemáticamente.
---

# Consolidación de sesión

Diez minutos al cerrar. Convierte cuatro horas de borradores en algo
recuperable en junio.

Solo texto. Todo el material está en la conversación; no hacen falta
herramientas.

## Parte A — Documento de síntesis

### 1. Formulario y condiciones de aplicación
Fórmulas en LaTeX. De cada una: cuándo se aplica y, sobre todo, cuándo
**no** puede usarse. Una fórmula sin su dominio de validez es una
trampa: se aplica con confianza donde no toca y el error es invisible.

### 2. Teoría clave extraída
Los teoremas y resultados concretos de los que ha dependido cada
resolución. Con rigor, no como lista de nombres.

### 3. Mapa de decisión y atajos
Árbol explícito, redactado como reglas que se disparan al ver la forma
del enunciado:

```
Si el enunciado tiene la estructura X  →  usar el atajo Y
Si aparece la condición Z              →  aplicar la transformación W
Si falta el dato W                     →  la vía directa no sirve, usar V
```

No consejos generales. Reglas ejecutables.

### 4. Soluciones limpias
Los mismos problemas reescritos en su versión directa, sin el caos del
borrador. Es la versión que se relee, no la del cuaderno.

### 5. Dónde se ha atascado
Los puntos de duda, error o reintento, con el patrón común si lo hay.
Es el bloque con más valor a tres meses vista.

### 6. Qué no ha salido hoy
Casos del tema que no han aparecido y que podrían caer igualmente. Una
sesión de problemas cubre un subconjunto sesgado del temario.

## Parte B — Libro de errores

Extracción de memorias duraderas. Solo patrones, no incidentes
aislados.

```
ERROR:        qué se hace mal, en una frase
EVIDENCIA:    dónde ha ocurrido en esta sesión
DISPARADOR:   qué tipo de enunciado lo provoca
CONTRAMEDIDA: la comprobación concreta que lo evita
CONFIANZA:    alta | media | baja
```

Agrupar por tema, no por orden cronológico. Si un error ya estaba
identificado en sesiones anteriores, subir su confianza en lugar de
duplicar la entrada. Si una entrada queda contradicha por evidencia
nueva, sustituirla. Convertir referencias temporales relativas
("la semana pasada") en absolutas.

Pocas entradas fuertes valen más que muchas débiles.

Este archivo, releído antes de un examen, rinde más que releer los
apuntes: ataca lo que falla este estudiante, no lo que falla la media.

El campo `DISPARADOR` es el que lo hace utilizable: sin él, el libro
de errores es una lista de reproches; con él, es un sistema de alerta
que se activa al leer el enunciado.

## Parte C — Bitácora de asignatura (opcional)

Secciones fijas, densas en información, con nombres exactos y
referencias a ejercicios concretos:

```
ESTADO ACTUAL          (actualizar siempre)
TEMARIO CUBIERTO
FORMULARIO ACUMULADO
ERRORES RECURRENTES
DUDAS SIN RESOLVER
TIPOS DE PROBLEMA DOMINADOS
PENDIENTE
```

Si una sección no tiene novedad, dejarla como está.

`DUDAS SIN RESOLVER` es la sección que hay que llevar a tutoría. Una
duda escrita con precisión se responde en dos minutos; una duda vaga
consume la tutoría entera.

---

## PROMPT LISTO

**Al cerrar la sesión**

```
Consolida esta sesión sobre [ASIGNATURA / TEMA] en 6 bloques. Solo
texto, todo está ya en la conversación.

1. FORMULARIO: fórmulas en LaTeX con sus condiciones de aplicación y,
   sobre todo, cuándo NO se pueden usar.
2. TEORÍA CLAVE: los teoremas concretos de los que ha dependido hoy.
3. MAPA DE DECISIÓN: reglas ejecutables del tipo "si el enunciado
   tiene X -> atajo Y", no consejos generales.
4. SOLUCIONES LIMPIAS: los problemas de hoy en su versión directa.
5. DÓNDE ME HE ATASCADO: puntos de duda o reintento, con el patrón.
6. QUÉ NO HA SALIDO HOY: casos del tema que podrían caer igual.
```

**Justo después**

```
Extrae mis errores de esta sesión como memoria duradera. Solo patrones.

Cada entrada:
   ERROR / EVIDENCIA / DISPARADOR / CONTRAMEDIDA / CONFIANZA

Agrupa por tema. Si ya lo tenía detectado antes, súbele la confianza en
vez de duplicarlo. El DISPARADOR es lo importante: qué tengo que ver
en un enunciado para que me salte la alarma.
```
