# Primeras realizaciones {.unnumbered}

Motivado por el algoritmo de Shor [@shor1994algorithms], durante los años 90 hubo mucha motivación para proporcionar una realización física de lo que hasta ese momento era trabajo mayormente teórico.

Cualquier sistema físico de dos niveles podría ser un buen candidato para un qubit, pero necesitamos encontrar una realización que permita la operación y la realización de las tareas que podríamos considerar un algoritmo.

En 1998, usando resonancia magnética nuclear (NMR) tanto la Universidad de Oxford como Stanford lograron las primeras implementaciones de algoritmos de dos qubits [@chuang1998experimental]. Más o menos en el mismo período, Yasunobu Nakamura y Jaw-Shen Tsai demostraron cómo un chip superconducting puede usarse como un qubit controlando la corriente a través de él [@nakamura2001rabi].

2007 es conocido como la fecha clave en la que nació el primer **transmon**. Es el equivalente del transistor en el régimen cuántico [@koch2007charge]. Así que los primeros qubits han existido desde principios de los 2000, lo cual no es mucho, pero desde la fabricación de un qubit hasta construir un ordenador completo... ese es un largo camino.

Múltiples métricas se usarán para comparar diferentes dispositivos y realizaciones en las secciones siguientes, así que mejor tenerlas claras ahora.

**Tiempo T1**

También conocido como **tiempo de relajación**, identifica cuánto tiempo tardaría un qubit en transitar desde un estado excitado ($|1\rangle$) a su estado fundamental ($|0\rangle$). El tiempo T1 no es un tiempo real de estado a estado, sino que identifica el tiempo en que un estado podría transitar y cambiar de estado una vez excitado ($P(|1\rangle) = e^{-\frac{t}{T1}}$).

**T2 tiempo**

Conocido como el **tiempo de coherencia de fase**. Básicamente cuantifica el tiempo en que la fase asociada a un estado es estable.

$$
|+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}} \quad \xrightarrow[T2]{} \quad |-\rangle = \frac{|0\rangle -|1\rangle}{\sqrt{2}}
$$

Estos dos métricas de tiempo caracterizan el **tiempo de coherencia** de nuestros qubits, el tiempo en que nuestros qubits son realmente qubits y no bits clásicos jugando trucos.

Otra medida a la que a menudo nos referimos es la **fidelidad**. Basicmente mide la brecha entre el estado teórico y el resultado físico como métrica de calidad de un qubit. La fidelidad se refiere a la más general closeness entre dos estados cuánticos, pero en las secciones siguientes proporcionará una medida para entender qué tan bien cada operación renderiza el resultado esperado.

$$
F(\rho, \sigma) = |\langle \psi | \phi \rangle | ^2
$$

::: {.callout-warning}

## NOTE 

Esto solo ocurre al considerar ambos estados como puros.

:::

## Construyendo la cosa

Hay más de un tipo de ordenador cuántico. Todavía no sabemos cuál ganará el podio, pero la carrera es interesante en este punto. La realización física condiciona muchos aspectos de la máquina completa, por lo que es relevante entender un poco de su funcionamiento interno para poder seleccionar la opción más apropiada.

Hay una definición general de cómo podría verse un ordenador cuántico dado por los **criterios de DiVincenzo** [@divincenzo1997topics].

* Debe tener qubits escalables y bien caracterizados.
* El sistema debe poder inicializarse ($|00...\rangle$ estado la elección común)
* El tiempo de coherencia de los qubits debe ser mucho mayor que el tiempo de actuación
* Permitir un conjunto universal de puertas/operaciones
* Capaz de medir desde qubits específicos

Con esta receta se han propuesto muchas plataformas usando diferentes realizaciones físicas para la tecnología.