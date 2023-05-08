# Practica 7 - Clase NPI + Complejidad espacial + Miscelaneas
## 1. La noción de certificado es la de una cadena y que contribuye a probar que otra cadena w pertenece a un lenguaje. Por ejemplo, vimos en el caso de SAT que un certificado para una fórmula φ de SAT es una asignación A de valores de verdad a las variables de la fórmula. En este caso particular el certificado es suscinto, porque |A| = poly (|φ|). Indicar certificados para las siguientes lenguajes, y especificar y justificar cuáles son suscintos: CH (grafos con circuito de Hamilton), NOSAT (fórmulas no satisfactibles), ISO (grafos isomorfos), NODIVISOR (números que no tienen un divisor que termina en 3).
- CH:
 + Un posible certificado para CH es el mismo CH, es decir, el mismo camino de Hamilton para el grafo.
 + Se puede verificar en tiempo polinomial, ya que solo es recorrer el grafo y verificar que los vértices no aparezcan más de una vez (salvo el primero). Ocupa espacio polinomial, ya que el camino de Hamilton es un camino con todos los vértices no repetidos del grafo. Por lo tanto, el certificado es suscinto.
- NOSAT:
 + Un certificado podría ser una asignación de valores de verdad que hagan que la fórmula booleana no sea satisfactible.
 + Su tamaño depende de las variables de la fórmula (2^|φ|), por lo que el certificado no es suscinto.
- ISO:
 + Un certificado podría ser una agrupación de tuplas de tamaño |V| de la forma (a,b), tal que a representa el vértice de un grafo G1 y b representa el vértices de un grafo G2, es decir, sería un mapeo de uno a otro
 + Su tamaño es polinomial, ya que debe codificar ambos grafos (O(n^2)), entonces el certificado es suscinto.
- NODIVISOR:
 + Un certificado podría ser un número primo z que no tenga un divisor que termina en 3, por ejemplo, el número primo 17 no tiene ningún divisor que termine en 3.
 + El certificado es suscinto, ya que puedo verificar en tiempo polinomial si el número posee algún divisor que termine en 3, y ocupa espacio polinomial solo se trata de un número.
## 2. Probar que la asunción NP ≠ CO-NP es más fuerte que la asunción P ≠ NP, es decir que la implica. *Ayuda: intentar con el contrarrecíproco.*
## 3. Justificar por qué se consideran tratables sólo a los problemas que se resuelven en espacio logarítmico.
- Sea una MT M que trabaja en espacio S(log b n) y en tiempo T(n) = c^log b n, siendo b > 1 y c > 0. Si b = c, entonces T(n) = b^log b n = n. De esta manera, puedo decir que los problemas tratables son aquellos que trabajan en espacio logaritmico ya que se resuelven en tiempo polinomial.
## 4. Probar que una MT que trabaja en tiempo poly(n) lo hace en espacio a lo sumo poly(n), y que una MT que trabaja en espacio poly(n) lo hace en tiempo a lo sumo exp(poly(n)).
- **MT que trabaja en tiempo poly(n) lo hace en espacio a lo sumo poly(n)**
 + Pensar que si una MT M trabaja en tiempo poly(n) no podría hacer más de poly(n) pasos, lo que lleva a que no pueda escribir más de poly(n) celdas de todas las cintas de trabajo.
- **MT que trabaja en espacio poly(n) lo hace en tiempo a lo sumo exp(poly(n))**
 + Se puede detectar, para una MT que trabaja en espacio poly(n), si la máquina loopea o no mediante sus configuraciones: (n+2) * poly(n) * K * |Q| * |Σ|^poly(n) * K. Con esto dicho, se puede concluir que la máquina trabajará en tiempo O(c^poly(n)), con c > 0
  + (n+2) por el input
  + poly(n) representa las celdas en cada Ki cinta de trabajo.
  + |Q| estados posibles
  + |Σ| símbolos posibles en cada celda de las poly(n) usadas en cada Ki cinta de trabajo
## 5. Probar que el problema de los palíndromos está en SPACE(n).
- Recordar que el problema de los palíndromos pertenece a TIME(T(n)), por lo que su MT M no podría hacer más de T(n) pasos y no podría escribir más de T(n) celdas de todas las cintas de trabajo. Por lo tanto, el problema de los palindromos trabaja en espacio S(n) y pertenece a SPACE(S(n)).
## 6. Probar que FACT = {(N, M) | N tiene un divisor primo menor que M} está en la clase CO-NP. *Ayuda: Todo número natural N se descompone de una única manera en factores primos, los cuales concatenados no ocupan más de poly(|N|) símbolos.*
