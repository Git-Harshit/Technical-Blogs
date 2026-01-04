# Digital Logic

## Operations

1. NOT ($\lnot, \overline{A}$)
    - Function: Inverts the input.
2. OR (Disjunction, $\cup, +$)
    - Function: True if at least one input is true.
3. AND (Conjunction, $\cap, .$)
    - Function: True if all inputs are true.
4. NOR (Not OR)
    - Function: True if all inputs are false.
5. NAND (Not AND)
    - Function: True if at least one input is false.
7. XOR (Exclusive OR, $\oplus$)
    - Function: True if exactly one input is true.
6. XNOR (Exclusive NOR, $\overline{\oplus}$)
    - Function: True if inputs are equal.

## Properties

1. Commutative Law

    - OR: $A \cup B = B \cup A$
    - AND: $A \cap B = B \cap A$

2. Associative Law

    - OR: $A \cup (B \cup C) = (A \cup B) \cup C$
    - AND: $A \cap (B \cap C) = (A \cap B) \cap C$

3. Distributive Law

    - OR over AND: $A \cup (B \cap C) = (A \cup B) \cap (A \cap C)$
    - AND over OR: $A \cap (B \cup C) = (A \cap B) \cup (A \cup C)$

4. Identity Law

    - OR: $A \cup 0 = A$
    - AND: $A \cap 1 = A$
    - OR: $A \cup 0 = A$
    - AND: $A \cap 1 = A$

5. Null Law

    - OR: $A \cup 1 = 1$
    - AND: $A \cap 0 = 0$

6. Idempotent Law

    - OR: $A \cup A = A$
    - AND: $A \cap A = A$

7. Inverse Law

    - OR: $A \cup \overline{A} = 1$
    - AND: $A \cap \overline{A} = 0$

8. Absorption Law

    - $A \cup (A \cap B) = A$
    - $A \cap (A \cup B) = A$

9. De Morgan's Theorem

    - $\overline{AB} = \overline{A}+\overline{B}$
    - $\overline{A+B} = \overline{A}.\overline{B}$

10. Double Negation Law

    - $\overline{\overline{A}} = A$ <!-- Alternative writing, $\lnot{\lnot{A}} = A$ -->

11. Consensus Theorem

    - $AB + \overline{A}C + BC = AB + \overline{A}C$
    - $(A+B)(\overline{A}+C)(B+C)=(A+B)(\overline{A}+C)$

## Operator Equivalence

1. XOR ($\oplus$)

    - $A \oplus B = \overline{A}B+A\overline{B} = (A+B)(\overline{A}+\overline{B})$

2. Implies ($\implies$)

    - $A \implies B = \overline{A}+B$

3. Biconditional (If and only if, $\iff$)

    - $A \iff B = AB + \overline{A}.\overline{B} = A \overline{\oplus} B$

## Karnaugh Map (K-map)

K-Map or [Karnaugh Map](https://en.wikipedia.org/wiki/Karnaugh_map) is a technique to minimise or directly obtain the simplified boolean expression in either of Sum-Of-Products (SOP) or Product-of-Sums (POS) form. It is created with a grid and involves grouping of 1s (minterm, in case of SOP) or 0s (maxterm, in case of POS) in powers of 2 as in dual (pair of 2), quad (group of 4), octet (group of 8), hexadecad (group of 16) and so on.

<u>Gray Code</u> is a sequence of binary numbers where two consecutive numbers differ in exactly one bit. This property makes Gray Code especially useful in error correction and digital communication.

## Switching Circuits

Digital circuits are also called as switching circuits because the voltage levels in a digital circuit is assumed to be switched instantaneously from a value to another and the transition time is assumed as zero.

Switching Circuits can be divided into two types:

1. Combinational Switching Circuit: Switching circuits whose output levels at any instant of time are dependent only on the level of inputs at that instant. Any prior input level conditions have no effect on the present outputs, as combinational logic circuits have no memory.

2. Sequential Switching Circuit: Switching circuits whose output levels at any instant of time are dependent not only on the levels present at the inputs at that time, but also on the state of the circuit, i.e., the prior input level conditions (or its past inputs). The past history is provided by feedback loop from output back to the input. This means that sequential switching circuits have memory. Sequential switching circuits = Combinational switching circuit + Memory.
    1. Synchronous Sequential Switching Circuit: State transitions can take place only when the inputs are applied along with a clock pulse. Such a circuit will be active only when clock signal is present.
    2. Asynchronous Sequential Switching Circuit: State transitions can take place any time the inputs are applied, irrespective of clock. These are not controlled by a clock.

### Flip-Flops and Latches

A Flip-Flop, known formally as a bistable multivibrator, also called a binary or one-bit memory, has two stable states. It can remain in either of the states indefinitely and its state can be changed by applying the triggering signal.

Latch refers to non-clocked flip-flops, because these flip-flops may 'latch' on to a 0 or 1 immediately upon receiving the input pulse called as Set or Reset. Gated Latch contains an Enable or gating signal, and they respond to the inputs only when they are enabled with the input Enable with a High gating signal.

## Recommendations:

1. [Fundamentals of Digital Circuits by Prof. A. Anand Kumar, Prentice Hall PHI Learning - Amazon](https://www.amazon.in/Fundamentals-Digital-Circuits-Kumar-Anand/dp/8120352688)

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

Boolean algebra. Combinational and sequential circuits. Minimization. Number representations and computer arithmetic (fixed and floating point).