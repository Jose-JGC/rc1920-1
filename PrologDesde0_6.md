# Prolog desde 0
## Árboles binarios. Lista de hojas

Continuando con los ejercicios de árboles binarios, vamos a implementar el predicado **lista_hojas**, que recibe un árbol binario 
y devuelve una lista de todas sus hojas:
```
/* 
  lista_hojas(Arbol, Lista)
  es cierto si Lista unifica con 
  una lista que contiene todas las hojas
  del árbol
*/
```
Por ejemplo:
```
     1
    / \
   2   5
  / \ 
 3   4 
```
Un resultado podría ser: [3,4,5], que son las etiquetas de los nodos que están en las hojas.

Nos apoyaremos en este vídeo  [009 Prolog: Árboles binarios. Lista de hojas](https://www.youtube.com/watch?v=5OQ3uL4uJPg&list=PL_d-XKRO_5G_4k1l6Dz81JhyLnyXRkEsP&index=34).

Vamos a ver cómo se implementa este predicado. Como siempre, aplicamos el principio de inducción. 
```
	% p(n-1) -> p(n)
	% P(N) :- N2 is N-1, P(N2).
```
En el caso del árbol más pequeño será una lista vacía:
```
lista_hojas(nil, []).
```

A continuación, tenemos que detectar las hojas. Para ello comprobamos que el árbol tenga una etiqueta y que no tenga ningún hijo ni a la derecha ni a la izquierda, esto es:
```
lista_hojas(a(E, nil, nil), [E]).
```

Ahora hay que detectar los casos en los que no sean hojas e implementarlos. Se han de tener en cuenta todas las opciones:

- Dos árboles no nulos
Definimos el árbol, sin etiqueta porque no se va a usar, con hijo a la izquierda e hijo a la derecha.
```
lista_hojas(a(_, HI, HD), R):-
```
Haremos una llamada recursiva para buscar hijos a la derecha y a la izquierda
```
lista_hojas(HI, LI),
lista_hojas(HD, LD), 
```
y hay que asugurarse de que los hijos no sean nulos porque no funcionaria.
```
HI \= nil, HD \= nil,
```
y concatenamos las dos listas en una lista R.
```
append(LI, LD, R).
```
- HD nulo HI no nulo

Sería el caso de un árbol de este tipo
```
   1
    \
     2
```

En este caso, se hace una llamada recursiva con el árbol de la derecha y el resultado del árbol completo será la lista de la derecha
```
lista_hojas(a(_, nil, HD), LD):-
    HD \= nil,
    lista_hojas(HD, LD).
```
- HI nulo HD no nulo
Será del tipo:
   1
  /
 2

Se implementa una llamada recursiva con hijo izquierda y el resultado será la lista de la izquierda.
```
lista_hojas(a(_, HI, nil), LI):-
    HI \= nil,
    lista_hojas(HI, LI).
```

El código completo que se ha implementado para el predicado que nos muestra la lista de todas las hojas de un árbol binario es:
```
  lista_hojas(nil, []).
  lista_hojas(a(E, nil, nil), [E]).
  lista_hojas(a(_, HI, HD), R):-
    HI \= nil, HD \= nil,
    lista_hojas(HI, LI),
    lista_hojas(HD, LD),	
    append(LI, LD, R).
  lista_hojas(a(_, nil, HD), LD):-
    HD \= nil,
    lista_hojas(HD, LD).
  lista_hojas(a(_, HI, nil), LI):-
    HI \= nil,
    lista_hojas(HI, LI).
```
