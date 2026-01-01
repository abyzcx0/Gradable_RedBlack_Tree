Gradable Red-Black Tree (GRB) con Invariante N2SRB
​Este repositorio presenta el GRB (Gradable Red-Black Tree), una variante optimizada de los árboles Rojo-Negro. Su arquitectura se apoya en la restricción horizontal N2SRB (Not 2 Siblings Red-Black), permitiendo una gestión dinámica de la estructura mediante desplazamientos laterales de "carga roja" para igualar las alturas reales del árbol.
​1. La Restricción N2SRB
​A diferencia de un árbol Rojo-Negro convencional, el sistema N2SRB impone una regla estricta:
​Regla: Un nodo negro no puede tener dos hijos rojos simultáneamente.
​Ventaja: Esta restricción garantiza que, si un nodo tiene un hijo rojo, su hermano es obligatoriamente negro. Esto elimina la ambigüedad en el balanceo y habilita un "pasillo" para mover nodos rojos horizontalmente sin colisiones.
​2. El Concepto "Gradable" (Graduable)
​Un árbol es Gradable cuando puede ajustar su densidad sin alterar su validez. En el GRB, la Altura Negra (bh) se mantiene constante para asegurar un rendimiento de O(\log n), pero la Altura Real se "gradúa" (se estira o encoge) para optimizar el acceso a los datos.
​3. Operación de Gradación (Transferencia Lateral)
​Esta es la operación núcleo que permite que un nodo rojo "salte" de una rama a su hermana. Se compone de dos pasos atómicos:
​Flip de Color: Intercambio de color entre el padre negro y su hijo rojo.
​Rotación Inversa: Rotación en dirección opuesta al hijo original para preservar el orden BST y reubicar la jerarquía.
​Ejemplo de Optimización (Balanceo de Altura Real)
​Estado A: Desbalanceado (Ruta derecha más larga)
​En esta configuración, el nodo rojo P genera una ruta más profunda hacia sus descendientes.

              A [Negro]  <-- Raíz del subárbol
             /     \
           h1       P (Rojo)
                   / \
                  h2  B [Negro]
                     / \
                    h3  h4

​Altura Real a h1: 2 nodos.
​Altura Real a h3/h4: 4 nodos.
​Estado B: Balanceado (Tras la operación de Gradación)
​Al aplicar el Flip (A rojo, P negro) y rotar hacia la izquierda, el rojo se desplaza a la rama izquierda, igualando las profundidades.

            P [Negro]  <-- Nueva cabecera
           /      \
    (Rojo) A        B [Negro]
          / \      / \
         h1  h2   h3  h4

​Altura Real a h1/h2: 3 nodos.
​Altura Real a h3/h4: 3 nodos.

​Resultado: Las rutas se han igualado, optimizando el tiempo medio de búsqueda.
​4. Análisis de Consistencia
​Altura Negra: Se puede verificar matemáticamente que el número de nodos negros desde la raíz hasta h1, h2, h3 y h4 no cambia tras la operación.
​Localidad: La operación es local (O(1)). Dado que la raíz del subárbol comienza siendo negra y termina siendo negra, el resto del árbol superior no se ve afectado.
​Equivalencia: Bajo N2SRB, existen múltiples topologías válidas para los mismos datos; el GRB busca activamente la que minimiza la diferencia de altura real entre ramas.
​5. Conclusión
​El GRB con N2SRB transforma los nodos rojos de "errores estructurales" en "unidades de carga móviles". Esto permite que el árbol actúe como un sistema de vasos comunicantes, donde la profundidad fluye de las ramas saturadas hacia las ramas con mayor capacidad (nodos negros disponibles), logrando un balanceo más fino y proactivo que el modelo tradicional.
​Desarrollado como una alternativa de alta eficiencia para estructuras de datos dinámicas.
