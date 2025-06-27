# Other considerations {.unnumbered}

most of what we saw relates to binary optimization but there are two things we may need or want to work on as well:

* Non-binary variables
* Beyond quadratic models

## Non-binary variables

Many problems require continuous variables so in order to be solvable by quantum computers, or at least Quantum Annealers, we might need to transform that numerical precision into bins.

So, if we take the example of the portfolio optimization problem, assuming a percentage of the available money goes to different assets (not just binary decisions if we invest or not) we will need to reformulate it, so imaging that instead of

$$
\max \sum_i r_ix_i - \sum_i \sum_j c_{ij}x_ix_j \\
\text{ s. t. } \sum_i b_ix_i \le B
$$
where $x_i \in \{0, 1\}$, you need to define a variable $w_i \in \mathbb{R}$. In order for that to work on a quantum computer, you will need to define your problem so that

$$
w_i = \sum_{p=0}^{K} \frac{1}{2^p} x_{i,p}
$$
so that $w_i$ is the linear combination of weights $\{\frac{1}{2^0}, \frac{1}{2^1}, \frac{1}{2^2}, \dots, \frac{1}{2^p} \}$. We will need to define the precision we would like and that also affects the number of qubits required to solve our problem. If the binary case required one qubit per asset, now we need $p$ qubits per asset, which might be challenging for large problems.

## Beyond QUBO

The limitation to quadratic terms might not be suitable for all soft of problems. We may want to extend our problem so that for example, covers a three-parti relationship

$$
\max \sum_i a_ix_i - \sum_i \sum_j b_{ij}x_i, x_j + \sum_i \sum_j \sum_k c_{ijk}x_ix_jx_k.
$$

That extra three-party relation adds a whole new level of complexity as it requires either a three party gate (like de Toffoli gate) in systems that do not go beyond two-qubit gates. So we will need to decompose this interaction into several new two body terms, exploding the resources required. This are defined as [Higher-Order Unconstainer Binary Optimization (HUBO) problems](https://docs.dwavequantum.com/en/latest/quantum_research/reformulating.html#non-quadratic-higher-degree-polynomials).