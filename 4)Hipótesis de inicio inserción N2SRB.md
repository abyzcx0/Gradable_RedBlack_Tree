Considerese un arbol N2SRB cualquiera, donde debe insertarse un nodo:

El nodo siempre resultara como nodo terminal(hoja) por propiedad de insercion bst.
El nodo es asignado rojo.

Para todo caso RB(excepto insercion de la raiz, que es asignacion directa de color negro), el algoritmo pide revisar solo el color del padre, y una vez determinado el caso rojo/rojo, el color del tio.
En ambos casos igualmente se puede originar una cascada de arreglos. pero RB es mas eficaz en detener propagacion por rotacion con tio negro(y permitir rojos hermanos ambos).

En el subconjunto de arbol N2SRB es ligeramente diferente localmente, pero significativo en la recursion:
si el nodo insertado no tiene hermano(NIL), no se hace nada(correcto RB)
si el nodo insertado tiene hermano rojo(por tanto padre negro), a diferencia de RB, no es estatico, sino que fuerza un flip.
NOTA: aunque paresca una gran diferencia, en realidad una siguiente insercion generaria exactamente lo mismo en RB clasico.

despues de eso, la diferencia es por forzar propagacion para depurar hermanos rojos ademas de padre/hijo rojos del RB clasico.
