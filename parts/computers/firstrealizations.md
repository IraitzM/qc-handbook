# First realizations {.unnumbered}

Motivated by Shor's algorithm [@shor1994algorithms], during late 90s there was quite some motivation to provide a physical realization of what up to that moment was mostly theoretical work.

Any two-level physical system could be a good candidate for a qubit but we need to a find a physical realization that allows for operation and performing the set of tasks we could consider an algorithm.

In 1998, using nuclear magnetic resonance (NMR) both Oxford University and Stanford achieved the first implementations of two qubit algorithms [@chuang1998experimental]. More or less in the same period, Yasunobu Nakamura and Jaw-Shen Tsai demonstrated how a superconducting chip can be used as a qubit by controlling the current through it [@nakamura2001rabi].

2007 is known to be a key date as the first **transmon** was born. It is the equivalent of the transistor in the quantum regime [@koch2007charge]. So first qubits exist since early 2000 which is not much but from manufacturing a qubit to building a whole computer... that is a long road.

Many metrics will be used to compare different devices and realizations in following sections so better get them clear now.

**T1 time**

Also known as the **relaxation time**, identifies how much time it would take a qubit to transition from an excited state ($|1\rangle$) to its ground state ($|0\rangle$). T1 time is not an actual time from state to state but rather identifies the time in which a state might transition and flips states once exited ($P(|1\rangle) = e^{-\frac{t}{T1}}$).

**T2 time**

Known as the **phase coherence** time. Basically quantifies the time in which the phase associated to a state is stable.

$$
|+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}} \quad \xrightarrow[T2]{} \quad |-\rangle = \frac{|0\rangle -|1\rangle}{\sqrt{2}}
$$

These two time-metrics characterize our qubits **coherence time**, the time in which our qubits are actually qubits and not classical bits playing tricks on us.

Another measure we will often refer to is the **fidelity**. Basically it measures the gap between theoretical state and physical outcome as a qubit quality metric. Fidelity attends to the more general state of closeness between two quantum states but in this following sections it will provide a measure to understand how well each operation renders the expected result.

$$
F(\rho, \sigma) = |\langle \psi | \phi \rangle | ^2
$$

::: {.callout-warning}
## NOTE 

This is the case just when considering both states to be pure
:::

## Building the thing

There is more than one type of quantum computer. Actually we yet don't know the one that will win the podium, but the race is interesting at this point. The physical realization conditions many aspects of the whole machine so it is relevant to understand a bit of their inner workings so that we can select the most appropriate option.

There is one general definition of how a quantum computer may look like and it is given by the **DiVincenzo criteria** [@divincenzo1997topics].

* Must be scalable and well characterized qubits.
* System may be able to be initialized ($|00...\rangle$ state is the common choice)
* Qubit coherence time must be much larger than the actuation time
* Enable a universal set of gates/operations
* Capable of measuring from specific qubits

With this recipe many platforms have been proposed using different physical realizations for the technology.