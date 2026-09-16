---
name: study-notes
description: Redacta teoría técnica a fondo a partir de diapositivas, PDF o notas sueltas, con demostraciones, rangos de validez, unidades y convenios explícitos. Usar cuando el estudiante empieza un tema nuevo o quiere convertir material esquemático en un texto autosuficiente.
---

# Redacción de teoría

Apuntes, no resúmenes. El material de partida ya suele ser un esquema;
resumirlo otra vez no aporta nada.

## Cadena de tres pasos

Un solo prompt que pida teoría, propiedades, errores, metodología y un
ejercicio resuelto produce cinco secciones mediocres. Se encadena:

1. **Teoría** — este documento
2. **Errores del método** — `study-verifier`, variante final
3. **Caso práctico** — `study-planner`, variante de resolución modelo

Cada paso se apoya en el anterior ya escrito. Con la teoría delante, el
análisis de errores sale concreto; sin ella, sale genérico.

## Estructura del paso 1

### Por cada resultado

- Enunciado preciso
- Hipótesis bajo las que es válido
- Demostración o justificación
- Rango exacto de aplicabilidad

### Por cada ecuación

Variable por variable, con unidades. Un símbolo sin definir es una
laguna, no una abreviatura.

### Etiquetado explícito

Marcar qué es **definición**, qué es **teorema** y qué es
**aproximación de ingeniería**.

En las aproximaciones, obligatorio: qué se desprecia y cuándo deja de
ser legítimo despreciarlo. Los problemas de examen empujan
deliberadamente fuera del rango cómodo, y una aproximación aplicada
fuera de su dominio es un error invisible: el desarrollo posterior
sigue siendo correcto y el resultado es falso.

### Notación y convenios

Fijar el convenio y hacerlo explícito la primera vez. Los que más
confusión causan están catalogados en `study-bridge`, parte A.3.

Al usar una fórmula de fuente externa, verificar qué convenio usa esa
fuente antes de mezclarla con el del curso.

### Sección final: "esto reaparece en"

Dónde vuelve a hacer falta el tema más adelante. Los apuntes de un
primer cuatrimestre se reabren en el segundo; escribirlos sin esa
sección hace que se reabran sin contexto.

## Nivel

Segundo curso de grado. Ni divulgativo ni formalismo de posgrado.
LaTeX para las ecuaciones.

## Cuándo no usar esta skill

Si el estudiante ya tiene un libro de texto o unos apuntes sólidos del
profesor. Reescribir buen material no aporta; la capa que sí aporta es
la de errores, atajos y verificación.

---

## PROMPT LISTO

**Mensaje 1 — teoría**

```
Asignatura: [X]. Tema: [Y].
Redáctame el desarrollo teórico completo, no un resumen ni un esquema.
Por cada resultado: enunciado preciso, hipótesis bajo las que es
válido, demostración o justificación, y rango exacto de aplicabilidad.
Cada ecuación explicada variable por variable con sus unidades.
Marca qué es definición, qué es teorema y qué es aproximación de
ingeniería; en las aproximaciones, qué se desprecia y cuándo deja de
ser legítimo despreciarlo.
Fija explícitamente los convenios de notación que uses.
Termina con una sección "esto reaparece en".
Ecuaciones en LaTeX. Nivel de 2º de grado.

Entrada: [PDF / DIAPOSITIVAS / NOTAS]
```

**Mensaje 2 — errores** (tras leer el anterior)

```
Sobre esa teoría: los errores estructurales que induce el propio
método. No genéricos: los puntos concretos donde la técnica invita a
equivocarse.
Por cada uno: qué se hace mal, por qué es tentador, cómo se detecta
mirando el resultado, y la comprobación que lo caza en 30 segundos.
Si alguno no lo tienes identificado como estructural, dilo en vez de
rellenar.
```

**Mensaje 3 — caso práctico**

```
Ahora un ejercicio de nivel examen sobre lo anterior, por la vía más
corta defendible, indicando en cada paso qué propiedad usas y por qué
es aplicable aquí. Termina con verificación dimensional y casos límite.
```
