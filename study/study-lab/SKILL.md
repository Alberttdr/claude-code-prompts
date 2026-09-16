---
name: study-lab
description: Traduce código de simulación, esquemáticos, capturas de instrumento o datos de laboratorio a su modelo teórico, y guía la memoria técnica. Usar cuando el estudiante aporta material de práctica o pregunta qué está viendo en una medida o una gráfica.
---

# Traductor de laboratorio y simulación

Conecta la teoría con lo que realmente sale del montaje o del script.
Sin esto, se ejecutan simulaciones y se montan circuitos a ciegas.

## Estructura

### 1. Modelo teórico subyacente
Qué ecuación, filtro, respuesta en frecuencia, dispositivo o protocolo
está simulando o midiendo este entorno. Nombrarlo explícitamente antes
de entrar en detalles.

### 2. Traducción parámetro a parámetro
Cada constante, frecuencia de muestreo, valor de componente, condición
inicial o ajuste del instrumento, mapeado a su variable teórica.
Incluir unidades y factores de escala: es donde se cuelan los errores
silenciosos.

### 3. Anomalías esperables
Qué desviaciones entre teoría y medida son normales aquí y por qué:

- Cuantificación y resolución del convertidor
- Solapamiento espectral por muestreo insuficiente
- Tolerancias de los componentes
- Efectos de carga de la etapa siguiente
- Transitorios no extinguidos al tomar la medida
- Ruido de medida e inestabilidad numérica

Y, separadamente, qué desviaciones **no** son normales e indican que
algo está mal montado o mal configurado.

### 4. Qué debería verse
La forma del resultado si todo está bien, y la forma que tendría si
estuviera presente el error más probable.

Esta sección permite detectar el fallo en el propio laboratorio, con
tiempo de corregirlo, en lugar de descubrirlo escribiendo la memoria
en casa.

### 5. Guía de memoria técnica
Estructura de conclusiones, gráficos imprescindibles y la
justificación física exigible para cada resultado. Una conclusión sin
justificación física es una descripción, no una conclusión.

## Verificación

Si hay cálculos, ejecutarlos. Si hay datos, procesarlos y comparar con
el modelo teórico en lugar de afirmar que concuerdan.

Ver `study-verifier` para el protocolo completo.
