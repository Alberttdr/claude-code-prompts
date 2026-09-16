# 2º GITT UC3M — mapa de asignaturas

Qué skill rinde más en cada asignatura y qué error estructural cuesta
más puntos. Los errores listados son de la **materia**, no estadística
de exámenes de esta universidad: eso requeriría exámenes reales, y
afirmarlo de memoria sería inventarlo.

---

## Cuatrimestre 1

### Arquitectura de Sistemas
**Skills:** `study-verifier` ★, `study-consolidation`, `study-exam`

Casi todo es comprobable ejecutando algo: trazar la ejecución
instrucción a instrucción, simular una secuencia de accesos y contar
aciertos reales, aplicar una fórmula de CPI y contrastarla con el
ciclo a ciclo.

**Errores estructurales:** repartir mal los bits de dirección en caché
por no fijar primero el tamaño de bloque · confundir latencia con
productividad al evaluar segmentación · olvidar los ciclos de parada
por riesgos · extensión de signo · orden de bytes.

### Componentes y Circuitos Electrónicos
**Skills:** `study-verifier` ★, `study-notes`, `study-lab`

El bucle *asumir región → resolver → verificar la hipótesis* **es**
verificación adversarial. La skill se aplica sin adaptación.

**Errores estructurales:** asumir la región de operación y no
verificarla nunca · mezclar el modelo de continua con el de pequeña
señal · anular mal las fuentes al pasar a pequeña señal · signo de la
ganancia · ignorar el efecto de carga de la etapa siguiente.

### Sistemas Lineales
**Skills:** `study-verifier` ★, `study-planner`, `study-notes`

La comprobación numérica es directa: convolucionar o transformar y
comparar punto a punto con el resultado analítico.

**Errores estructurales:** omitir la región de convergencia (misma
expresión, sistemas distintos) · límites de integración mal en la
convolución · mezclar convenios de la transformada de Fourier (`f`
frente a `ω`, colocación del 2π) · aplicar propiedades de LTI a
sistemas que no lo son · olvidar la condición de Nyquist.

Fijar el convenio del 2π el primer día y escribirlo en la primera
página de los apuntes.

### Probabilidad
**Skills:** `study-verifier` ★, `study-notes`

Monte Carlo contra el resultado analítico. Si no coinciden, uno de los
dos está mal y suele verse cuál.

**Errores estructurales:** confundir independencia con
incompatibilidad · invertir la condicionada · olvidar el jacobiano en
cambios de variable · límites del soporte mal en integrales dobles ·
aplicar el TCL con muestras insuficientes o dependientes.

### Fundamentos de Redes
**Skills:** `study-exam` (parte C) ★, `study-lab`, `study-verifier`

La menos matemática. Mucha nomenclatura y una parte de cálculo muy
mecánica —direccionamiento y subredes— que son puntos seguros si no se
falla. Verificable con `ipaddress`.

**Error estructural principal:** confundir el alcance de MAC e IP. La
IP de destino no cambia salto a salto; la MAC sí. Se enuncia bien de
palabra y se aplica mal en el problema escrito.

---

## Cuatrimestre 2

### Ampliación de Matemáticas
**Skills:** `study-planner` ★, `study-verifier`

Si incluye variable compleja, el riesgo principal es de **elección**,
no de cálculo. Enumerar contornos candidatos antes de escribir nada.
Contrastar el resultado por residuos con cuadratura numérica.

**Errores estructurales:** contorno que no encierra los polos que se
cree · ignorar la contribución del arco al infinito sin justificar que
se anula · cortes de rama mal elegidos · confundir polo con
singularidad esencial.

### Análisis y Diseño de Circuitos
**Skills:** `study-planner`, `study-verifier`, `study-lab`

Los problemas de diseño son abiertos: varias topologías válidas, así
que la fase de plan pesa tanto como el cálculo.

**Errores estructurales:** pendientes mal en las asíntotas del Bode ·
olvidar el desfase que aportan los polos en la fase · signo del lazo
en realimentación · confundir polos con ceros al trazar.

### Teoría de la Comunicación
**Skills:** `study-verifier` ★, `study-active-learning`

Integra Probabilidad y Sistemas Lineales. Con esas dos sólidas es
exigente pero tratable; sin ellas, es un muro. Simular la BER contra
la expresión teórica es la comprobación más informativa del curso.

**Errores estructurales:** confundir Eb/N0 con SNR · densidad
espectral de ruido unilateral frente a bilateral (el factor 2) · no
normalizar la energía del símbolo al comparar modulaciones · argumento
de la función Q mal.

Buena parte de las discrepancias en esta asignatura vienen de
definiciones distintas de SNR, no de errores de fondo. Verificar el
convenio antes de concluir que el desarrollo está mal.

### Redes y Servicios
**Skills:** `study-exam` (parte C), `study-lab`, `study-planner`

Continuación de Fundamentos, con más diseño y criterio.

**Error estructural principal:** arrastrar lagunas de Fundamentos sin
repasarlas. Revisar encapsulación y direccionamiento antes de empezar.

### Gestión de Empresas del Sector de Telecomunicaciones
**Skills:** `study-exam` (parte C) ★, `study-verifier` solo para
finanzas

Las skills de verificación aportan poco aquí, salvo para VAN, TIR,
ratios y umbral de rentabilidad, que sí se comprueban numéricamente.
Elaborar apuntes extensos rinde menos que el repaso repetido.

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
reabren en el segundo: conviene escribirlos con la sección "esto
reaparece en" que indica `study-notes`.

**Dependencia inversa:** Ampliación de Matemáticas explica en el
segundo cuatrimestre por qué funcionaba la transformada de Laplace que
en el primero se usó como receta. Anotar durante Sistemas Lineales las
preguntas que queden sin respuesta.

**Antes de empezar Teoría de la Comunicación:** repaso puente desde
Probabilidad y Sistemas Lineales enfocado a lo que esa asignatura
necesita.
