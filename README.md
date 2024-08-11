Esta es la implementación dada a la Asignación 1 del curso de Lenguajes Formales y Compiladores por parte de los alumnos Samuel Acosta Aristizabal y Katherin Nathalia Allin Murillo.

A continuación podemos ver el contenido de la asignación y sus referencias

# Formal Languages and Compilers
#### Assignment 1

This repository contains the first assignment for the Formal Languages and Compilers course. The assignment focuses on deterministic finite automata (DFA)
<br>

## Preliminaries
For this assignment some definitions and notions are required. Let M = (Q,Σ,δ,s,F) be a deter-
ministic finite automaton (DFA).

1. **Inaccessible states.** A state q ∈ Q is said to be **inaccessible** if there is no string x ∈ Σ∗ such that ˆδ(s, x) = q
   
2. **Equivalent states.** A pair of states p,q ∈ Q is said to be equivalent if and only if (∀x ∈ Σ∗)(ˆδ(p, x) ∈ F ≡ ˆδ(q, x) ∈ F).
   That is, any string x that from p allows us to access a final state, must also allows us to reach a final state from q, and vice versa.
   
3. We say that two states can be **collapsed** if they are equivalent.

## Assignment

The assignment is to implement, in any programming language, the minimization algorithm pre-
sented in Kozen 1997, Lecture 14.

Given a DFA with no inaccessible states, the algorithm returns the states that are equivalent.
Therefore, such states can be collapsed and we shall obtain a minimized automaton.
The minimization algorithm in Lecture 14 is based on the construction given in Lecture 13. It is
not necessary to read Lecture 13 to implement the algorithm, but if you choose to read it, you can
gain a high level understanding of the minimization procedure.

## Input/output

Your program should fulfill the following specifications.

#### Input
A case is a DFA M with no inaccessible states.
You may assume states are denoted by natural numbers and the initial state (s) is always the
number 0 (zero). Alphabets are formed with letters of the latin alphabet (with 26 letters). In ASCII
code, characters from 97 to 122.
The input of the program is as follows.
1. A line with a number c > 0 indicating how many cases you will receive.
2. For each case, in a single line a number n > 0 denoting of states of M.
3. Then, a single line with the alphabet of M. Symbols are separated by blank spaces.
4. Then, the final states of M separated by blank spaces.
5. Finally, n lines, one for each state. Each line contains a row of the table that represents M.
Assume that the symbols of the alphabet appear in the table in the same order as they were
given in step 3. For instance, if the automaton is

<div align="center">
  
![image](https://github.com/user-attachments/assets/d64cab34-a4bb-4f7f-8323-d5da4c0d29ca)

</div>

#### Output

For each case, print the pairs of states that are equivalent in lexicographical order. All the pairs in a
single line separated by blank spaces.

## References
Kozen, Dexter C. (1997). Automata and Computability. 1st. Berlin, Heidelberg: Springer-Verlag.
ISBN: 0387949070. DOI: https://doi.org/10.1007/978-1-4612-1844-9.

En este Readme vamos a hacer un desglose de lo que hace el código y cómo se ejecuta este:
