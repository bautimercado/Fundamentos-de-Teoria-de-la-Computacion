# Practica 3 - Jerarquía de la Computabilidad (2da parte)

1.  Probar que los lenguajes LU = {(< M>, w) | M acepta w}, y HP = {(< M>, w) | M para sobre w} pertenecen a la clase RE. Ayuda: construir MT y pare (en casos positivos)

//Verificar solución
 * LU = {(< M>, w) | M acepta w} ∈ RE. La siguiente MT MU acepta el lenguaje LU. Dado un input (< M>, w), ejecuta M sobre w, y acepta si y solo si M acepta a w
 * HP = {(< M>, w) | M para sobre w} ∈ RE. La siguiente MT MHP acepta el lenguaje HP. Dado el input (< M>, w), ejecuta M sobre w, y acepta si y solo si M acepta w.

2. Responder cada uno de los incisos
 i. ¿Se puede decidir si una MT M con una cinta, a partir de la cadena vacía λ, escribe alguna vez un símbolo no blanco? Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en loop?
  * Si, se puede decidir en a lo sumo Q estados, siendo Q la cantidad de estados

 ii. ¿Se puede decidir si a partir de un input w, una MT M que sólo se mueve a la derecha para? Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en loop?
  * Se puede decidir. Es como mucho |w| + Q, w es el tamaño de la entrada y Q la cantidad mácima de estados
 iii. ¿Se puede decidir si dada una MT M, existe un input w a partir del cual M para en a lo sumo 10 pasos? Ayuda: ¿Hasta qué tamaño de cadenas hay que chequear?
  * Se puede decidir calculando la cota máxima de pasos distintos
 iv. ¿Se puede decidir si dada una MT M, existe un input w de a lo sumo 10 símbolos a partir del cual M para?
Ayuda: ¿En este caso se puede acotar la ejecución de M considerando la cantidad de pasos, la cantidad de celdas recorridas u otro parámetro?
  * No se puede decidir porque es la definición de HP

3. Explicar cómo enumeraría los números naturales pares, los números enteros, los números racionales (o fraccionarios) y las cadenas de Ʃ* siendo Ʃ = {0, 1}

4. Una función f: A -> B se dice que es total computable, si y sólo si existe una MT M que computa f para todo elemento a ∈ A. Sea la función fHP : Ʃ* -> {0, 1}, tal que:
 * fHP(x) = 1, si x = (< M>, w) y M para a partir de w.
 * fHP(x) = 0, si x = (< M>, w) M no para a partir de w
Probar que la función fHP no es total computable.
Ayuda: Se podría probar que asumiendo que fHP es total computable, se llega a que HP es recursivo.



5. Responder cada uno de los incisos
 i. Si L1 ∈ RE y L2 ∈ RE ¿L1 - L2 ∈ RE?
  * Buscar contraejemplos para casos falsos
 ii. Si L1 ⋂ L2 ∈ RE ¿L1 o L2 ∈ RE?

 iii. Si L1 ⋃ L2 ∈ RE ¿L1 o L2 ∈ RE?


6. Explicar (informal pero claramente) cómo sería una MT que genera la n-ésima fórmula booleana satisfactible, cuya sintaxis contiene variables de la forma xi, los operadores lógicos del conjunto {¬, ∧, ∨}, y paréntesis.
