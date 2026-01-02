Esta parte es especulativa, y abierta a interpretacion y pruebas.

Sea un arbol RB clasico, el arbol  en si se puede considerar efectivo para su trabajo al mantener logaritmica la varianza de altura, teniendo una cota limite para el peor caso cercana a 2logN
Sea un arbol RB tipo N2SRB, no se ha investigado si el propagar/forzar correcciones ayuda a mejorar el balance mas que RB clasico, ni hasta que cota para el peor caso(quizas igual a RB)
pero por intuicion, la presencia de nodos rojos aislados divide ramas hermanas en una con 1 mas de rojo que la otra(lo cual podria apuntar a similitud avl pero no exacto)
Ahora bien, un Gradable RB se basa en la distribucion optima de esos rojos tal que generen alturas similares de forma global(si posible), eso potencialmente puede ser mas balanceado que avl, o peor hasta el limite de un RB normal, 
segun el criterio de reordenamiento de rojos.
En conclusion: se aclara que encontrar el criterio de balanceo de rojos el lo que puede mejorar el N2SRB y por ende el RB. el N2SRB es la infraestructura necesaria para la transicion de RB a GRB.

Ahora bien, si definimos GRB como el subconjunto optimo de N2SRB, y este un subconjunto restringido de RB; se puede ver que GRB seria la version optimizada de balance de RB.
mantener un RB dentro de los parametros optimos GRB puede dar origen a un arbol muy balanceado, mientras que relajar las restricciones en un GRB solo degenera a RB.

Y estos cambios se pueden realizar por cada operacion u opcional, un GRB puede permitirse facilmente actuar como RB puro sin que ello afecte su validez RB, pero un RB si requiere pasar a N2SRB y luego gradarse para ser GRB. por tanto la relacion no es bidireccional directa.

Otro punto a tratar es exacto el ajuste adaptable, es comprensible que en escrituras se pueda directamente tratar N2SRB/GRB como RB, dejara de ser ellos y pasara a ser un RB normal.
y se puede(opcionalmente) pasar a N2SRB->GRB para optimizacion de lectura.
