# Otras consideraciones {.unnumbered}

Al trabajar con algoritmos cuánticos en hardware real, hay varias consideraciones prácticas que van más allá de la formulación teórica del problema.

## Limitaciones de hardware

### Conectividad del dispositivo

No todos los dispositivos cuánticos tienen conectividad all-to-all. La mayoría tienen topologías limitadas como:

- **Cadena lineal**: Qubits dispuestos en una línea, solo conexiones entre vecinos.
- **Matriz cuadrada**: Conectividad en forma de rejilla.
- **Topología de chip específico**: Cada fabricante tiene su arquitectura única.

Si su problema requiere conexiones que no están disponibles nativamente, deberá usar puertas SWAP u otras técnicas de transpilación.

### Puertas nativas

Cada dispositivo tiene un conjunto de puertas nativas que pueden ejecutarse directamente. Las puertas lógicas deben decomponerse en estas puertas nativas. Por ejemplo:

- Dispositivos superconducting: típicamente $X$, $Z$, $ZX$, $CNOT$ como puerta de dos qubits.
- Trampas de iones: puertas basadas en láser con configuraciones específicas.
- Átomos neutrales: operaciones basadas en Rydberg.

### Ruido y decoherencia

El hardware cuántico real está sujeto a ruido que afecta la fidelidad de las operaciones. Las consideraciones incluyen:

- **Tiempos de coherencia ($T_1$, $T_2$)**: Limitan la profundidad máxima del circuito.
- **Tasas de error de puerta**: Afectan la probabilidad de obtener el resultado correcto.
- **Error de readout**: Sesgo en la medición de los resultados.

## Estrategias de mitigación

### Error suppression

Techniques like dynamical decoupling, DRAG, y otras buscan reducir el impacto del ruido sin modificar el circuito lógico.

### Error mitigation

Techniques como zero-noise extrapolation (ZNE), readout mitigation, y probabilistic error cancellation (PEC) buscan reducir el efecto del ruido en los resultados después de la ejecución.

### Optimización de circuitos

- Reducir la cuenta de puertas de dos qubits (el mayor contribuyente al error).
- Optimizar el layout y routing para minimizar SWAP gates.
- Usar compiladores vendor-agnostic como pytket o BQSKit.

## Limitaciones algorítmicas

Algunos algoritmos cuánticos tienen requisitos específicos:

- **VQE**: Requiere un buen ansatz y optimizador clásico.
- **QAOA**: La elección de parámetros y el número de capas afectan el rendimiento.
- **Simulación de tiempo**: La trotterización introduce errores que deben controlarse.

Estas consideraciones prácticas a menudo determinan más el éxito de un experimento que la teoría subyacente del algoritmo.