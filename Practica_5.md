# Practica 5 - Complejidad temporal

## 1. Responder y justificar brevemente las siguientes preguntas conceptuales:
### a. ¿Por qué sólo tiene sentido tratar la complejidad temporal dentro de la clase R?
- Recordar que los lenguajes de la clase R son aquellos para los cuales existe una MT M que siempre para, no tendría sentido evaluar el tiempo en MTs que pueden no parar.
### b. Probar que n3 = O(2n).
- Para probar esto, necesitamos una constante C que haga que lo de la izquierda sea menor siempre. Por ejemplo, tomo C = 10, entonces 10^3 = 1000 y 2^10 = 1024.
### c. Probar que si T1(n) = O(T2(n)), entonces TIME(T1(n)) ⊆ TIME(T2(n)).
- Sea L en T1(n), existe una MT M que la resuelve en O(T1(n)) y como T1(n) es igual a O(T2(n)) entonces O(T1(n)) = O(T2(n)). Recordar que un problema pertenece a TIME(T(n)), sí y sólo sí, existe una MT M que lo resuelve en O(T(n)), entonces existe como hay una MT M que resuelve a L en O(T1(n)) y llegamos al hecho de que O(T1(n)) = O(T2(n)), puedo afirmar que ese L pertenece a TIME(T1(n)) y, como su orden es igual al de O(T2(n)), se concluye que TIME(T2(n)) contiene a TIME(T1(n))
### d. Hemos resuelto de dos maneras el problema de los palíndromos, una con una MT con una cinta y otra con una MT con varias cintas. La primera tarda O(n^2) pasos y la segunda O(n). ¿Por qué es indistinta la cantidad de cintas utilizadas, considerando la jerarquía temporal que definimos?
- La MT M de una cinta tarda O(n^2) pasos, mientras que la MT M de varias cintas tarda O(n), considerando la jerarquía temporal, ambas tardan poly(n), por esa razón es que es indistintas para este caso.
### e. Probar que si L está en P, también lo está su complemento L^C.
- Por propiedad, sabemos que si L está en P, su complemento también lo está. Por ejemplo, el caso de CLIQUE', tal que CLIQUE' se define como:
 + CLIQUE' = {G | G es un grafo que no tiene un clique de K vértices}
- El complemento de CLIQUE' se resuelve de manera similar, podría recorrer el grafo buscando si existe un clique de tamaño K fijo, que sería n^K (polinomial). Por lo tanto el complemento de CLIQUE' también pertenece P.
## 2. Sea el lenguaje SMALL-SAT = {φ | φ es una fórmula booleana sin cuantificadores en la forma normal conjuntiva (o FNC), y existe una asignación de valores de verdad que la satisface en la que hay a lo sumo 3 variables con valor de verdad verdadero}. Probar que SMALL-SAT ∈ P. Comentario: φ está en la forma FNC si es una conjunción de disyunciones de variables o variables negadas, como p.ej. (x1 ∨ x2) ∧ x4 ∧ (¬x3 ∨ x5 ∨ x6).
- Tenemos que considerar un número x total de variables tomadas de 1, tomadas de 2 y tomadas de 3, para así conformar un número combinatorio que representa las posibles formas para SMALL-SAT, la sumatoria de esas combinaciones es polinomial, la solución construida se resuelve en poly(n) y SMALL-SAT pertenece a P
## 3. Un subconjunto D de vértices de un grafo G es un conjunto dominante de G, si todo vértice de G fuera de D es adyacente a algún vértice de D. El problema de determinar si un grafo tiene un conjunto dominante de K vértices se representa por el lenguaje DOM-SET = {(G, K) | G es un grafo que tiene un conjunto dominante de K vértices}.
### a. Justificar por qué DOM-SET no estaría en P
- Una MT que acepta el lenguaje prueba en el peor caso todas las permutaciones de los vértices, lo cuál conlleva a V! permutaciones, eso lleva un tiempo exp(n), por lo tanto, a priori pareciera que DOM-SET no está en P.
### b. Probar que DOM-SET ∈ NP
- Dado el grafo G, tal que G = ({1,2,3,4}, {(1,2), (2,3), (3,4), (4,1)}) y el subconjunto de vértices D = (1,2,3)
- La verificación de la sintaxis de G y D es de orden O(n^2)
- La verificación de que D define un conjunto dominante de G es de orden O(n^2)
 + Validar que el arco (1,2) formado a partir de D este en el conjunto E => O(|E|)
 + Validar que el arco (2,3) formado a partir de D este en el conjunto E => O(|E|)
 + Validar que el vértice (4) sea adyacente con alguno que conforma D => O(|E|)
 + |D| = |V| - 1, se hacen 3 validaciones, por lo tanto tarda O((|V|-1)*|E|) = O(n^2)
 + En total = O(n^2) + O(n^2) = O(n^2).
- Puedo validar la solución en tiempo poly(n), por lo tanto DOM-SET pertenece a NP
### c. Justificar por qué el complemento de DOM-SET no estaría en NP
- Pude probar que DOM-SET no pertenece a P, ya que no existe (al menos a mi no se me ocurrió) una MT que resuelva el lenguaje en tiempo poly(n). Pero puede probar que pertenece a NP mediante una verificación de tiempo poly(n), por la propiedad de conjuntos, el complemento de DOM-SET pertenece a CO-NP, ya que si pertenecierá a P (que no es el caso) su complemento estaría en P.
## 4. Dos grafos son isomorfos si son idénticos salvo por la disposición de sus vértices. P.ej. el cuadrado con arcos (1,2), (2,3), (3,4) y (4,1) es isomorfo al cuadrado con arcos (1,2), (2,4), (4,3) y (3,1). El problema de determinar si dos grafos son isomorfos se representa por el lenguaje ISO = {(G1, G2) | G1 y G2 son grafos isomorfos}.
### a. Justificar por qué ISO no estaría en P.
- Una solución podría ser que una MT M reciba dos grafos, verificar que los vértices de ambos son iguales, que el número de arcos sea iguales. Después debería verificar que difieran en al menos un arco, en el peor de los casos se chequean las permutaciones de todos los vértices, lo cuál me llevaría un tiempo exp(n). Por lo tanto, ISO pareciera no pertenecer a P.
### b. Probar que ISO ∈ NP.
- Dado el grafo G1 = ({1,2,3,4}, {(1,2), (2,3), (3,4) y (4,1)}) y el grafo G2 = ({1,2,3,4}, {(1,2), (2,4), (4,3) y (3,1)})
- La verificación de la sintaxis de G1 y G2 es de O(n^2)
- La verificación de que G1 y G2 son isomorfos es de O(n^3)
 + Verifico que G1 y G2 tengan los mismos vértices => O(|V|^2)
 + Usando la función f, verifico si el arco de G1 (1,2) está en G2 => O(|E|)
 + Usando la función f, verifico si el arco de G1 (2,3) está en G2 => O(|E|)
  + Con este ejemplo, ahí encuentro un arco diferente, por lo que la MT dice para con qA, pero si el ejemplo es diferente, podría seguir.
 + Todas estas verificaciones tardan O(n^3)
- En total = O(n^2) + O(n^3) = o(n^3)
- Puedo validar la solución construida en tiempo poly(n), por lo tanto ISO pertenece a NP
### c. Justificar por qué el complemento de ISO no estaría en NP.
- Copypaste del inciso 3c
### Ayuda para (b): la MT asociada debería recibir dos grafos G1 y G2 y una función f de los vértices de G1 a los vértices de G2, y verificar si los vértices de G1 y G2 son iguales y si se cumple que un arco (v1,v2) está en G1 sii el arco (f(v1),f(v2)) está en G2