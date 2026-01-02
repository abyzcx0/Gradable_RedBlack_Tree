En un RB, para corregir una violación Rojo-Rojo, la clave es el color del Tío:
​1. Si el Tío es ROJO (Recoloreo)
​Acción: Padre y Tío pasan a Negro. Abuelo pasa a Rojo.
​Siguiente paso: Repetir el análisis desde el Abuelo (el problema sube).
​2. Si el Tío es NEGRO (Rotación)
​Depende de la forma que formen el Nodo (N), Padre (P) y Abuelo (G):
​Triángulo (Zig-Zag): Rotar el Padre para convertirlo en una línea.
​Línea: 1. Rotar el Abuelo.
2. El Padre pasa a Negro y el Abuelo a Rojo.
3. Fin: El árbol queda balanceado.

Pero en caso de N2SRB se da dos situaciones particulares:

1) no hay arreglo particular con tio rojo: eso debido a la regla de no hermanos rojos, el padre siendo rojo anula la presencia del tio rojo (ya ha sido arreglado previamente).
2) con la consideracion anterior, se da el caso del tio negro, pero este caso al final, genera dos hermanos rojos,los cuales por logica del arbol N2SRB tambien son reparados subiendo el problema(flip)

Los puntos 1 y 2 implican que el algoritmo de coreccion desencadenan cambios hasta que se encuentre un punto estable o la raiz, por punto estable se toma que la correccion y generación de rojo superior llega a un lugar donde no tiene ni padre ni hermano rojo(rojo aislado) o en su defecto hasta convertir la raiz en rojo, y luego por propiedad la raiz recupera su negrura.

considerese que la ejecucion es mas sencilla y mecanica: rojorojo padre/hijo es rotacion y flip, rojorojo hermanos es solo flip.

el arbol N2SRB en si, reduce la cantidad de rojos a encontrarse, siendo mas probable encontrar un punto estable antes que la raiz.
