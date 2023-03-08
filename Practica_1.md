# Practica 1 - Máquinas de Turing (MT)

1. Responder breve y claramente los siguientes incisos:
    a. ¿En qué se diferencia un problema de búsqueda de un problema de decisión?
        Un problema de decisión es aquel para el que existe una MT que responde SI o NO.
        En cambio, un problema de búsqueda es más general, el output de la MT no es un acepto o un rechazo,
        es un resultado
    
    b. ¿Por qué en el caso de los problemas de decisión, podemos referirnos indistintamente a problemas y lenguajes?
        Un lenguaje es un conjunto de cadena de símbolos que va asociado a un problema, el lenguaje contiene todos
        los strings para los que la MT "dice" que SI

    
    c. En la clase 1 se presentó el problema de satisfactibilidad de las fórmulas booleanas, en su forma de decisión: 
    *“Dada una fórmula φ, ¿existe una asignación A de valores de verdad que la hacen verdadera?”* Enunciar el problema 
    de búsqueda asociado.
        En MT de búsqueda me daría la asignación de valores de verdad que hacen a φ verdadera
        En MT de decisión me diría si existe una asignación de valores que hacen que φ sea verdadera o si no existe
    
    d. Además de la visión de MT que reconoce lenguajes (visión reconocedora), está la visión de MT que los genera 
    (visión generadora). En el caso del problema del inciso anterior, ¿qué lenguaje generaría la MT de visión generadora 
    que resuelve el problema?
        Generaría un lenguaje con formulas booleanas que además son satisfacibles
    
    e. ¿Qué postula la Tesis de Church-Turing?
        Postula que todo lo computable puede ser resuelto en una MT
    
    f. ¿Cuándo dos MT son equivalentes? ¿Y cuándo dos modelos de MT son equivalentes?
        Dos MT son equivalentes cuando para toda MT M1 de un modelo existe una MT M2 equivalente del otro, es decir
        L(M1) = L(M2). Dos modelos de MT son equivalentes si dada una MT M1 de un modelo, existe otra MT M2 equivalente
        del otro, por ejemplo, el modelos de MT M1 es 1 cinta y el de MT M2 es de k cintas pero su lenguaje es el mismo

2. Dado el alfabeto Ʃ = {0, 1}:
    a. Obtener el conjunto Ʃ* y el lenguaje incluido en Ʃ* con cadenas de a lo sumo 2 símbolos
      Ʃ* = {λ, 0, 1, 00, 01, 10, 11}

    b. Dado el lenguaje L = {0^n1^n | n ≥ 0}, calcular Ʃ* ⋂ L, Ʃ* ⋃ L y L^c con respecto a Ʃ*.
        Ʃ* ⋂ L = L
        Ʃ* ⋃ L = Ʃ*
        L^c = Ʃ* - L

3. En la clase 1 se mostró una MT no determinística (MTN) para aceptar las cadenasde la forma ha^n o hb^n, con n ≥ 0. 
Construir una MT determinística (MTD) equivalente.


4. Describir una MT de K cintas (plantear la idea general, opcionalmente construirla formalmente), que acepte 
de la manera más eficiente posible el lenguaje L = {a^nb^nc^n | n ≥ 0}.


5. Explicar (informal pero claramente) cómo simular una MT por otra que no tenga el movimiento S 
(es decir el no movimiento).
    Para simular el no movimiento, se podría, por ejemplo, hacer que el cabezal vaya a la derecha (R) y después
    a la izquierda (L). Obivamente sin cambiar el símbolo corriente

6. En la clase 1 se construyó una MT con dos cintas para aceptar el lenguaje L = {w | w ∈ {a, b}* y w es un palíndromo o “capicúa”}. Construir una MT con una cinta para aceptar el mismo lenguaje (la solución que vimos para aceptar el lenguaje 
de las cadenas a^nb^n, con n ≥ 1, puede ser un buen punto de partida).

*Los ejercicios 7. y 8. están resueltos parcialmente al final de la ppt 1*

7. Construir una MT que calcule la resta de dos números (se puede considerar la idea de solución propuesta en la clase 1).


8. Construir una MT que genere todas las cadenas de la forma a^nb^n, con n ≥ 1 (se puede considerar la idea de solución 
propuesta en la clase 1).