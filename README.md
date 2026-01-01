# Gradable Red-Black Tree (GRB) con Invariante N2SRB

Este repositorio presenta el **GRB (Gradable Red-Black Tree)**, una arquitectura avanzada de árboles binarios de búsqueda balanceados que optimiza tanto la estructura teórica como el rendimiento en hardware moderno.

## 🚀 La Innovación: De Reacción a Gestión
A diferencia de los árboles Rojo-Negro (RB) convencionales que reaccionan a los desbalances mediante reglas complejas de post-procesamiento, el GRB utiliza un modelo de **Logística de Carga Roja** proactivo.

### Pilares del Modelo
1. **[Invariante N2SRB](./INVARIANTE_N2SRB.md):** (Not 2 Siblings Red-Black). Una restricción que prohíbe hermanos rojos, eliminando la ambigüedad y permitiendo descensos de pasada única (*one-pass*).
2. **[Estela de Color](./LOGISTICA_DE_COLOR.md):** Un mecanismo que transporta nodos rojos proactivamente hacia el punto de eliminación, eliminando el uso de pilas (*stacks*) y el retroceso (*backtracking*).
3. **[Gradación Estructural](./GRADACION_ESTRUCTURAL.md):** La capacidad de equilibrar la **Altura Real** (distancia física) moviendo nodos rojos como contrapesos, reduciendo el tiempo promedio de búsqueda.

## 📊 Ventajas Comparativas

| Característica | RB Tradicional | GRB (N2SRB) |
| :--- | :--- | :--- |
| **Complejidad de Borrado** | 6 casos asimétricos | 2 operaciones lógicas |
| **Recorrido** | Doble (Bajar y Subir) | **Única (Solo bajar)** |
| **Uso de Memoria Adicional** | $O(\log n)$ (Pila) | **$O(1)$ (In-place)** |
| **Eficiencia de Caché** | Media | **Máxima (Top-Down)** |

## 🛠️ Algoritmos Principales
Puedes consultar la lógica detallada en nuestro archivo de **[Algoritmos de Operación Única](./ALGORITMOS_GRB.md)**, donde se detalla:
- El **Split Preventivo** para inserciones.
- La **Transferencia Lateral** y
