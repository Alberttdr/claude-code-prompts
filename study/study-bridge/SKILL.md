---
name: study-bridge
description: Conecta un tema con otras asignaturas, traduce entre notaciones y convenios distintos del mismo objeto, y diagnostica qué prerrequisito flojo está causando un atasco. Usar cuando algo ya se ha visto en otra asignatura y no encaja, al empezar una asignatura que depende de otras, o cuando el estudiante se atasca repetidamente en lo mismo.
---

# Puentes y prerrequisitos

## A — Conectar asignaturas

El mismo objeto matemático aparece en varias asignaturas con nombre,
notación y convenio distintos, y nadie avisa. El estudiante lo trata
como dos cosas separadas y estudia el doble.

Al conectar dos temas:

### 1. Qué es lo mismo
El objeto común, nombrado en los términos de cada asignatura. No basta
con decir que "están relacionados": identificar la correspondencia
exacta.

### 2. Qué notación cambia
Tabla de traducción, símbolo a símbolo. Casi siempre cambia algo.

### 3. Conflictos de convenio — lo importante
Donde el mismo símbolo significa cosas distintas, o el mismo concepto
lleva factores distintos. Estos son los que producen errores
silenciosos, porque el desarrollo sigue siendo internamente coherente:

- Variable `f` frente a `ω`, y dónde se coloca el factor 2π
- Densidad espectral de ruido unilateral frente a bilateral
- Energía por bit frente a energía por símbolo
- Criterio de signos de corriente y de realimentación
- Definiciones distintas de relación señal-ruido
- Logaritmo natural frente a decimal en expresiones de ganancia

Avisar **antes** de que el estudiante mezcle fórmulas de las dos
fuentes, no después.

### 4. Qué de esto reaparece
Qué del tema actual va a hacer falta más adelante, y con qué nivel de
detalle. Sirve para decidir qué merece apuntes cuidados y qué no.

### 5. Puentes retroactivos
A veces la asignatura posterior explica por qué funcionaba algo que la
anterior usó como receta. Señalarlo en ambos sentidos.

## B — Diagnosticar prerrequisitos

Muchos atascos no son del tema en curso: son de algo anterior que quedó
flojo y nunca se volvió a tocar. Seguir adelante sobre esa base no
funciona, y el estudiante lo interpreta como que el tema actual es
difícil.

### Señales

- El mismo tipo de error reaparece en temas distintos
- El estudiante sigue cada paso pero no puede reproducirlo solo
- Sabe aplicar la fórmula y no sabe cuándo no aplicarla
- Los fallos se concentran en un paso concreto del procedimiento

### Protocolo

1. **Aislar el paso** donde ocurre el fallo, no el tema.
2. **Proponer una comprobación mínima**: un ejercicio corto del
   prerrequisito sospechoso, no un repaso completo.
3. **Si falla, parar el tema actual.** Reparar la base primero. Es más
   rápido que avanzar arrastrando el hueco.
4. **Si no falla, descartar esa hipótesis explícitamente** y buscar
   otra. No dejar el diagnóstico abierto.

No diagnosticar de oído. Una hipótesis de prerrequisito flojo se
confirma con un ejercicio, no con una intuición.

---

## PROMPT LISTO

```
Estoy en [ASIGNATURA A] viendo [TEMA].

1. Cómo se conecta esto con [ASIGNATURA B]: qué objeto es el mismo,
   nombrado en los términos de cada una.
2. Tabla de traducción de notación entre ambas.
3. Conflictos de convenio: dónde el mismo símbolo significa cosas
   distintas o aparecen factores distintos (2pi, unilateral/bilateral,
   signos, por bit/por símbolo). Avísame ANTES de que mezcle fórmulas.
4. Qué de lo que estoy aprendiendo ahora me va a hacer falta allí, y
   con cuánto detalle.
```

```
Llevo varios problemas atascándome en lo mismo: [DESCRIBE EL ATASCO]

No me expliques el tema todavía. Primero:
1. Aísla el paso concreto donde falla, no el tema.
2. Dime qué prerrequisito sospechas y por qué.
3. Ponme UN ejercicio corto de ese prerrequisito para confirmarlo.
4. Si lo apruebo, descarta esa hipótesis y busca otra.
```
