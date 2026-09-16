# Recetas de verificación

Código por materia para comprobar un resultado por vía independiente.
Todas las recetas han sido ejecutadas; la salida mostrada es la real.

**Entorno:** Python 3.12 con `numpy`, `scipy`, `sympy`, `matplotlib`,
`pandas`. No hay `numpy_financial` ni `control`: las alternativas
están en las recetas 6 y 12.

---

## 1 · Probabilidad — Monte Carlo

El método general: simular el experimento y contar. Si la simulación y
el cálculo analítico no coinciden, uno de los dos está mal.

```python
import numpy as np
rng = np.random.default_rng(0)

# P(X+Y > 1) con X,Y ~ U(0,1)
x, y = rng.random(10**6), rng.random(10**6)
print(np.mean(x + y > 1))        # 0.5005   (teórico 0.5)
```

Con 10⁶ muestras el error típico es del orden de 10⁻³. Una discrepancia
en el tercer decimal no significa nada; en el segundo, sí.

## 2 · Probabilidad — densidades y momentos (simbólico)

```python
import sympy as sp
t = sp.symbols('t', positive=True)
f = 3*sp.exp(-3*t)

sp.integrate(f, (t, 0, sp.oo))      # 1      → es densidad válida
sp.integrate(t*f, (t, 0, sp.oo))    # 1/3    → E[T]
```

Comprobar que la densidad integra 1 antes que nada. Si no integra 1, el
resto del problema está construido sobre arena.

## 3 · Sistemas Lineales — convolución

```python
import numpy as np
dt = 1e-3
t  = np.arange(0, 5, dt)
x  = np.exp(-t) * (t >= 0)
h  = (t >= 0).astype(float)

y_num = np.convolve(x, h)[:len(t)] * dt      # ← el *dt es obligatorio
y_teo = 1 - np.exp(-t)
print(np.max(np.abs(y_num - y_teo)))         # 1.00e-03
```

El error residual es del orden de `dt`: es discretización, no un fallo.
Si el error es del orden del propio resultado, hay un error real.

**Olvidar el `* dt`** es el fallo más común al verificar: `np.convolve`
hace la suma discreta, no la integral.

## 4 · Sistemas Lineales — Laplace simbólica

```python
import sympy as sp
s = sp.symbols('s')
t = sp.symbols('t', positive=True)

F = sp.laplace_transform(sp.exp(-2*t)*sp.sin(3*t), t, s, noconds=True)
print(sp.simplify(F))                      # 3/((s + 2)**2 + 9)
print(sp.inverse_laplace_transform(F, s, t))   # exp(-2*t)*sin(3*t)
```

Ida y vuelta: si la inversa no devuelve la señal original, hay un error
en el camino. Vale igual para Fourier (`fourier_transform`) y para la
Z (vía series).

## 5 · Circuitos — análisis nodal

```python
import numpy as np
R1, R2, R3, Vs = 1e3, 2.2e3, 3.3e3, 10.0

G = np.array([[1/R1 + 1/R2, -1/R2],
              [-1/R2,        1/R2 + 1/R3]])
I = np.array([Vs/R1, 0.0])
V = np.linalg.solve(G, I)
print(V)                    # [8.4615  5.0769]

# contraste independiente: divisor resistivo
print(Vs * R3 / (R1 + R2 + R3))     # 5.0769
```

La matriz de conductancias es simétrica y su diagonal es la suma de
conductancias que llegan a cada nodo. Si no sale simétrica, el
planteamiento está mal antes de resolver.

## 6 · Circuitos — respuesta en frecuencia y Bode

Sin `control`, `scipy.signal` cubre todo lo necesario:

```python
import numpy as np
from scipy import signal

num, den = [1], [1/(2*np.pi*1e3), 1]        # polo simple en 1 kHz
w, mag, phase = signal.bode((num, den),
                            w=2*np.pi*np.array([100, 1e3, 1e4]))
#   100 Hz   -0.04 dB    -5.71°
#  1000 Hz   -3.01 dB   -45.00°
# 10000 Hz  -20.04 dB   -84.29°
```

Los tres puntos de control de un polo simple: −3 dB y −45° en la
frecuencia de corte, −20 dB por década por encima. Si el trazado
asintótico no cumple eso, está mal.

## 7 · Arquitectura — campos de dirección de caché

```python
def campos(bits_dir, bytes_bloque, n_conjuntos):
    off = (bytes_bloque - 1).bit_length()
    idx = (n_conjuntos - 1).bit_length()
    return dict(offset=off, indice=idx, tag=bits_dir - off - idx)

print(campos(32, 32, 128))   # {'offset': 5, 'indice': 7, 'tag': 20}
```

El orden importa: primero el offset (lo fija el tamaño de bloque),
después el índice (lo fija el número de **conjuntos**, no de líneas), y
el tag es lo que sobra. Invertir ese orden es el error estructural de
la asignatura.

## 8 · Arquitectura — simulación de aciertos y fallos

```python
def simular(accesos, bytes_bloque, n_conjuntos, asociatividad):
    off = (bytes_bloque - 1).bit_length()
    idx = (n_conjuntos - 1).bit_length()
    conj = [[] for _ in range(n_conjuntos)]
    aciertos = fallos = 0
    for a in accesos:
        i   = (a >> off) & (n_conjuntos - 1)
        tag = a >> (off + idx)
        if tag in conj[i]:
            aciertos += 1
            conj[i].remove(tag); conj[i].append(tag)      # LRU
        else:
            fallos += 1
            if len(conj[i]) == asociatividad: conj[i].pop(0)
            conj[i].append(tag)
    return aciertos, fallos

accesos = [i*4 for i in range(64)] * 2
print(simular(accesos, 32, 8, 2))        # (120, 8)
```

Contraste a mano: 64 accesos de 4 en 4 cubren 256 B = 8 bloques de
32 B. Primera pasada, 8 fallos obligatorios y 56 aciertos; segunda
pasada, los 8 bloques caben en la caché, luego 64 aciertos.
56 + 64 = 120. Coincide.

## 9 · Redes — direccionamiento y subredes

Solo biblioteca estándar:

```python
import ipaddress
red = ipaddress.ip_network('192.168.10.0/26', strict=False)

red.network_address      # 192.168.10.0
red.broadcast_address    # 192.168.10.63
red.num_addresses - 2    # 62 hosts útiles
list(red.hosts())[0], list(red.hosts())[-1]   # .1 y .62
```

Para comprobar si una IP cae en una subred:
`ipaddress.ip_address('192.168.10.70') in red` → `False`.

## 10 · Comunicaciones — BER simulada

```python
import numpy as np
from scipy import stats
rng = np.random.default_rng(0)

for dB in [0, 4, 8]:
    e = 10**(dB/10)
    b = rng.integers(0, 2, 200_000)
    s = 2*b - 1                                   # BPSK
    r = s + rng.normal(0, np.sqrt(1/(2*e)), b.size)
    sim = np.mean((r > 0).astype(int) != b)
    teo = stats.norm.sf(np.sqrt(2*e))             # Q(sqrt(2 Eb/N0))
    print(dB, round(teo,5), round(sim,5))

# 0  0.07865  0.07885
# 4  0.01250  0.01260
# 8  0.00019  0.00016
```

`stats.norm.sf` **es** la función Q. La varianza del ruido es
`N0/2 = 1/(2·Eb/N0)` con energía de símbolo unidad: si al comparar sale
un desfase constante en dB, casi siempre es este convenio y no un error
en la derivación.

Para BER bajas hacen falta más muestras: con 2·10⁵ símbolos, una BER de
10⁻⁴ se estima con muy pocos errores y la dispersión es grande.

## 11 · Variable compleja — residuos contra cuadratura

```python
import sympy as sp, numpy as np
from scipy import integrate

z  = sp.symbols('z')
fz = 1/(z**2 + 1)**2
I_res = sp.simplify(2*sp.pi*sp.I * sp.residue(fz, z, sp.I))
print(I_res, float(I_res))          # pi/2   1.570796

I_num = integrate.quad(lambda u: 1/(u**2+1)**2, -np.inf, np.inf)[0]
print(I_num)                        # 1.570796
```

Esta es la verificación más útil de Ampliación: la cuadratura no sabe
nada de contornos, así que si coincide con el cálculo por residuos, el
contorno y los polos encerrados eran los correctos.

## 12 · Finanzas — VAN y TIR

Sin `numpy_financial`:

```python
from scipy.optimize import brentq

flujos = [-1000, 300, 400, 500, 200]
van = lambda r: sum(f/(1+r)**k for k, f in enumerate(flujos))

print(van(0.08))                     # 164.64
print(brentq(van, 1e-6, 1))          # 0.153221  → TIR 15.32 %
```

`brentq` necesita un intervalo donde el VAN cambie de signo. Si no lo
encuentra, o no hay TIR real o hay varias (flujos con más de un cambio
de signo).

---

## Al usar estas recetas

- **Enseñar siempre la salida literal.** Una verificación sin salida
  visible no es una verificación.
- **Atribuir bien las discrepancias.** Antes de declarar incorrecto el
  desarrollo del estudiante, descartar muestreo insuficiente,
  normalización y convenio distinto.
- **Comprobar la comprobación.** Si el resultado numérico es
  sospechosamente redondo o sospechosamente distinto, revisar primero
  el propio código.
