# Quantum Approximate Optimization Algorithm {.unnumbered}

Quantum Approximate Optimization Algorithm (QAOA) inherits directly from the concept of annealing and gradually approaching the ground state of our target Hamiltonian. It also can be seen as a particular case of VQE where the ansatz is already defined by Quantum Annealing. If we carefully analyze the composition of digitized version of the annealing algorithm we can identify three main blocks.

<figure markdown>
![Digitized Quantum Annealing](../../assets/digitized-qa.png)
</figure>

The initial and final Hamiltonian blocks ($H_i$ and $H_f$) are the ones that get propagated according to the trotterization. 

But we could probably come up with a better selection of parameters that minimizes the length of this evolution. If we take a large $n$ in our Suzuki-Trotter approximation we could move beyond the coherent threshold of a machine and setting static time-lapses for the whole evolution might not be the best approach to approximate the target evolution (which we do not fully know). One crucial point researchers focus on is generating the shallowest version of this evolution as the shorter it gets less error gets accumulated. We refer as the **depth** of the circuit to the maximal length it reaches considering every set of gates that can be executed within the same execution cycle as the unit depth.

If we could enter some placeholders and check how the circuit behaves for a different set of parameters we could maybe find a better solution than the canonical set of equally spaced steps.

$$
|\gamma, \beta\rangle = U(H_B,\beta_p)U(H_C, \gamma_p) \dots U(H_B,\beta_1)U(H_C, \gamma_1)|s\rangle
$$

where $|s\rangle$ is our starting state and $U(H_m, \theta_m) = e^{-i\theta_mH_m}$ is the unitary transformation parameterized for each step for a total of $p$ steps.

We could setup a free-form circuit so that we could change the values for those rotation angles according to a different criteria than the one used before.

```py
from qiskit import QuantumCircuit

init_state = QuantumCircuit(3)
for qi in init_state.qubits:
    init_state.h(qi)

# Initialization
layers = 1
qc = QuantumCircuit(3)

# Init state
qc = qc.compose(init_state)

# Trotter steps
for layer_idx in range(layers):
    # Init hamiltonian
    qc = qc.compose(Hi(layer_idx))

    # Final hamiltonian
    qc = qc.compose(Hf(layer_idx))

qc.draw('mpl', fold = 150)
```
<figure markdown>
![QAOA](../../assets/qaoa.png)
</figure>

So we only require to select the number of steps (also called layers when talking about QAOA) in order to produce our template circuit. Then it comes the time to select the values that should replace placeholder parameters $\gamma$ and $\beta$.

The existence of both Hamiltonians is crucial to the well functioning of the problem as if we did not have a initial Hamiltonian, our selection of parameters could make as fall into a higher energy level eigenstate ($|\lambda_1\rangle$) and by continuously applying our unitary associated to the target Hamiltonian we would get the same result being stuck in the same quantum state forever ($H|\psi_{\lambda_1}\rangle = E_{\lambda_1}|\psi_{\lambda_1}\rangle$). That is how our initial hamiltonian throughout the whole evolution allows us to scape those local minima looking for the actual ground truth.