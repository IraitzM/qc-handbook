# Formulaciones QUBO {.unnumbered}

Hemos visto que los problemas de optimización pueden formularse como QUBO (Quadratic Unconstrained Binary Optimization), pero hay múltiples formas de representar el mismo problema y algunas son más adecuadas para el hardware que otras.

## Formulación directa

La forma más directa de poseer un problema QUBO es:

$$
\min_x x^TQx + k
$$

donde $Q$ es una matriz simétrica de $n \times n$ y $k$ es un escalar. La solución óptima $x^*$ es el vector binario que minimiza la energía del sistema.

## Relación con el modelo Ising

El modelo Ising utiliza spins $s_i = \pm 1$ en lugar de bits $x_i \in \{0, 1\}$. La transformación entre ellos es:

$$
s_i = 2x_i - 1 \quad \text{o} \quad x_i = \frac{s_i + 1}{2}
$$

Sustituyendo en la formulación QUBO obtenemos el modelo Ising:

$$
H = -\sum_{\langle i j \rangle} J_{ij} s_i s_j - \sum_i h_i s_i
$$

donde $J_{ij}$ son los términos de acoplamiento y $h_i$ son los campos transversales.

## Formulaciones comunes

### 1. Ising model (compatibilidad con D-Wave)

La mayoría de los quantum annealers, particularmente los dispositivos D-Wave, nativamente operan con el modelo Ising. Cualquier problema QUBO puede convertirse al modelo Ising mediante la transformación mencionada arriba.

### 2. Formulación para QAOA

Para el Quantum Approximate Optimization Algorithm (QAOA), la formulación QUBO debe especificar tanto el Hamiltoniano de costo $H_C$ como el Hamiltoniano de mezclador $H_M$. El Hamiltoniano de costo codifica la función objetivo mientras que el mezclador Typically es un campo transversal $\sum_i \sigma_x^i$.

### 3. Formulación con restricciones

Los problemas con restricciones duras pueden formularse introduciendo términos de penalización en la función objetivo:

$$
\min_x x^TQx + k + \rho \cdot (\text{violated constraints})^2
$$

donde $\rho$ es un factor de penalización que controla el equilibrio entre minimizar la energía y satisfacer las restricciones.

## Consideraciones de hardware

Al mapear problemas QUBO a hardware real, considerar:

- **Conectividad nativa**: El hardware puede tener conectividad limitada (por ejemplo, cadena lineal, chimera graph, pleno completo virtual).
- **Fuerzas de cadena**: Para problemas all-to-all en hardware con conectividad limitada, pueden necesitarse chains de qubits físicos.
- **Rango de valores**: Los valores de $Q_{ij}$ y $h_i$ deben estar dentro del rango que el hardware puede representar con precisión.