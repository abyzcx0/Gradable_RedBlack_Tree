# Gradación Estructural: Equilibrio de Altura Real

El término **Gradable (Graduable)** en el GRB se refiere a la capacidad única del árbol para ajustar su "densidad" u "holgura" sin violar las propiedades de un árbol Rojo-Negro.

## 1. Altura Negra vs. Altura Real
- **Altura Negra (bh):** Es la medida de balanceo teórico. Garantiza que el árbol sea O(log n).
- **Altura Real (h):** Es la profundidad física de los nodos. En un RB tradicional, esta altura puede variar significativamente entre ramas, siempre que el bh sea el mismo.

El GRB utiliza los nodos rojos como **contrapesos móviles** para minimizar la diferencia entre las alturas reales de las ramas hermanas.

## 2. El Principio de los Vasos Comunicantes
Gracias a la invariante **N2SRB**, el árbol puede detectar cuando una rama es físicamente más profunda que su hermana. Si la rama profunda posee un nodo rojo, el árbol realiza una **Operación de Gradación**:

1. **Detección:** Se identifica que una ruta tiene un nodo rojo que "estira" la rama innecesariamente.
2. **Transferencia:** Mediante una rotación y un intercambio de color, el nodo rojo se "mueve" a la rama hermana que era más corta.
3. **Resultado:** La altura negra permanece intacta, pero las alturas reales se igualan.

## 3. Optimización del Tiempo de Búsqueda
Un árbol RB estándar se conforma con ser "suficientemente bueno" (bh balanceado). El **GRB** es más ambicioso:
Al "graduar" las alturas reales, el GRB reduce el **tiempo promedio de búsqueda (ASL - Average Search Length)**. El árbol actúa como un sistema de fluidos donde la profundidad fluye desde las zonas saturadas hacia las zonas con mayor capacidad (nodos negros disponibles).

## 4. Estabilidad del Sistema
Esta operación es:
- **Local:** Solo afecta al padre, al hijo rojo y al hermano negro.
- **Atómica:** Se realiza en tiempo constante O(1).
- **Segura:** Al terminar, el nodo que era raíz del subárbol sigue siendo negro, lo que garantiza que no hay efectos secundarios hacia los niveles superiores del árbol.
