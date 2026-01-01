Para que un árbol sea considerado Rojo-Negro valido, debe cumplir estrictamente estas cinco propiedades en todo momento estático:

A)​Cada nodo es rojo o negro.

B)​La raíz siempre es negra.

C)​Las hojas (nodos NIL/vacíos) son negras.

D)​Si un nodo es rojo, sus hijos deben ser negros. (No puede haber dos nodos rojos seguidos en un camino).

E)​Propiedad del camino negro: Cualquier camino/ruta desde un nodo hasta sus hojas descendientes debe contener el mismo número de nodos negros.

ahora bien, se considera una variante subconjunto de arboles RB con una restricción adicional para considerarse valido dentro del mismo subconjunto:

F)No debe tener sus nodos hijos ambos rojos: puede tener ambos hijos negro/NIL, o un nodo negro/NIL y otro rojo; independiente de la lateralidad, pero no ambos hijos rojos (por tanto, no debe existir hermanos rojos, de darse el caso se considera que requiere correccion)

Esta restriccion adicional no es parte del funcionamiento del grupo RB clasico, pero tampoco invalida su pertenencia a él.

Ahora bien, dado el caso de hermanos ambos rojos y siendo considerado invalido y a corregir, se ha de describir la forma correspondiente de tratar con ello:

Para mantener las igualdades en altura negra, y bajo la garantia que no se esta dando en el mismo tiempo una violacion rojo rojo de tipo padre/hijo, se consideran los nodos presentados  en la siguiente estructura y disposición:

-un nodo negro padre de ambos nodos rojos
-nodos rojos, hermanos, cada uno con solamente hijos negros/NIL
-aun no se esta considerando el color del nodo superior al padre(abuelo) ni su hermano(tio), puesto que no hay conflicto con el nodo padre(negro) en el estado presente.

La operacion procede de la siguiente manera:
1)los nodos rojos pasan a ser negros
 *este cambio es irrelevante para sus hijos, que son negros tambien.
2)El padre asume el color rojo, para mantener la invariante de altura negra en las rutas descendientes.

A nivel local se ha corregido el problema, pero el cambio del padre a rojo puede haber creado otro desajuste, que se daria si su padre(abuelo) es rojo, o si su hermano(tio) es rojo, dado que no se permite rojos padre/hijo ni hermanos ambos.
* cabe aclarar que el desajuste se genera un nivel mas arriba, manteniendo validez en la parte inferior a el, y por tanto solo puede converger hacia arriba, hasta encontrar un lugar estable o la raiz.

Una vez que todas las correcciones se han propagado hacia arriba, se obtiene un arbol con lo que denominaremos 'rojos aislados'(padre negro, hijos negros, hermano negro).

Si todo el arbol cumple con esa característica, entonces lo denominaremos un arbol N2SRB(not 2 siblings red, black), tal que pertenece y cumple con las reglas RB clasicas, ademas de la regla adicional de prohibir hermanos ambos rojos.

