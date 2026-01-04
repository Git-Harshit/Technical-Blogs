# Engineering Mathematics

## Discrete Mathematics

Propositional logic, also known as sentential logic, deals with propositions, which can either be true or false.

Logical Connectives are used to form complex propositions from simpler ones, such as:
- AND ($\land$): Conjunction
- OR ($\lor$): Disjunction
- NOT ($\lnot$): Negation
- Implies ($\rightarrow, \implies$): Implication

First-order logic (FOL), also known as predicate logic, extends propositional logic by incorporating quantifiers and predicates, allowing for more expressiveness
- Predicates: Descibe properties of objects.
- Quantifiers:
    - Universal Quantifier ($\forall$): Indicates that a predicate holds for all elements in a domain.
    - Existential Quantifier ($\exists$): Indicates that there exists at least one element in a domain for which the predicate holds.

Higher-order logic (HOL) is an extension of First-order logic (FOL) that lets quanitifaction over predicates and functions too other than individual variables.

### Sets

Set is a well-defined collection of distinct/unique elements.

* Types of sets: Finite, Infinite, Empty (Null Set), Subset, Superset, Universal Set.

* Operations on Sets: 
    - Union: $A \cup B = \{x|x \in A$ or $x \in B\}$
    - Intersection: $A \cap B = \{x|x \in A$ and $x \in B\}$ 
    - Difference (also called Relative Complement): $A-B = \{x|x \in A$ and $x \notin B\}$
    - Symmetric Difference: $A \Delta B = \{x|x \in A \cup B$ and $x \notin A \cap B\}$
    - Complement (with respect to universal set).

Power set of A is the set (collection) of all of the subsets of a given set A.

## Linear Algebra

### Matrices

Matrices are two-dimensional collection of elements with $m$ rows and $n$ columns, referred to as a $m \times n$ matrix.

$$A = \begin{bmatrix}
        a_{11} & a_{12} & \cdots \\
        a_{21} & a_{22} & \cdots \\
        \vdots & \ddots & \vdots \\
        a_{n1} & a_{n2} & \cdots
        \end{bmatrix}$$

#### Matrix Operations:

1. Addition - Element-wise (corresponding elements in the two matrices must be added to form the resulting Matrix)
2. Subtraction - Element-wise
3. Multiplication - Row-to-Column (due to this, $m \times n$ order matrix can be multiplied with $n \times o$ order matrix to obtain the resulting matrix of the order $m \times o$).

A real square matrix (i.e., with real number elements) is said to be:
- Symmetric if $A^T=A$, i.e., $a_{ij} = a_{ji}$
- Skew-Symmetric if $A^T=-A$, i.e., $a_{ij} = -a_{ji}$
- Orthogonal if $A^T=A^{-1}$.

Determinant of Orthogonal Matrix is always $\pm1$.
$1 = |A\cdot A^{-1}| = |A||A^T| = |A||A| = |A|^2$ Therefore, $|A|=\pm1$

### Determinant

Determinant is a scalar value, unlike a Matrix which is a dimensional collection.

$$det(A) = |A| = \begin{vmatrix}
                a_{11} & a_{12} & \cdots \\
                a_{21} & a_{22} & \cdots \\
                \vdots & \ddots & \vdots \\
                a_{n1} & a_{n2} & \cdots
                \end{vmatrix}$$

Value of a 2 $\times$ 2 matrix is found by the difference of cross-multiples as shown:

$\begin{vmatrix}a_{11} & a_{12} \\ a_{21} & a_{22}\end{vmatrix} = a_{11}a_{22}-a_{12}a_{21}$

## Differential

A Differential Equation (DE) is an equation involving (connecting) an unknown (or sought-for) function y of one or more independent variables and its derivatives.

Order - Order of a DE is the order of the highest derivative appearing in the equation.

Degree - Degree of the highest ordered derivative (without any radicals and fractions with the derivative terms) is the Degree of a DE.

### Ordinary Differential Equation (ODE)

Generally expressed as:

$F(x, y, y', y'', ..., y^n) = 0$

where $y' = dy/dx = \delta{y}/\delta{x} = \Delta{y}/\Delta{x}$

In an Ordinary Differential Equation, the dependent variable y only depends on one independent variable (so that the derivatives of y are ordinary derivatives).

### Partial Differential Equation (PDE)

In Partial Differentiation, the derivative of a function of multiple variables with respect to one of those variables is performed while considering the other variables as constants. It is represented by $\partial$, read as 'del'.

It is generally expressed as:

$F(x, t, y, \frac{\partial{y}}{\partial{x}}, \frac{\partial{y}}{\partial{t}}, \frac{\partial^2{y}}{\partial{x^2}}, \frac{\partial^2{y}}{\partial{x}\partial{t}}, \frac{\partial^2{y}}{\partial{t^2}}, \cdots)$

## Probability and Statistics

Probability is the likeliness of occurrence of an event. It quantifies certainity, is denoted by $P(E) \in [0, 1]$.

Impossible Event has its Probability = 0, and a Sure Event has its Probability = 1.

* Independent Events: Occurrence of one event does not affect the probability of another. $P(A \cap B) = P(A) \cdot P(B)$

* Mutually Exclusive Events: Two events are mutually exclusive if they cannot occur at the same time. If one event occurs, the other cannot. $P(A \cap B) = 0$

$P(A \cup B) = P(A) + P(B) - P(A \cap B)$

Conditional Probability

$P(A|B) = \frac{P(A \cap B)}{P(B)}$

[Bayes' Theorem](https://en.wikipedia.org/wiki/Bayes%27_theorem)

$P(A|B) = \frac{P(B|A).P(A)}{P(B)}$

## References

1. Higher Engineering Mathematics by B. V. Ramana - Tata McGrawHill Publications ([+ Chapter-Wise summary](https://highered.mheducation.com/sites/dl/free/007063419x/392340/Chaperwise_Summary.pdf)).
2. Higher Engineering Mathematics by B. S. Grewal - Khanna Publications.
3. [CoPilot](https://copilot.microsoft.com) query on Propositional Logic and First-order Logic.

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

- Discrete Mathematics: Propositional and first order logic. Sets, relations, functions, partial orders and lattices. Monoids, Groups. Graphs: connectivity, matching, colouring. Combinatorics: counting, recurrence relations, generating functions.
- Linear Algebra: Matrices, determinants, system of linear equations, eigenvalues and eigenvectors, LU decomposition.
- Calculus: Limits, continuity and differentiability, Maxima and minima, Mean value theorem, Integration.
- Probability and Statistics: Random variables, Uniform, normal, exponential, Poisson and binomial distributions. Mean, median, mode and standard deviation. Conditional probability and Bayes theorem.