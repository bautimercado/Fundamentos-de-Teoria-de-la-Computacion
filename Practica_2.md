# Practica 2 - Jerarquía de la Computabildiad

## 1. Responder las siguientes preguntas: 
  1. ¿En qué difieren los lenguajes recursivos, recursivamente numerables no recursivos, y no
recursivamente numerables?
   * Los lenguajes recursivos son aquellos para los que existe una MT que los acepta y para siempre (o rechaza). Los recursivamente numerables no recursivos serían todos los lenguajes que están en RE y no en R, mientras que los no recursivamente numerables son aquellas para los que ni siquiera hay una MT

  2. Probar que R⊆RE⊆𝓛 cursiva mayuscula. Ayuda: usar directamente las definiciones.
   * Se da que R ⊆ RE, ya que si un lenguaje posee una MT que con un lenguaje acepta o rechaza, entonces eso entra en la definición de RE, porque los lenguajes comprendidos en ese conjunto poseen una MT que los acepta, rechaza o loopea
   * Se da que RE ⊆ 𝓛, porque 𝓛 es el conjunto de todos los lenguajes, tengan MT o no, RE representa una porción de esos lenguajes (los que tienen una MT que los acepta, para o loopea)

  3. ¿Qué lenguajes de la clase CO-RE tienen MT que los aceptan?
    * Los lenguajes que también pertenecen a la clase R, es decir, RE ∩ CO-RE

  4. Justificar por qué los lenguajes Ʃ* y ∅ son recursivos
  * Se puede construir, para ambos, una MT que puede aceptar o rechazar
  * Para  Ʃ* se podría hacer una MT que, sin importar el input, siempre termine en qA. Así, la MT siempre aceptará
  * Para ∅ se podría hacer una MT que rechace siempre sin importar el input

  5. Justificar por qué un lenguaje finito es recursivo
   * Porque existe una MT capaz de reconocerlo y, lo acepta o lo rechaza. Podría construirse una MT con dos cintas: una con el lenguaje input y otra con el lenguaje finito. La idea es ir comparando los símbolos

  6. Justificar por qué si L1 ∈ CO-RE y L2 ∈ CO-RE, entonces (L1 ⋂ L2) ∈ CO-RE. Ayuda: una
manera de resolverlo es utilizando las leyes de De Morgan en el marco del álgebra de Boole.
  * Se asume lo primero verdadero, se tiene que probar lo último. Hay que partir de L1 y L2 hasta llegar a (L1 ∩ L2) ∈ CO-RE
  * L1 ∈ CO-RE y L2 ∈ CO-RE = L1^c ∈ RE y L2^c ∈ RE
  * L1^c ∪ L2^c ∈ RE
  * (de Morgan) (L1 ∩ L2)^c ∈ RE = (L1 ∩ L2) ∈ CO-RE

## 2. Considerando el Lema 2 estudiado en la clase 2:
  1. ¿Cómo implementaría copiar el input w en la cinta 2 de la MT M?
    * Copiar el símbolo de la cinta 1 en la cinta 2, mover el cabezal de ambas cintas a la derecha, copiar el símbolo y así hasta llegar al B en la cinta 1
  2. ¿Cómo implementaría borrar el contenido de la cinta 2 de la MT M?
    * Similar al copiar, se tiene que recorrer la cinta 2 y pisar los símbolos con B. Para esto, se necesitaría marcar, con algún caracter especial, el principio y el final de la cadena. Debería ir a uno de los extremos (marcados) y empezar a borrar hasta el otro extremo

## 3. Probar
  1. La clase R es cerrada con respecto a la operación de unión. Ayuda: la prueba es similar a la
desarrollada para la intersección.
   * Sea L1 ∈ R y L2 ∈ R, probar L1 ∩ L2 ∈ R
   * Dadas dos MT M1 y MT M2 que aceptan L1 y L2 y paran siempre. Se podría construir una MT M, primero se pasaría el input w por la MT M1, si ésta acepta, la MT M acepta, si rechaza, el input w pasa a la MT M2, si ésta acepta, la MT M acepta, si rechaza, la MT M rechaza. De esta manera, MT M para siempre porque MT M1 o MT M2 paran siempre.

  2. La clase RE es cerrada con respecto a la operación de intersección. Ayuda: la prueba es
similar a la desarrollada para la clase R.
  * Sea L1 ∈ RE y L2 ∈ RE, probar L1 ∩ L2 ∈ RE
  * Dadas dos MT M1 y MT M2 que aceptan L1 y L2 y paran siempre. Se podría construir una MT M en donde, se pasaría el input w por la MT M1, si MT M1 rechaza, la MT M rechaza, si loopea, la MT M loopea, si acepta, entonces se pasa el input w a la MT M2, aplicando el mismo procedimiento, solo que si acepta y para, entonces MT M acepta. 

## 4. Sean L1 y L2 dos lenguajes recursivamente numerables de números naturales representados en notación unaria (por ejemplo, el número 5 se representa con 11111). Probar que también es recursivamente numerable el lenguaje L = {x | x es un número natural representado en notación unaria, y existen y, z, tales que y + z = x, con y ∈ L1, z ∈ L2}. Ayuda: la prueba es similar a la vista en clase, de la propiedad de clausura de la clase RE con respecto a la operación de concatenación.

// Verificar solución
  * Mi idea es realizar una MT de 6 cintas. En la cinta 1 va a estar el input, la cinta 2 la voy a usar de contador de pasos (i), la cinta 3 van a ir los primeros 0+i símbolos, la cinta 4 van a ir los primeros n-i símbolos, en la cinta 5 voy a copiar los primeros símbolos de la cinta 3 y ejecutar M1, en la cinta 6 voy a copiar los primeros símbolos de la cinta 6 y ejecutar M2.
  * Recordar que el input es y+z=x, siendo x el input, voy a ir copiando los símbolos de x en las cintas 5 y 6 donde se ejecutarán M1 y M2. Si las dos aceptan, significa que los 1s que se copiaron en las cintas están en los lenguajes L1 y L2.
  * El contador me sirve para ir haciendolo paralelamente. Si en la cinta 3 se llega a un B, se incrementa el contador y se borran las cintas 3, 4, 5, 6. Sino, se sigue avanzando en las cintas 3 y 4, se borran las cintas 5 y 6. 

// Consultar si se realiza con una MT generadora
## 5. Dada una MT M1 con Ʃ = {0, 1}:
  1. Construir una MT M2 que determine si L(M1) tiene al menos una cadena.
   * Idea general:
    * MT M2 sería una que genere cadenas y se las envie a M1, si al menos una de las cadenas está en M1 dice qA.
   * Construcción de la MT M2
    i. Primero lo primero, inicializar el contador de pasos y de tamaño caracteres (i=1; n=0)
    ii. M2 crea la siguiente cadena v de símbolos con el conjunto {0, 1} según un orden canónico.
    iii. M2 hace i pasos, crea cadenas de tamaño n, y se las envía a M1
    iv. Si M1 dice qA, M2 dice qA
    v. Si M1 dice qR, hago i++; n++ y vuelvo a (ii)
  
  2. ¿Se puede construir además una MT M3 para determinar si L(M1) tiene a lo sumo una cadena? Justificar. Ayuda para la parte (1): Si L(M1) tiene al menos una cadena, entonces existe al menos una cadena w de unos y ceros, de tamaño n, tal que M1 a partir de w acepta en k pasos. Teniendo en cuenta esto, pensar cómo M2 podría simular M1 considerando todas las cadenas de unos y ceros hasta encontrar eventualmente una que M1 acepte (¡cuidándose de los casos en que M1 entre en loop!)

  