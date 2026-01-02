Sea un arbol RB binario f(1) consistente de un solo nodo. por tanto, el arbol solo consta de la raiz(que es negra por defecto).

Sea otro arbol RB binario f(2) consistente en una raiz y un hijo, dos nodos. por tanto el arbol solo consta de la raiz negra y el hijo rojo(para mantener altura negra valida). 

Sea f(3) el tercer arbol RB, de la siguiente manera:

Una raiz(por defecto es negra) que tiene de subarboles f2 y f1 como hijos de la raiz.

sea un arbol f'(n) que consta de la misma estructura que f(n), excepto que su raiz es roja, y solo aplica como estructura de subarbol, no como RB valido. 

Sea f(4) el cuarto arbol RB, que consta de una raiz con hijos subarboles f'(3) y f(2)

dado que f(3) consta de raiz y subarboles f(2) y f(1) que son de raiz negra, f'(3) con raiz roja no genera problemas con sus hijos que son las raices de f(2) y f(1). 

Sea f(5) el quinto arbol RB, que consta de una raiz con subarboles f(4) y f(3)

Sea f(6), raiz + f'(5) + f(4). 

f(7) = raiz + f(6) + f(5)
f(8) = raiz + f'(7) + f(6)
f(9) = ... 

y en general:
f(n) = raiz + f(n-1) + f(n-2); si n impar. 
f(n) = raiz + f'(n-1) + f(n-2); si n par.

Bajo esta generacion, se establece dos puntos:

A) El arbol es RB valido, acotado a una diferencia de altura real de 1 entre ramas hermanas(es un avl en el caso considerado como de peor balance posible); es un arbol binario fibonacci.

B) se da lugar a una estructura donde solo existe rojos aislados(no tiene hermanos ambos rojos), con desbalance arbitrario entre ramas en lo mas posible sin romper RB con la menor cantidad de nodos usados.

