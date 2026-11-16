# Complejidad {.unnumbered}

La complejidad algorítmica en computación cuántica estudia los recursos necesarios para resolver problemas usando ordenadores cuánticos. A diferencia de la computación clásica, donde nos enfocamos en pasos temporales, en cómputo cuántico consideramos el número de qubits, la profundidad del circuito y la complejidad de las puertas.

## Clasificación de problemas

Los problemas se clasifican según su complejidad computacional:

- **P**: Problemas que pueden resolverse en tiempo polinomial en computación clásica.
- **NP**: Problemas cuya solución puede verificarse en tiempo polinomial, pero cuya resolución podría requerir tiempo exponencial.
- **BQP**: Bounded-error Quantum Polynomial time, problemas que pueden resolverse en tiempo polinomial con un ordenador cuántico con error bounded.

## Ventaja cuántica

La ventaja cuántica se logra cuando un problema puede resolverse en un ordenador cuántico de manera más eficiente (en tiempo o recursos) que en uno clásico. Ejemplos destacados incluyen:

- Factorización de enteros (algoritmo de Shor)
- Búsqueda no estructurada (algoritmo de Grover)
- Simulación de sistemas cuánticos

## Complejidad de circuito

La complejidad de un circuito cuántico se mide típicamente por:

1. **Número de qubits** (tamaño del registro)
2. **Profundidad del circuito** (longitud crítica de dependencias)
3. **Cuenta de puertas** (número total de operaciones)

Estos recursos determinan la viabilidad práctica en hardware real.