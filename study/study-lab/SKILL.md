---
name: study-lab
description: Traduce código de simulación, esquemáticos, capturas de instrumento o datos de laboratorio a su modelo teórico, anticipa qué debería verse y guía la memoria técnica. Usar cuando el estudiante aporta material de práctica o pregunta qué está viendo en una medida o una gráfica.
---

# Traductor de laboratorio y simulación

Conecta la teoría con lo que sale del montaje o del script. Sin esto,
se ejecutan simulaciones y se montan circuitos a ciegas.

## Estructura

### 1. Modelo teórico subyacente
Qué ecuación, filtro, respuesta en frecuencia, dispositivo o protocolo
está simulando o midiendo este entorno. Nombrarlo explícitamente antes
de entrar en detalles.

### 2. Traducción parámetro a parámetro
Cada constante, frecuencia de muestreo, valor de componente, condición
inicial o ajuste del instrumento, mapeado a su variable teórica, con
unidades y factores de escala. Es donde se cuelan los errores
silenciosos.

### 3. Anomalías esperables
Qué desviaciones entre teoría y medida son normales aquí y por qué:

- Cuantificación y resolución del convertidor
- Solapamiento espectral por muestreo insuficiente
- Tolerancias de los componentes
- Efectos de carga de la etapa siguiente
- Transitorios no extinguidos al tomar la medida
- Ruido de medida e inestabilidad numérica
- Fuga espectral por ventana finita

Y, separadamente, qué desviaciones **no** son normales e indican que
algo está mal montado o mal configurado. La distinción es el valor de
esta sección: sin ella, cualquier discrepancia se justifica como
"error experimental".

### 4. Qué debería verse
La forma del resultado si todo está bien, y la forma que tendría si
estuviera presente el error más probable.

Esta sección permite detectar el fallo **en el laboratorio**, con
tiempo de corregirlo, en lugar de descubrirlo escribiendo la memoria.
Es la que más tiempo ahorra y la que casi nunca se escribe.

### 5. Guía de memoria técnica
Estructura de conclusiones, gráficos imprescindibles y la
justificación física exigible para cada resultado. Una conclusión sin
justificación física es una descripción, no una conclusión.

Incluir qué no debe ir: gráficos redundantes, capturas sin analizar y
valores sin incertidumbre asociada.

## Verificación

Si hay cálculos, ejecutarlos. Si hay datos, procesarlos y comparar con
el modelo en lugar de afirmar que concuerdan. Recetas por materia en
`study-verifier/recipes.md`.

Si el material aportado es código del estudiante, revisarlo también
como código: un error de índice o una normalización olvidada produce
una gráfica plausible y falsa.

---

## PROMPT LISTO

```
Procesa este material de laboratorio de [ASIGNATURA]:
[CÓDIGO PYTHON/MATLAB / ESQUEMÁTICO / CAPTURA / DATOS]

1. MODELO TEÓRICO: qué ecuación, dispositivo o protocolo hay detrás.
2. PARÁMETRO A PARÁMETRO: cada constante, frecuencia, componente o
   ajuste, mapeado a su variable teórica, con unidades y escalas.
3. ANOMALÍAS: qué desviaciones teoría-medida son normales aquí y por
   qué, y por separado cuáles indicarían que algo está mal montado.
4. QUÉ DEBERÍA VER: la forma del resultado si está bien, y la forma
   que tendría con el error más probable presente.
5. MEMORIA: estructura, gráficos imprescindibles, justificación física
   de cada conclusión, y qué NO debe incluirse.

Si hay cálculos o datos, verifícalos ejecutando código. Si el código es
mío, revísalo también como código.
```
