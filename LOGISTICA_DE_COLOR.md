# Logística de Carga Roja y la "Estela de Color"

En el Gradable Red-Black Tree (GRB), la eliminación de un nodo negro no se trata como una reparación posterior, sino como un proceso de **gestión de suministros**.

## 1. El Concepto de Carga Roja
Consideramos al color **Rojo** como una unidad de "permiso de eliminación". Un nodo rojo puede ser eliminado físicamente sin afectar la altura negra ($bh$) del árbol. Por lo tanto, el objetivo del algoritmo es transportar un rojo hasta el nodo que se desea remover.

## 2. El Algoritmo de la Estela (The Red Wake)
A diferencia de los métodos tradicionales que suben desde la hoja, el GRB utiliza un descenso de **Pasada Única (Top-Down)**. Mientras el puntero de búsqueda desciende hacia el objetivo, va creando una "estela" de color rojo.

### Mecanismo de Transporte:
Si el siguiente nodo en la ruta de descenso es negro, el algoritmo lo "enrojece" proactivamente tomando el color de dos posibles fuentes:

1. **Transferencia Lateral (Préstamo):** Si el hermano del nodo actual tiene un hijo rojo, se realiza una rotación para trasladar esa carga roja a nuestra ruta. Es una operación $O(1)$ de punteros.
2. **Descarga Vertical (Flip Inverso):** Si no hay rojos laterales pero el padre es rojo, se realiza un *Flip Inverso*. El padre cede su rojez a ambos hijos. Debido a la invariante **N2SRB**, esta descarga es intrínsecamente segura y no genera colisiones en la rama vecina.

## 3. Ventajas de la Pasada Única
- **Cero Backtracking:** No se requiere una pila (*stack*) para rebalancear el árbol al subir. Una vez que el nodo es eliminado, el proceso termina.
- **Predictibilidad de Memoria:** Al solo bajar, los nodos se mantienen en la caché L1/L2 del procesador, optimizando el rendimiento en hardware moderno.
- **Simplicidad:** Se reduce la eliminación a una sola regla: "Si vas a bajar a un nodo negro, asegúrate de traer un rojo contigo".

## 4. El Caso de la Raíz
Si el árbol está "seco" (no hay rojos disponibles en la ruta), la demanda de color escala hasta la raíz. La raíz genera el rojo inicial (reduciendo la altura negra global de forma uniforme) y este se desplaza hacia abajo mediante la estela de flips inversos.
