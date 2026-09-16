# 2º GITT UC3M — mapa de asignaturas

Qué skills rinden más en cada asignatura y qué errores estructurales
cuestan más puntos.

> Los errores listados son de la **materia**, no estadística de
> exámenes de esta universidad. Afirmar lo segundo requeriría exámenes
> reales; de memoria sería inventarlo. Para lo específico del curso,
> aportar exámenes antiguos y analizarlos con el documento delante.

---

## Cuatrimestre 1

### Arquitectura de Sistemas
**Skills:** `study-trace` ★ · `study-verifier` · `study-drill` ·
`study-exam` C

Casi todo es comprobable ejecutando algo. `study-trace` es la skill
principal aquí: los problemas son secuencias de estados, no álgebra.
Recetas 7 y 8 de `study-verifier/recipes.md`.

**Errores estructurales:** fijar el índice de caché por número de
líneas en vez de por número de conjuntos · calcular los campos de
dirección en el orden equivocado · confundir latencia con
productividad al evaluar segmentación · olvidar ciclos de parada por
riesgos · extensión de signo · orden de bytes.

### Componentes y Circuitos Electrónicos
**Skills:** `study-verifier` ★ · `study-drill` · `study-notes` ·
`study-lab`

El bucle *asumir región → resolver → verificar la hipótesis* **es**
verificación adversarial. La skill se aplica sin adaptación. Receta 5.

`study-drill` rinde mucho aquí: la variación controlada ideal es mover
un parámetro hasta que el dispositivo cambia de región.

**Errores estructurales:** asumir la región de operación y no
verificarla nunca · mezclar el modelo de continua con el de pequeña
señal · anular mal las fuentes al pasar a pequeña señal · signo de la
ganancia · ignorar el efecto de carga de la etapa siguiente.

### Sistemas Lineales
**Skills:** `study-verifier` ★ · `study-planner` · `study-notes` ·
`study-bridge`

Verificación directa: convolucionar o transformar y comparar punto a
punto. Recetas 3 y 4. La verificación **simbólica** con sympy es
especialmente útil: transformada de ida y vuelta para comprobar un paso
intermedio.

`study-planner` para la decisión recurrente: resolver en tiempo o en
frecuencia.

**Errores estructurales:** omitir la región de convergencia (misma
expresión, sistemas distintos) · límites de integración mal en la
convolución · mezclar convenios de Fourier (`f` frente a `ω`,
colocación del 2π) · aplicar propiedades de LTI a sistemas que no lo
son · olvidar la condición de Nyquist.

Fijar el convenio del 2π el primer día y escribirlo en la primera
página de los apuntes.

### Probabilidad
**Skills:** `study-verifier` ★ · `study-drill` · `study-notes`

Monte Carlo contra el resultado analítico: si no coinciden, uno de los
dos está mal y suele verse cuál. Recetas 1 y 2.

Antes de nada, comprobar que la densidad integra 1. Un problema
construido sobre una densidad mal normalizada no se salva después.

**Errores estructurales:** confundir independencia con
incompatibilidad · invertir la condicionada · olvidar el jacobiano en
cambios de variable · límites del soporte mal en integrales dobles ·
aplicar el TCL con muestras insuficientes o dependientes.

### Fundamentos de Redes
**Skills:** `study-exam` C ★ · `study-trace` · `study-lab` ·
`study-verifier`

La menos matemática. Mucha nomenclatura —de ahí el repaso activo— y
una parte de cálculo muy mecánica que son puntos seguros: receta 9.

`study-trace` para los recorridos de paquete: qué cabecera se añade o
quita en cada salto, y qué dirección cambia y cuál no.

**Error estructural principal:** confundir el alcance de MAC e IP. La
IP de destino no cambia salto a salto; la MAC sí. Se enuncia bien de
palabra y se aplica mal en el problema escrito.

---

## Cuatrimestre 2

### Ampliación de Matemáticas
**Skills:** `study-planner` ★ · `study-verifier` · `study-drill`

Si incluye variable compleja, el riesgo principal es de **elección**,
no de cálculo: enumerar contornos candidatos antes de escribir nada.

Receta 11: la cuadratura numérica no sabe nada de contornos, así que
si coincide con el cálculo por residuos, el contorno era el correcto.
Es la verificación más útil de la asignatura.

**Errores estructurales:** contorno que no encierra los polos que se
cree · ignorar la contribución del arco al infinito sin justificar que
se anula · cortes de rama mal elegidos · confundir polo con
singularidad esencial.

### Análisis y Diseño de Circuitos
**Skills:** `study-planner` ★ · `study-verifier` · `study-lab` ·
`study-bridge`

Los problemas de diseño son abiertos —varias topologías válidas— así
que la fase de plan pesa tanto como el cálculo. Receta 6 para
contrastar el trazado asintótico del Bode.

Los tres puntos de control de un polo simple: −3 dB y −45° en la
frecuencia de corte, −20 dB/década por encima.

**Errores estructurales:** pendientes mal en las asíntotas · olvidar el
desfase que aportan los polos en la fase · signo del lazo en
realimentación · confundir polos con ceros al trazar.

### Teoría de la Comunicación
**Skills:** `study-verifier` ★ · `study-bridge` · `study-drill` ·
`study-active-learning`

Integra Probabilidad y Sistemas Lineales. Con esas dos sólidas es
exigente pero tratable; sin ellas, es un muro. Receta 10: simular la
BER contra la expresión teórica es la comprobación más informativa del
curso.

**Errores estructurales:** confundir Eb/N0 con SNR · densidad espectral
de ruido unilateral frente a bilateral (el factor 2) · no normalizar la
energía del símbolo al comparar modulaciones · argumento de la función
Q mal.

Buena parte de las discrepancias vienen de definiciones distintas de
SNR, no de errores de fondo. Verificar el convenio antes de concluir
que el desarrollo está mal.

**Antes de empezar:** `study-bridge` desde Probabilidad y Sistemas
Lineales, enfocado a lo que esta asignatura necesita.

### Redes y Servicios
**Skills:** `study-exam` C · `study-trace` · `study-lab` ·
`study-planner` · `study-bridge`

Continuación de Fundamentos, con más diseño y criterio.

**Error estructural principal:** arrastrar lagunas de Fundamentos sin
repasarlas. Revisar encapsulación y direccionamiento antes de empezar.

### Gestión de Empresas del Sector de Telecomunicaciones
**Skills:** `study-exam` C ★ · `study-verifier` solo para finanzas

Las skills de verificación aportan poco aquí, salvo VAN, TIR, ratios y
umbral de rentabilidad, que sí se comprueban: receta 12.

Elaborar apuntes extensos rinde menos que el repaso repetido. Es la
asignatura donde `study-exam` parte C es el método principal y no un
complemento.

---

## Dependencias entre cuatrimestres

```
Componentes  ─────────────────→  Análisis y diseño de circuitos
Sistemas Lineales  ───────┬───→  Teoría de la Comunicación
Probabilidad  ────────────┘
Sistemas Lineales  ───────────→  Análisis y diseño (resp. frecuencia)
Fundamentos de Redes  ────────→  Redes y Servicios
```

Cuatro de las cinco asignaturas del primer cuatrimestre son
prerrequisito directo de una del segundo. Los apuntes del primero se
reabren en el segundo: escribirlos con la sección "esto reaparece en"
que indica `study-notes`.

**Dependencia inversa:** Ampliación de Matemáticas explica en el
segundo cuatrimestre por qué funcionaba la transformada de Laplace que
en el primero se usó como receta. Anotar durante Sistemas Lineales las
preguntas que queden sin responder.

## Conflictos de convenio a vigilar

El mismo objeto con distinta definición según la asignatura. Producen
errores silenciosos porque el desarrollo sigue siendo coherente:

| Objeto | Dónde choca |
|---|---|
| Factor 2π en Fourier (`f` vs `ω`) | Sistemas Lineales ↔ Teoría de la Comunicación |
| Ruido unilateral vs bilateral | Probabilidad ↔ Teoría de la Comunicación |
| Energía por bit vs por símbolo | dentro de Teoría de la Comunicación |
| Criterio de signos de corriente | Componentes ↔ Análisis y diseño |
| Polos como `s` vs como frecuencia | Sistemas Lineales ↔ Análisis y diseño |

Usar `study-bridge` al detectar cualquiera de estos.
