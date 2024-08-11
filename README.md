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

En este Readme vamos a explicar lo que hace el código y cómo se ejecuta este:
Este es un script de Python que minimiza un autómata finito determinista (DFA) al encontrar estados equivalentes. En este README vamos a hacer un desglose de lo que hace el código y cómo se ejecuta este:

### read_input() function:

1.	Lee la entrada estándar (generalmente la consola) línea por línea.

2.	Almacena las líneas de entrada en una lista de líneas.

3.	Se espera que la entrada sea en un formato específico:

3.1.	La primera línea contiene un entero c, que representa el número de casos de prueba.

3.2.	Cada caso de prueba consiste en:

•	Un número entero *n*, que representa el número de estados en el DFA.

•	Una línea que contiene el alfabeto (una lista de símbolos separados por espacios).

•	Una línea que contiene los estados finales (una lista de enteros separados por espacios).

•	*n* líneas, cada una de las cuales contiene una transición (una lista de enteros separados por espacios).

La función devuelve una lista de duplas, donde cada dupla representa un caso de prueba y contiene *n, alphabet, final_states y transitions*.

### minimize_dfa() function:

1.	Toma cuatro argumentos: *n, alphabet, final_states y transitions*, que representan un DFA.

2.	La función minimiza el DFA al encontrar estados equivalentes utilizando los siguientes pasos:

3.	Marca pares de estados donde uno es definitivo y el otro no.

4.	Marca iterativamente los pares de estados en función de sus transiciones.

5.	Recoge los pares de estados equivalentes.

6.	La función devuelve una lista de pares de estados equivalentes.

### main() function:

1.	Llama a  read_input() para leer la entrada y almacenarla en los casos.
2.	Itera sobre cada caso de prueba en los casos y llama a minimize_dfa() para minimizar el DFA.
3.	Almacena los resultados en una lista  results.
4.	Imprime cada resultado, que es una cadena que representa los pares equivalentes de estados.

### Bloque if __name__ == "__main__"::
 Este bloque asegura que main() se ejecute solo cuando el script se ejecuta directamente, y no cuando se importa como módulo.

## EJECUCIÓN :

1.	Guarde el código en un archivo, por ejemplo, dfa_minimizer.py.
2.	Ejecuta el script desde la línea de comandos: python dfa_minimizer.py
3.	Cuando se ejecuta este script el programa espera a que el usuario ingrese datos describiendo uno o más DFA y tras procesar la entrada, imprime las parejas de estados que son equivalentes según el proceso de minimización del DFA, por ejemplo:

```
2
3
a b
1 2
0 1
1 2
0 0
1 1
4
a b
2 3
0 1 2 3
1 2 3 0
2 3 0 1
3 0 1 2

```
Esta entrada representa dos casos de prueba. El primer caso de prueba tiene 3 estados, alfabeto {a, b}, estados finales {1, 2} y sus transiciones.
El segundo caso de prueba tiene 4 estados, alfabeto {a, b}, estados finales {2,3} y sus transiciones.
El script mostrará los pares de estados equivalentes para cada caso de prueba, que en este caso serían:
```
(0,2) (0,1}
(0,1) (2,3)

```
Esta salida indica que los estados 0,2  y 0,1 son equivalentes, en el primer caso de prueba. Del mismo modo, la salida del segundo caso de prueba indicaría que los estados 0,1 son equivalentes, al igual que los estados 2 ,3, lo que significa que podrían ser combinados en el DFA minimizado.


