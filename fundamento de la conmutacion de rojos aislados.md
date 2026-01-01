Sea un arbol RB perteneciente al subconjunto N2SRB, que especifica como regla adicional que no debe tener hermanos ambos rojos a la vez.

Este da origen a lo que denominaremos 'rojos aislados', ya que su parentesco directos son todos negros(padre negro, hijos negros, y hermano negro).

Con esas condiciones especificas, solo pueden ocurrir dos configuraciones locales particulares, simetricas:

A) padre negro y el nodo es hijo izquierdo rojo. eso por defecto deja que su hermano derecho sea negro(por condicion de validez) y sus hijos sean negros(condicion de validez).

B) similar, padre negro, hijo rojo derecho con sus respectivos hijos negros, y hermano izquierdo negro.

Se quiere demostrar una operacion añadida que permite conmutar/trasladar un nodo rojo de una rama a la rama hermana carente de el.

la operacion es la siguiente(y simetrica para el otro caso):

Sea el padre y el hijo izquierdo rojo, se realiza una rotacion talque:

padre->izq apunta a hijo->der
hijo->der apunta a padre
el puntero que apunta desde arriba al padre apunta al hijo(o se retorna la nueva cabecera)

Efectivamente cambiando la jerarquia mediante una rotacion, pero respetando orden bst.

Sin embargo, esto por si solo desbalancea la cantidad de nodos rojos/negros por ruta.

para arreglarlo, se realiza un cambio de coloracion en ambos nodos(padre e hijo pasan al color cpntrario)
*se recomienda la recoloracion previa rotación, y considerar ambas operaciones inseparables.

El resultado es que el nuevo nodo superior(hijo previo, es negro, conservando la negrura inicial para todas las rutas involucradas, el camino derecho de el es ahora rojo(previo padre), pero observamos que ahora a ese nivel el rojo esta "del otro lado"(a la derecha)

Ahora bien, si se aplica el traslado hacia el otro lado se obtiene el orden original.

Mediante esta demostración se indica que es una operacion neutra con respecto a la altura negra y no genera violacion de reglas en N2SRB.

Pero, y esto es importante, la rotacion si  produce una variacion de altura real con respecto a las ramas hermanas involucradas, donde la rama que cede el rojo pierde altura y la otra gana altura por el simple hecho de rotar, fuera del hecho de ganar/perder un nodo rojo(considerando que la altura real es rojos+negros y estos son constantes)

por tanto la operacion añadida puede segun criterio de aplicacion, mejorar o empeorar el balance de altura real, pero sin alterar la altura negra.

