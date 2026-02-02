Eliminating ε-Transitions from an NFA
Objective

The goal of this work is to eliminate ε (epsilon) transitions from a Non-Deterministic Finite Automaton (NFA) and produce an equivalent NFA without ε-transitions.
This step is required before determinizing an NFA.

Initializing the NFA
States

q0, q1, q2

Alphabet

{a, b}

Start State

q0

Final State

q2

Transitions

q0 —ε→ q1

q1 —a→ q1

q1 —b→ q2

q2 —ε→ q0

Method Used
1. ε-Closure

For each state, its ε-closure is computed.
The ε-closure represents all states reachable using only ε-transitions, including the state itself.

Computed ε-closures:

ε-closure(q0) = {q0, q1}

ε-closure(q1) = {q1}

ε-closure(q2) = {q2, q0, q1}

2. New Transitions

For each state and each input symbol:

Compute the ε-closure of the state

Follow the symbol transitions from all states in the closure

Compute the ε-closure of the reached states

Create a new transition without ε

Example

From state q0:

ε-closure(q0) = {q0, q1}

On symbol a:

q1 —a→ q1

ε-closure(q1) = {q1}
→ (q0, a) → {q1}

On symbol b:

q1 —b→ q2

ε-closure(q2) = {q2, q0, q1}
→ (q0, b) → {q0, q1, q2}

From state q1:

(q1, a) → {q1}

(q1, b) → {q0, q1, q2}

From state q2:

(q2, a) → {q1}

(q2, b) → {q0, q1, q2}

All resulting transitions are free of ε.

3. New Final States

A state is considered final if its ε-closure contains at least one original final state (q2).

ε-closure(q0) ∩ {q2} ≠ ∅ → q0 is final

ε-closure(q1) ∩ {q2} = ∅ → q1 is not final

ε-closure(q2) ∩ {q2} ≠ ∅ → q2 is final

New final states: {q0, q2}

Result

All ε-transitions are removed

The new NFA is equivalent to the original one

The recognized language is preserved

Conclusion

This project demonstrates the elimination of ε-transitions using ε-closures, following automata theory rules.
The resulting NFA is suitable for determinization.
