---
name: study-trace
description: Traza la ejecución paso a paso de un sistema discreto —ensamblador, caché, pipeline, autómatas, intercambios de protocolo— en forma de tabla de estados, y localiza el primer paso donde una traza del estudiante diverge. Usar cuando el estudiante se pierde siguiendo una secuencia de estados o su conteo no cuadra.
---

# Trazador de ejecución

Hay una familia de problemas que no se resuelven con álgebra sino
siguiendo estados: qué contiene cada registro tras cada instrucción,
qué bloque ocupa cada vía de la caché, qué etapa ocupa cada
instrucción en cada ciclo, qué mensaje va en cada sentido.

Son implacables con el detalle: un bit mal en el paso 3 invalida el
resto, y el error es invisible porque todo lo demás sigue siendo
correcto.

## Método

### 1. Fijar el modelo antes de trazar

Explicitar lo que el enunciado da por supuesto, porque distintos
convenios producen trazas distintas:

- Número de etapas del pipeline y qué hace cada una
- Si hay adelantamiento de operandos y de dónde a dónde
- Política de reemplazo y de escritura de la caché
- Orden de bytes, extensión de signo, tamaño de palabra
- Quién inicia el intercambio y con qué temporizadores

Si el enunciado no lo fija, decirlo y elegir un convenio
explícitamente en vez de asumirlo en silencio.

### 2. Tabla de estados

Una fila por paso, una columna por elemento de estado. Nunca prosa:
la prosa oculta justo el detalle que importa.

```
Ciclo | IF    | ID    | EX    | MEM   | WB    | Parada
------|-------|-------|-------|-------|-------|--------
1     | I1    |       |       |       |       |
2     | I2    | I1    |       |       |       |
3     | I3    | I2    | I1    |       |       |
4     | I3    | I2    | —     | I1    |       | RAW I1→I2
```

Marcar explícitamente las paradas, los vaciados y los fallos, con su
causa. Un ciclo perdido sin causa anotada es un ciclo que no se puede
auditar.

### 3. Verificar ejecutando

Escribir el simulador. Es corto —ver `study-verifier/recipes.md`,
recetas 7 y 8— y elimina el error aritmético del conteo.

Contrastar además con un razonamiento agregado independiente: número
de fallos obligatorios por capacidad, límite teórico de la
segmentación, cota inferior de ciclos. Si la traza y el agregado no
cuadran, hay un error en uno de los dos.

### 4. Comparar con la traza del estudiante

Localizar **el primer paso donde divergen** y parar ahí. No mostrar la
traza correcta completa: a partir del punto de divergencia, el
estudiante puede rehacerla.

## Errores estructurales de esta familia

- Fijar el índice de caché por el número de líneas en lugar de por el
  número de **conjuntos**
- Calcular los campos de dirección en el orden equivocado: el offset lo
  fija el tamaño de bloque y va primero
- Confundir latencia con productividad al evaluar segmentación
- Olvidar los ciclos de parada por riesgos, o aplicar adelantamiento
  donde el enunciado no lo permite
- Extensión de signo omitida en cargas de media palabra o byte
- En protocolos, confundir lo que cambia salto a salto con lo que no

## Aplicable a

Ensamblador y ruta de datos, jerarquía de memoria, segmentación,
autómatas y máquinas de estados, intercambios de protocolo,
planificación de procesos, y en general cualquier problema cuya
solución sea una secuencia de estados discretos.

---

## PROMPT LISTO

```
Traza esto paso a paso en forma de tabla de estados, no en prosa.

[CÓDIGO / SECUENCIA DE ACCESOS / INTERCAMBIO / ENUNCIADO]

1. Antes de empezar, explicita el modelo que estás asumiendo (etapas,
   adelantamiento, política de reemplazo y escritura, orden de bytes,
   tamaño de palabra...). Si el enunciado no lo fija, dilo y elige.
2. Tabla: una fila por paso, una columna por elemento de estado.
   Marca paradas, vaciados y fallos con su causa.
3. Verifica ejecutando un simulador en Python y enséñame la salida.
4. Contrasta el total con un razonamiento agregado independiente
   (fallos obligatorios, cota de ciclos, límite teórico).
```

```
Esta es mi traza: [TU TABLA]
Dime SOLO el primer paso donde diverge de la correcta, y por qué.
No me des la traza completa: desde ahí la rehago yo.
```
