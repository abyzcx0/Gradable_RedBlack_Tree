Considerese un arbol N2SRB, en el cual se debe eliminar un nodo cualquiera.

NOTA: se debe entender que la eliminacion es un proceso de busqueda BST y remoción del nodo encontrado/designado, lo cual puede afectar al RB en altura negra, que debe mantener constante en toda ruta del arbol. 
Se hace diferenciación entre el procedimiento de eliminacion bst en si, con la necesidad posterior de reparacion RB.
Ademas se hace referencia que el algoritmo en si tiende a una eliminacion real de un nodo terminal o casi terminal, en reemplazo del lugar especifico, asi que se debe tratar considerando los casos de arreglo desde la base.

Sea una eliminacion de un nodo terminal(o que se haya tomado de reemplazo en otro lugar del arbol) en un arbol N2SRB, segun el algoritmo clasico de eliminacion RB se tiene:

1)el nodo es rojo: se elimina y finaliza, no causa variacion de altura negra.
2)el nodo es negro: aqui se genera el problema, que segun los casos de arreglo se puede resumir como una deuda de negrura que se paga con un rojo.

Pero bajo la configuracion N2SRB, los rojos son escasos y aislados. eso podria pensarse que es un problema, pero es una ventaja, los casos se reducen a esto:

Ubicar el rojo mas cercano al problema, sea en los nodos propios de la ruta o sus hermanos segun cada nivel.(ademas se garantiza que el mas cercano de existir sera segun se evalua un nodo, o el padre o el hermano, porque no puede haber ambos para un nodo determinado por imposibilidad de rojorojo fuera del lugar de arreglo de la eliminacion).

1)si el nodo mas cercano esta en el hermano de ruta, se puede aplicar una operacion de refinamiento/traslacion(ver documento sobre ello) para pasar el nodo rojo a la ruta.
*es practicamente la misma operacion de transformar un rojo hermano a padre en casos de eliminacion RB.

2)hacer la inversa del la correccion de hermanos ambos rojos(es decir flip donde un rojo hereda rojos a sus hijos volviendose negro.
la razon por la que esto no causa problema en la rama hermana es porque, si se empieza del rojo mas cercano en subida, eso anula la posibilidad de encontrar nodos rojos mas abajo, evitando situaciones rojo/rojo en la rama propia o contigua.
3)seguir haciendo flip inverso hasta llegar al nodo objetivo, cuando este se vuelva rojo, eliminar como tal.

es si es un funcionamiento casi identico al de eliminacion de RB puro , pero con la peculiaridad N2SRB y la validez de la operacion de traslado(ver documento)
