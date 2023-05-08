# Practica 8 - Lógica de Enunciados + Representación Simbólica
## 1. Traduzca al lenguaje simbólico los siguientes enunciados:
### a. Juan necesita un matemático o un informático.
- p: Juan necesita un matemático
- q: Juan necesita un informático
- (p ∨ q)
### b. Si Juan necesita un informático entonces necesita un matemático.
- p: Juan necesita un matemático
- q: Juan necesita un informático
- (q -> p)
### c. Si Juan no necesita un matemático entonces necesita un informático.
- p: Juan necesita un matemático
- q: Juan necesita un informático
- (¬p -> q)
### d. Si Juan contrata un informático entonces el proyecto tendrá éxito.
- p: Juan contrata un informático
- q: El proyecto será exitoso
- (p -> q)
### e. Si el proyecto no tiene éxito entonces Juan no ha contratado un informático.
- p: Juan contrata un informático
- q: El proyecto será exitoso
- (¬q -> ¬p)
### f. El proyecto tendrá éxito si y sólo si Juan contrata un informático.
- p: Juan contrata un informático
- q: El proyecto será exitoso
- (q <-> p)
### g. Para aprobar Lógica, el alumno debe asistir a clase, desarrollar un cuaderno de prácticas aceptable y demostrar que dicho cuaderno ha sido desarrollado por él; o desarrollar un cuaderno de prácticas aceptable y aprobar el examen final.
- p: Aprobar lógica
- q: Alumno asiste a clase
- r: Desarrollar un cuaderno aceptable
- s: Demostrar que el cuaderno lo hizo el alumno
- t: Aprobar el examen final
- (((q ∧ r ∧ s) ∨ (r ∧ t)) -> p)
### h. El alumno puede asistir a clase u optar por un examen libre.
- p: El alumno asiste a clases
- q: El alumno rinde examen libre
- (p ∨ q)
### i. Si x es un número racional e y es un entero, entonces z no es real.
- p: x es un número racional
- q: y es un número entero
- r: z es un número real
- ((p ∧ q) -> r)
### j. La suma de dos números es par si y sólo si los dos números son pares o los dos números son impares.
- p: La suma de dos números es par
- q: Los dos números son pares
- r: Los dos números son impares
- (p <-> (q ∨ r))
## 2. Dada la siguiente información:
- *Si el unicornio es mítico, entonces es inmortal, pero si no es mítico, entonces es un mamífero mortal. Si el unicornio es o inmortal o un mamífero, entonces tiene un cuerno. El unicornio es mágico si tiene un cuerno.*
## Simbolizarla en el Cálculo de Enunciados y responder:
- Frases atómicas:
 + p: El unicornio es mítico
 + q: El unicornio es inmortal
 + r: El unicornio es mamífero
 + s: El unicornio tiene un cuerno
 + t: El unicornio es mágico
- Fórmulas compuestas/Argumentos:
 + A1: (p -> q)
 + A2: ((¬p) -> (r ∧ (¬q)))
 + A3: ((q ∨ r) -> s)
 + A4: (s -> t)
### a. El unicornio es mítico?. Fundamentar.
- Conclusión:
 + A: p
- Valores de verdad para las variables:
 + p: F
 + q: F
 + r: V
 + s: V
 + t: V
- Argumentos + Conclución:
 + A1: (p(F) -> q)   =>    V
 + A2: ((¬p(V)) -> (r(V) ∧ (¬q(V))))    =>    V
 + A3: ((q(F) ∨ r(V)) -> s(V))       =>    V
 + A4: (s(V) -> t(V))    =>     V
 + A: p(F)     =>      F
- La argumentación es inválida porque la conclusión es falsa, por lo tanto, el unicorno no es mítico   
### b. El unicornio no es mítico?. Fundamentar.
- Conclusión:
 + A: ¬p
- Valores de verdad para las variables:
 + p: F
 + q: F
 + r: V
 + s: V
 + t: V
- Argumentos + Conclución:
 + A1: (p(F) -> q)   =>    V
 + A2: ((¬p(V)) -> (r(V) ∧ (¬q(V))))    =>    V
 + A3: ((q(F) ∨ r(V)) -> s(V))       =>    V
 + A4: (s(V) -> t(V))    =>     V
 + A: ¬p(F)     =>      V
- La argumentación es válida porque la conclusión es verdadera, por lo tanto, el unicorno no es mítico
### c. El unicornio es mágico?. Fundamentar.
- Conclusión:
 + A: t
- Valores de verdad para las variables:
 + p: F
 + q: F
 + r: V
 + s: V
 + t: V
- Argumentos + Conclución:
 + A1: (p(F) -> q)     =>   V
 + A2: ((¬p(V)) -> (r(V) ∧ (¬q(V))))    =>    V
 + A3: ((q(F) ∨ r(V)) -> s(V))     =>    V
 + A4: (s(V) -> t)    =>    V
 + A: t(V)      =>    V
- La argumentación es válida porque la conclusión es verdadera, por lo tanto, el unicornio es mágico
## 3. Se sabe que:
- *La página web tiene un error o el examen de álgebra no es el 2 de julio. Si el examen de álgebra es el 2 de julio entonces la página web tiene un error. El examen de álgebra es el 14 de julio si y sólo si la página web tiene un error y el período de exámenes no termina el 10 de julio.*
- Idea: escríbalo como forma argumentativa y determine si es válida o inválida.
- Frases atómicas:
 + p: La página web tiene un error
 + q: El examen de álgebra es el 2 de Julio
 + r: El examen de álgebra es el 14 de Julio
 + s: El período de exámenes termina el 10 de Julio
- Argumentos:
 + A1: (p ∨ (¬q))
 + A2: (q -> p)
 + A3: r <-> (p ∧ (¬s))
## Teniendo en cuenta que el período de exámenes termina el 10 de julio y que la página web tiene un error, deducir la verdad o falsedad de los siguientes enunciados:
- p: V
- s: V
### a. El examen de álgebra es el 2 de julio.
- Conclusión:
 + A: q
- Valores de verdad para las variables:
 + p: V
 + q: V
 + r: F
 + s: V
- Argumentos + Conclusión:
 + A1: (p(V) ∨ (¬q))   =>    V
 + A2: (q(V) -> p(V))      =>   V
 + A3: (r(F) <-> (p(V) ∧ (¬s(F))))    =>  V
 + A: q(V)   =>   V
- La forma argumentativa es válida, por lo tanto, podemos decir que el enunciado "El examen de álgebra es el 2 de julio" es válido
### b. Si la página web no tiene un error entonces el examen de álgebra es el 14 de julio.
- Conclusión:
 + A: ((¬p) -> r)
- Valores de verdad para las variables:
 + p: V
 + q: V
 + r: F
 + s: V
- Argumentos + Conclusión:
 + A1: (p(V) ∨ (¬q))   => V
 + A2: (q(V) -> p(V))  => V  
 + A3: (r(F) <-> (p(V) ∧ (¬s(F))))  => V
 + A: ((¬p(F)) -> r(F))   =>  V
- La forma argumentativa es válida, por lo tanto, podemos decir que el enunciado "Si la página web tiene un error entonces el examen de álgebra es el 14 de Julio" es válido.  
## 4. Se tienen las siguientes premisas (Lo dejo de repaso):
- Si Juan tiene suerte y llueve entonces estudia.
- Juan aprobará si y sólo si estudia o tiene suerte.
- Si Juan no tiene suerte entonces no llueve.
## Sabiendo que llueve, responder:
- Idea: escríbalo como forma argumentativa y determine si es válida o inválida.
### a. ¿Aprobará Juan?
### b. ¿Tendrá suerte Juan?