# Practica 3 - Jerarquía de la Computabilidad (2da parte)

## 1.  Probar que los lenguajes LU = {(< M >, w) | M acepta w}, y HP = {(< M >, w) | M para sobre w} pertenecen a la clase RE. Ayuda: construir MT y pare (en casos positivos)

//Verificar solución
 * LU = {(< M >, w) | M acepta w} ∈ RE. La siguiente MT MU acepta el lenguaje LU. Dado un input (< M >, w), ejecuta M sobre w, y acepta si y solo si M acepta a w
 * HP = {(< M >, w) | M para sobre w} ∈ RE. La siguiente MT MHP acepta el lenguaje HP. Dado el input (< M >, w), ejecuta M sobre w, y acepta si y solo si M acepta w.

## 2. Responder cada uno de los incisos
 ### 1. ¿Se puede decidir si una MT M con una cinta, a partir de la cadena vacía λ, escribe alguna vez un símbolo no blanco? Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en loop?
  * Si, se puede decidir en a lo sumo Q estados, siendo Q la cantidad de estados

 ### 2. ¿Se puede decidir si a partir de un input w, una MT M que sólo se mueve a la derecha para? Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en loop?
  * Se puede decidir. Es como mucho |w| + Q, w es el tamaño de la entrada y Q la cantidad mácima de estados
 
 ### 3. ¿Se puede decidir si dada una MT M, existe un input w a partir del cual M para en a lo sumo 10 pasos? Ayuda: ¿Hasta qué tamaño de cadenas hay que chequear?
  * Se puede decidir calculando la cota máxima de pasos distintos
 ### 4. ¿Se puede decidir si dada una MT M, existe un input w de a lo sumo 10 símbolos a partir del cual M para? Ayuda: ¿En este caso se puede acotar la ejecución de M considerando la cantidad de pasos, la cantidad de celdas recorridas u otro parámetro?
  * No se puede decidir porque es la definición de HP

## 3. Explicar cómo enumeraría los números naturales pares, los números enteros, los números racionales (o fraccionarios) y las cadenas de Ʃ* siendo Ʃ = {0, 1}
  * Para los números naturales pares se podría asignar a cada par así mismo en el conjunto de los números naturales mediante la función Identidad(n). Recordar que la función Identidad(n) es f(x)=x, es una función inyectiva.

  * Para los números enteros se podría mapear el 0 entero por el 0 natural, a cada número entero positivo mapearlo con un número par con la función 2n, a cada número entero negativo mapearlo con un número impar con la función -2n-1.

  * Para los números racionales usamos la función f(x)=2^n*3^d, siendo n el númerador y d el denominador. Para los números racionales negativos la función sería f(x)=2^-n *3^d.

  * Para las cadenas de Ʃ*, siendo Ʃ = {0,1}, a cada string se le asigna un número en función de su representación en el sistema binario que lo mapea a los naturales.

## 4. Una función f: A -> B se dice que es total computable, si y sólo si existe una MT Mf que computa f para todo elemento a ∈ A. Sea la función fHP : Ʃ* -> {0, 1}, tal que:
 * fHP(x) = 1, si x = (< M >, w) y M para a partir de w.
 * fHP(x) = 0, si x = (< M >, w) M no para a partir de w. 
Probar que la función fHP no es total computable. Ayuda: Se podría probar que asumiendo que fHP es total computable, se llega a que HP es recursivo.
  * Dada una máquina M que dado un input w, en el caso de que w sea un código de MT, es decir < N >, la MT M hace:
   1. Ejecuta MHP sobre (< N >, < N >).
   2. Si MHP dice qA, entonces M "se hace entrar en loop".
   3. Si MHP dice qR, entonces M para.
  * Con esta máquina simulamos el input < M > sobre M, lo cuál lleva a una contradicción:
   + Si M para sobre < M >, significa que MHP dijo que M no para sobre < M > (MHP -> qR)
   + Si M no para sobre < M >, significa que MHP dijo que M para sobre < M > (MHP -> qA)
  * Por lo tanto, no puede existir M. Y como M se construyó a partir de MHP, tampoco puede existir MHP. HP no es recursivo.

## 5. Responder cada uno de los incisos:
 ### 1. Si L1 ∈ RE y L2 ∈ RE ¿L1 - L2 ∈ RE?
  * El enunciado es falso, un contraejemplo podría ser, por ejemplo, L1=Ʃ* ∈ RE & L2=LHP ∈ RE, la resta nos da L^cHP, por el mapa de la computabilidad sabemos que L^cHP ∈ CO-RE.
 ### 2. Si L1 ⋂ L2 ∈ RE ¿L1 o L2 ∈ RE?
  * El enunciado es falso, un contraejemplo podría ser, por ejemplo, L1=Ʃ* ∈ 𝓛-(RE ⋃ CO-RE) y L2=^cƩ* ∈ 𝓛-(RE ⋃ CO-RE), la resta nos da L=∅ ∈ R.
 ### 3. Si L1 ⋃ L2 ∈ RE ¿L1 o L2 ∈ RE?
  * El enunciado es falso, usando el mismo contraejemplo que el inciso 5.2, en este caso, el resultado de la resta es Ʃ* ∈ R.


## 6. Explicar (informal pero claramente) cómo sería una MT que genera la n-ésima fórmula booleana satisfactible, cuya sintaxis contiene variables de la forma xi, los operadores lógicos del conjunto {¬, ∧, ∨}, y paréntesis.
  * Se crea una MT M que haga:
   + Aclaración: La MT M va a contar con otras MT's (MT G y MT M1).
   1. En la cinta 1 inicie el contador n.
   2. En la cinta 2 se simula la MT generadora < G > la cuál genera un string, de forma canónica, y lo copia en la cinta 3 (cada vez que toque el paso 2, la máquina < G > genera el string y pisa lo que haya en la cinta 3).
   3. Sobre la cinta 2, donde está la cadena generada, se simula la máquina < M1 > la cuál se encarga de verificar si se trata de una fórmula booleana satisfactible, en ese caso, hace n-- (cinta 1).
   4. Si n==0, la máquina para y la cadena que quedó en la cinta 3 es la n-ésnima fórmula booleana satisfactible. Si n!=0, se vuelve al paso 2.