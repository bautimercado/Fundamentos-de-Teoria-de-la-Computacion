# Practica 6 - Clase NPC + Reducciones

## 1. Mostrar que la relación αP es reflexiva y transitiva.
- Reflexividad:
 + Para probar que L αP L, se podría tener una función de reducción que simplemente devuelva el input sin modificarlo, como el string no se procesa, se trabaja en tiempo eficiente
- Transitividad:
 + Dado que L1 αP L2 y L2 αP L3, la prueba de que L1 αP L3 se podría pensar como que existe una función de reducción f1 para L1 y L2, y una función de reducción f2 para L2 y L3, una función de reducción de L1 a L3 podría ser f(x)=f2(f1(x))
## 2. ¿Por qué si L1 αP L2, entonces L2 es tan o más difícil que L1 en el sentido de la complejidad temporal?
- Si L1 reduce polinomialmente a L2, L2 es tan o más difícil que L1 porque cualquier algoritmo que resuelva L2 también puede ser usado para resolver L1. No se cumple la inversa, por ejemplo, si L2 fuera más fácil que L1 no habría forma de transformar instancias de L1 en instancias de L2 en tiempo polinomial.
## 3. Hemos mencionado que existe una reducción polinomial del problema CH (circuito de Hamilton) al problema TSP (viajante de comercio).
### a. Sabiendo sólo que TSP es NP-completo, ¿se cumple que CH ∈ NP?
- Si, porque efectivamente hay una reducción eficiente de CH a TSP, por lo tanto, CH es como mucho tan difícil como TSP.
- La propiedad es la de la reducción polinomial. Puedo decir que CH está en NP porque TSP está en NP
### b. Sabiendo sólo que CH es NP-completo, ¿se cumple que TSP ∈ NPC?
- Si, por propiedad, como CH reduce a TSP y es NP-Completo, TSP es tan o más difícil que CH, por lo tanto TSP pertenece a NP-Completo (además de la transitividad)
## 4. ¿Por qué si un problema es NP-completo prácticamente está “condenado” a no pertenecer a la clase P?
- Esto pasa porque no se encontró una solución eficiente para ningún problema NP-Completo. La definición de NPC implica que si se encuentra una solución eficiente para un problema NPC, entonces todos los problemas NP se pueden resolver en tiempo eficiente.
- Si un lenguaje pertenece a NPC, se considera "tan difícil" como cualquier otro problema en NP. Si un problema NPC pudiera resolverse en tiempo polinómico, entonces todos los problemas en NP podrían resolverse en tiempo polinómico, lo que contradice la hipótesis de que P≠NP.
## 5. ¿Por qué si L1 ∈ NPC y L2 ∈ NPC, entonces se cumple L1 αP L2 y L2 αP L1?
- Recordar que, si ambos lenguajes son NPC, entonces también son NP y también son NP-Difícil (hay una reducción polinomial de cualquier lenguaje NP a ellos). Con esto dicho, como L1 es NP y L2 es NPC, se puede L1 αP L2 (mismo caso el inverso)
## 6. Probar que si se cumple L1 αP L2, L2 αP L1, y L1 ∈ NPC, entonces L2 ∈ NPC.
- Similar al inciso anterios, si L1 αP L2 y L1 ∈ NPC, entonces L2 es tán o más difícil que L1 por lo que L2 ∈ NPC.
## 7. Explicar cómo agregaría lenguajes a la clase NPC a partir del lenguaje CLIQUE, que se sabe está en la clase NPC.
- Sabemos que CLIQUE pertenece a la clase NPC (lo probamos con una reducción de VC a CLIQUE), por lo cuál, usando el lenguaje CLIQUE, podemos reducir polinomialmente algún otro lenguaje (CH por ejemplo) y probar que ese otro lenguaje también pertenece a la clase NPC, utilizando la función de reducción adecuada para cada reducción.
## 8. Sean los lenguajes A y B, tales que A ≠ Ø, A ≠ Ʃ*, y B ∈ P. Probar: (A ⋂ B) αP A.
## 9. Sea el lenguaje HPA-s-t = {(G, s, t) | G es un grafo que tiene un camino de Hamilton del vértice s al vértice t}. Un grafo G = (V, E) tiene un camino de Hamilton si existe un par de vértices v1 y v2 de V tal que G tiene un camino entre v1 y v2 que recorre todos los vértices restantes una sola vez. Probar que HPA-s-t es NP-completo. Ayuda: se sabe que CH (el problema del circuito de Hamilton) es NP-completo.