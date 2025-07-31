# Quadratic Knapsack Problem (QKP)

The 0-1 quadratic knapsack problem (QKP) consists of maximizing a quadratic objective function subject to a linear constraint, where the variables are binary (0 or 1). It has applications in several areas, such as finance (resource allocation and stock portfolio selection) and independent project selection. Formally:

Maximize:

> **Z** = XᵀQX = ∑∑ qᵢⱼxᵢxⱼ 

Subject to:

> ∑ aᵢxᵢ ≤ b xᵢ ∈ {0, 1} for all i

Where:
- Q = (qᵢⱼ) is an n×n matrix of "profit" coefficients (positive definite)
- a = (aᵢ) is a vector of weights/capacities
- b is the total capacity of the knapsack
- xᵢ indicates whether item i is (1) or not (0) in the knapsack

This problem is classified as NP-Hard, meaning that finding exact solutions for larger instances is computationally infeasible. Given this difficulty, the paper proposes a GRASP (Greedy Randomized Adaptive Search Procedure) heuristic to solve it in its QKP1 formulation, which will not be discussed in this work.

---

## Selected Evolutionary Algorithm

Because this is a problem with binary variables, the Traditional Genetic Algorithm with Binary Encoding can handle the problem well, provided it has a good fitness function. Furthermore, this algorithm can efficiently explore the search space for binary solutions full of local optima, in addition to easily incorporating the capacity constraint.

For the parts of this algorithm, we define:
- **Individual Representation**: binary vector of size n;
- **Fitness Function**: XᵀQX, if aᵀX ≤ b; XᵀQX − λ × max(0, Σ aᵢxᵢ − b), if aᵀX > b
- **Crossover**: Binary Tournament
- **Recombination**: Uniform Crossover
- **Mutation**: Bit-Flip (checking viability)
- **Survival**: (μ + λ)

### Execution
For the genetic algorithm, it is also necessary to define some execution parameters. In this case, the stopping condition is given by the maximum number of generations reached. Furthermore, we also define a number of executions for comparison purposes. Other parameters to define would be:
- **Population Size**: defines the maximum number of individuals (p) that can persist in a population (initially and during survival);
- **Crossover Probability**: defines the chances of reproduction occurring between two individuals in a population (generally high);
- **Mutation Probability**: defines the chances of a mutation occurring in an individual generated in a population (generally low).

---

## Bibliographic References

Nogueira, R. T., Paula Jr., G. G. de, & Póvoa, C. L. R. (2003). UMA HEURÍSTICA GRASP PARA O PROBLEMA DA MOCHILA QUADRÁTICA 0-1. A Pesquisa Operacional e os Recursos Renováveis, XXXVSBPO, Natal-RN, 4 a 7 de novembro de 2003.

