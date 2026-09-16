---
name: study-notes
description: Redacta teoría técnica a fondo a partir de diapositivas, PDF o notas sueltas, con demostraciones, rangos de validez y unidades. Usar cuando el estudiante empieza un tema nuevo o quiere convertir material esquemático en un texto autosuficiente.
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

Cada paso se apoya en el anterior ya escrito. No apilar.

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
confusión causan:

- Transformada de Fourier: variable `f` frente a `ω`, y dónde se
  coloca el factor 2π
- Densidad espectral de ruido: unilateral frente a bilateral
- Criterio de signos en circuitos y en realimentación
- Energía por bit frente a energía por símbolo

Al usar una fórmula de fuente externa, verificar qué convenio usa esa
fuente antes de mezclarla.

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
