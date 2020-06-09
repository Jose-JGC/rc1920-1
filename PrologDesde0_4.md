# Prolog desde 0
## Árboles Binarios

En el día de hoy aprenderemos a hacer árboles en prolog y recorrerlos. Para ello nos apoyaremos en el siguiente video: [RC#6 PROLOG QUICKSORT (II) + ARBOLES BINARIOS](https://youtu.be/Acz_ynNrIS8?t=1383)
a partir del minuto indicado en el propio enlace. En él se explican los recorridos en árboles binarios.

Para empezar definiremos la estructura árbol en prolog.
```
/*
  Arboles Binarios

  nil
  a(Etiqueta, HijoIzquierda, HijoDerecha)
  
  arbol1
      1
     / \
    2   3	  

arbol2
       1
	    / \  
     /   \
    2     3	  
   / \   / \
  4   5 6   7
  
arbol3  
       +
	    / \  
     /   \
    *     /	  
   / \   / \
  4   5 6   7
*/ 
```


Mediante los hechos siguientes definiremos los 3 árboles.
```
arbol1( a(1, a(2, nil, nil), a(3, nil, nil))).
arbol2(a(1, a(2, a(4,nil,nil), a(5,nil,nil)), a(3, a(6,nil,nil),a(7,nil,nil)))).
arbol3(a('+', a('*', a(4,nil,nil), a(5,nil,nil)), a('/', a(6,nil,nil),a(7,nil,nil)))).
```
- Donde el primer elemento es la *raíz* del árbol y los otros dos son las *hojas*.
- Donde nil es lo equivalente a NULL en otros lenguajes. Significa que ahi no hay nodo.

Después de esto, crearemos el predicado preorden, que mostrará el arbol en ese orden.
```
/*
preorden(Arbol, Lista)
 es cierto si Lista unifica con el recorrido 
 en preorden de Arbol.
 
 raiz, hi, hd
*/
```

Primero usaremos como caso base la siguiente afirmación:
```
preorden(nil, []).
```
Ya que el árbol más pequeño que podemos mostrar es un arbol vacío.

En caso de que el árbol no sea vacío, usaremos la siguiente:
```
preorden(a(E,HI,HD), U):-
  preorden(HI,RI),
  preorden(HD,RD),
  append([E|RI],RD,U).
```
