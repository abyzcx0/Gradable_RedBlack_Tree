# Algoritmos de Operación Única (Top-Down)

El GRB elimina la necesidad de subir por el árbol (backtracking). Todo se resuelve en el descenso.

## 1. Inserción con Split Preventivo (N2SRB)
Para mantener la invariante, antes de insertar, "limpiamos" el camino de nodos que podrían generar dos hijos rojos.

FUNCION insertar_grb(raíz, clave):
    SI raíz es NEGRO y ambos hijos son ROJOS:
        # Flip Preventivo (Promoción)
        raíz = ROJO, hijos = NEGRO
    
    # ... Descenso BST estándar ...
    # Si se genera un rojo-rojo, se corrige con rotación simple/doble
    # y se asegura que el resultado final respete N2SRB.

## 2. Eliminación con Estela de Color (The Red Wake)
Este es el algoritmo núcleo para extraer un nodo sin desbalancear el árbol.

FUNCION eliminar_grb(nodo_actual, clave):
    1. Si el objetivo es NEGRO:
       A. Intentar TRANSFERENCIA LATERAL:
          SI hermano tiene hijo ROJO:
              Rotar carga roja hacia el camino actual.
              Recolorear para que el nuevo 'hijo' sea ROJO.
       
       B. Si no hay transferencia, intentar DESCARGA VERTICAL:
          SI padre es ROJO:
              Realizar Flip Inverso (Padre Negro, Hijos Rojos).
       
       C. Si todos son negros:
          Escalar demanda al nivel superior (Recursión).

    2. Si el nodo_actual es el objetivo:
       - Si es Hoja Roja: Eliminar directamente.
       - Si tiene hijos: Intercambiar con sucesor y seguir la estela.

## 3. Operación de Gradación (Rebalanceo de Altura Real)
Se puede disparar durante búsquedas o inserciones para optimizar el árbol.

FUNCION graduar_subarbol(padre):
    SI h(hijo_izq) > h(hijo_der) + 1 Y hijo_izq es ROJO:
        Rotar_Derecha(padre)
        Intercambiar Colores(nuevo_padre, antiguo_padre)
