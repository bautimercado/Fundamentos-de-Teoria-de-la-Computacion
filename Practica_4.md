# Practica 4 - Reducciones + MT restringidas

## 1. Considerando la reducción de HP a LU descripta en clase, responder:
### a. Explicar por qué la función identidad, es decir la función que a toda cadena le asigna la misma cadena, no es una reducción de HP a LU.
- Sintaticamente, la función identidad recibe un par que tiene (< M >, w), lenguaje de HP, y devuelve exactamente lo mismo, los strings que pertenecen a HP van a tener la misma forma que los strings que pertenecen a LU.
- Hasta ahí todo bien, el problema es que los pares que pertenecian a HP son los pares para los cuales < M > se detiene sobre w, mientras que los pares que pertenecen a LU son pares tales que < M > acepta ese w. El caso que me genera el problema es cuando tenga una M2 (la que trata LU) que se detiene sobre w pero en qR porque el par pertenece a HP y no pertenece a LU. Por lo tanto, la función identidad no cumple con la definición de función de reducción
### b. Explicar por qué las MT M´ generadas en los pares (< M´ >, w), o bien paran aceptando, o bien loopean.
- Recordar que HP es un lenguaje de esta forma. HP = {(< M >, w) | M para sobre w}. La máquina de Turing MT M' es la MT para el lenguaje LU, se comporta igual que M, solo que si M para (qA o qR), M' acepta; Si M loopea, M' loopea
### c. Explicar por qué la función utilizada para reducir HP a LU también sirve para reducir HP^C a LU^C
- Por la propiedad de las reducciones en los complementos, se cumple que HP α LU <-> HP^C α LU^C
### d. Explicar por qué la función utilizada para reducir HP a LU no sirve para reducir LU a HP.
- No me serviría, si bien la forma sintactica de las cadenas es la misma en ambos lenguajes, la implementación no es la adecuada porque justamente debería ser al reves. Una nueva función de comprensión podría ser así:
 + f((< M >, w))=(< M' >, w) -> tal que M' se comporta igual que M, salvo que cuando M dice qR, M' loopea.
### e. Explicar por qué la siguiente MT Mf no computa una reducción de HP a LU: dada una cadena válida (< M >, w), Mf ejecuta M sobre w, si M acepta entonces genera el output (< M >, w), y si M rechaza entonces genera una cadena inválida, por ejemplo la cadena 1.
- Parcialmente la reducción es correcta, el problema es que no tiene en cuenta el caso en el que que la M de HP para (dice qA o qR) porque si HP dice qR entonces la M de LU también dice qR cuando no debería ser así, LU debería ser qR en el caso de que HP quede loopeando.
## 2. Considerando la reducción de LU a LƩ* descripta en clase, responder:
### a. Explicar por qué no sirve como función de reducción alternativa la función siguiente: a todo input le asigna como output el código < MƩ* >.
- < MƩ* > seguro pertenece a LƩ*, si la función de reducción devuelve algo que siempre pertenece a LƩ*, podrían darse casos en los que la función reciba algo que no pertenece a LU.
### b. Explicar por qué la reducción descripta en clase no sirve para probar que LƩ* ∉ RE.
- Sabemos que LU, que pertenece a RE - R, permite verificar que LƩ* ∉ R, pero no nos permite ver si LƩ* ∉ RE ya que LU pertenece a dicho conjunto, por lo cuál debería buscar otro lenguaje y otra función de reducción que tampoco pertenezca a RE
- LU ∈ RE - R, LU^C ∈ CO-RE - R, es decir, LU^C ∉ RE, por lo tanto LU^C me podría servir para demostrar formalmente que LƩ* ∉ RE
## 3. Un autómata linealmente acotado (ALA) es una MT con una sola cinta, con la restricción de que su cabezal sólo puede moverse a lo largo de las celdas ocupadas por el input. Probar que el lenguaje aceptado por un ALA es recursivo. Ayuda: *¿en cuántos pasos se puede detectar que el ALA entra en loop?*
- Sabemos que se mueve en un espacio limitado, la cantidad de combinaciones totales que hay de valores distintos que puede haber en cada una de las posibles celdas en las que se va a ir moviendo el cabezal y de posibles estados que se encuentre la máquina va a ser finita (configuraciones, número combinatorio), similar a la solución de engañar el HP con espacio acotado. Una vez que la máquina haga más movimientos que la cantidad total de combinaciones, seguro que en ese caso loopea
- Entonces, podría construir una máquina de Turing que siempre para (entonces pertenece a R), tal que se lleve un contador de pasos, se ejecute por pasos, se tenga el número de configuraciones que servirá como un límite, cuando se supere, la máquina dice qR, sino lo supera dice qA. 
## 4. Construir un autómata finito que reconozca el lenguaje de las cadenas de {0, 1}* , es decir todas las cadenas de 0 y 1 de cualquier tamaño incluso la vacía, tales que a todo cero le siga un uno. Ayuda: *En general conviene primero construir el diagrama de transición de estados, porque da una idea de cómo construir el autómata finito.*
- Al no tener memoria, hay que usar estados para aceptar o rechazar cada cadena.
- Sea el siguiente automata finito:
 + Q = {q0, q1, q2, q3}
  + q0: Estado inicial
  + q1: Encontre un 0, chequeo que el siguiente símbolo sea un 1
  + q2: Encontre un 1
  + q3: Encontre algo distinto de 1 después de un 0
 + Ʃ = {0, 1, B}
 + q0 = q0
 + F = {q0, q3}
 + Función de transición:
  + δ(q0, 0) = q1
  + δ(q0, 1) = q2
  + δ(q0, B) = q0
  + δ(q1, 0) = q3
  + δ(q1, 1) = q2
  + δ(q1, B) = q3
  + δ(q2, 0) = q1
  + δ(q2, 1) = q2
  + δ(q2, B) = q0
## 5. Sea el lenguaje DHP = {wi | Mi para desde wi, según el orden canónico}. Encontrar una reducción de DHP a HP.
- DHP está compuesto por cadenas, la idea es encontrar una función de reducción que a partir de esas cadenas genere pares (< M >, w) de HP. Cuando recibimos la cadena, no conocemos el índice de la cadena, tampoco conocemos la i-ecima M. Debería identificar la posición de w en el orden canónico y encontrar la i-ésima M.
- Podría construir una MT Mf qué reciba ese wi, sabemos que hay una MT Mi que para sobre wi, podría tener la cinta 1 con wi, un contador de pasos en la cinta 2, copiar el input de la cinta 1 en la cinta 3, submáquinas generadoras que generen una cadena wi en el orden canónico sobre la cinta 4, que generen códigos de máquina i en el orden canónico sobre la cinta 5, ejecutar la máquina generada de la cinta 5 sobre las cadenas de las cintas 3 y 4, cuando la máquina i para, la MT Mf tira como output el par (< Mi >, wi). Sino, se incrementa el contador, se limpian las cintas 3, 4 y 5.
## 6. Sea el lenguaje LØ = {< M > | L(M) = Ø}. Responder:
### a. Encontrar una reducción de LU^C a LØ. Ayuda: basarse en la idea de la reducción de LU a LƩ*,es muy *similar*.
- Construir una MT Mf que modifique el código que se tenga originalmente para construir una máquina que borre el input y a partir de eso que escriba un input particular en la cinta
- Función de reducción:
 + f((< M >, w)) = < Mw >
- Mw es una MT que borra borra su input original y lo reemplaza por un input vacío, si y solo si, M rechaza w (la parte de LU^C)
 + Si M rechaza w -> L(Mw) = Ø
 + Si M acepta w -> L(Mw) = {Ʃ*}
- La función f es total computable
 + Si la cadena de entrada es válida (< M >, w), pertenece a LU^C, la máquina Mf genera una cadena < MØ > tal que L(MØ) = Ø
 + Si la cadena de entrada no es válida, la máquina Mf no borra el input, es decir, el input es distinto de Ø, por lo tanto L(Mw) != Ø
### b. Considerando la reducción desarrollada en (a), ¿qué se puede decir de LØ, a qué clase de la jerarquía de la computabilidad no pertenece?
- Se comprobó que LU^C puede reducir a LØ, por lo tanto, LØ es tan o más difícil que LU^C, entonces LØ ∈ Ʃ* - (RE U CO-RE)
## 7. Construir una MT que genere todos los índices i tales que (< Mi >, wi) ∈ HP, según el orden canónico.
- 