# La Invariante N2SRB (Not 2 Siblings Red-Black)

El fundamento del **Gradable Red-Black Tree (GRB)** reside en una restricción estructural más estricta que la del árbol Rojo-Negro (RB) convencional.

## 1. Definición de la Regla
En un árbol balanceado bajo la norma N2SRB, se añade la siguiente condición de integridad:
> **"Ningún nodo negro puede poseer dos hijos rojos simultáneamente."**

### Consecuencia Lógica
Si un nodo $P$ tiene un hijo rojo $A$, su hermano $B$ es **obligatoriamente negro**. 

## 2. Propósito de la Invariante
Esta restricción elimina la ambigüedad estructural. En un árbol RB clásico, un nodo negro con dos hijos rojos representa un nodo 4 del modelo 2-3-4. En el modelo **GRB**, los nodos 4 se gestionan de forma proactiva (mediante Flips o Rotaciones) para transformarlos en configuraciones que permitan el flujo de color.

## 3. Ventajas Arquitectónicas
1. **Pasillos de Transferencia:** Al garantizar que siempre hay un hermano negro, se habilitan "espacios vacíos" para mover nodos rojos horizontalmente (Préstamo Lateral) sin generar colisiones Rojo-Rojo.
2. **Eliminación de Ambigüedad:** Durante el descenso (Top-Down), el algoritmo no necesita evaluar múltiples casos complejos; la configuración de los hermanos dicta una única acción posible.
3. **Optimización de Caché:** Facilita la implementación de algoritmos de pasada única (*one-pass*), eliminando la necesidad de retroceso (*backtracking*) y el uso de pilas en memoria.

## 4. Estabilidad Estructural
A diferencia de variantes como el LLRB (Left-Leaning Red-Black), el N2SRB no fuerza una inclinación artificial. El rojo puede estar a la izquierda o a la derecha, siempre que sea hijo único de su padre negro, lo que reduce significativamente el número de rotaciones necesarias para mantener el balanceo.
