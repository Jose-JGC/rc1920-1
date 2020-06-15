# Prolog desde 0
## Árboles Genéricos. Cuenta nodos
Un árbol genérico en Prolog, a diferencia del árbol binario, no tiene el equivalente al árbol nulo; el árbol más pequeño es el árbol que tiene un único nodo.
Se representa de la siguiente forma:
- Árbol de un sólo nodo
  1       a(1,[])
- Árbol con dos hijos:  
    1
   / \    a(1,[a(2,[]),a(3,[])])
  2   3
- Árbol con tres hijos: 
    1
   /|\    a(1,[a(2,[]),a(3,[]),a(4,[])])
  2 3 4

Vamos a resolver el predicado **cuenta_nodos**, que cuenta el número de nodos que tiene un árbol genérico.
```
/* cuenta_nodos(+A, -N)
   es cierto si N unifica con el número de
   nodos del árbol genérico A
*/
```
El árbol más pequeño es aquel que tiene un único nodo. Para los ejercicios de árboles genéricos vamos a utilizar un truco que nos facilita la implementación y consiste en trabajar, por un lado con la estructura árbol y por otro con la lista de hijos. Así definimos el predicado como: 
```
cuenta_nodos(a(_, Lista_hijos), R2):-
```
Vamos a crear un predicado sobre la lista de hijos, obtendremos el resultado y le sumaremos uno. R2 será el resultado de la cuenta de todos los nodos del árbol genérico.
```
cuenta_nodos(Lista_hijos, R),
R2 is R + 1.
```
Ahora implementamos un *cuenta_nodos* para una lista de árboles, siguiendo la estructura que hemos visto anteriormente para listas. Para una lista de árboles vacía, tendrá cero nodos:
```
cuenta_nodos([], 0).
```
Para una lista de árbol que tiene una cabeza y un resto, 
```
cuenta_nodos([Ca|Resto], R):-
```
contaremos los nodos de la cabeza, que es un árbol, y contaremos los nodos del resto, que es una lista de árboles, que unificará con lista vacía o con la otra parte, y sumaremos las dos cantidades:
```
  cuenta_nodos(Ca, Rca),  
  cuenta_nodos(Resto, RResto),
  R is RCa + RResto.
```
siendo R el resultado total de nuestro predicado.

El predicado **cuenta_nodos** queda finalmente implementado con el siguiente código:
```
cuenta_nodos(a(_, Lista_hijos), R2):-
cuenta_nodos(Lista_hijos, R),
R2 is R + 1.
cuenta_nodos([], 0).
cuenta_nodos([Ca|Resto], R):-
cuenta_nodos(Ca, RCa),  
  cuenta_nodos(Resto, RResto),
  R is RCa + RResto.
```
Nos apoyamos en el video https://www.youtube.com/watch?v=LQ4sx2hqZKw&list=PL_d-XKRO_5G_4k1l6Dz81JhyLnyXRkEsP&index=36