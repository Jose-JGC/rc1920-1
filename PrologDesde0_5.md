# Prolog desde 0
## Árboles binarios balanceados

Vamos a aprender a definir árboles binarios balanceados trabajando el pensamiento declarativo y la idea del principio de inducción. 
Con este ejercicio, aprenderemos a identificar si un árbol binario es balanceado o no.
Nos apoyaremos en el siguiente video: [2.10 Programación Lógica con Prolog: Árboles balanceados (Nueva versión 4K!)🌳🌳⚖
](https://www.youtube.com/watch?v=JkBlucdXFYg&list=PL_d-XKRO_5G_4k1l6Dz81JhyLnyXRkEsP&index=20)

Para ello, definiremos los predicados **balanceado** y **altura**, siendo este último utilizado en el de balanceado.
Vamos a ver **balanceado**.

Un árbol es balanceado si, **para todo nodo**, la diferencia entre la altura del hijo Izquierda y la altura del hijo derecha es como máximo 1 en valor absoluto. O lo que es lo mismo, si la altura del hijo izquierdo y el derecho se diferencian como máximo en 1 y el árbol de la izquierda y de la derecha es balanceado.
Por definición, el árbol nulo es balanceado.

Para comprobar si el árbol es balanceado usaremos el predicado **balanceado**
```
/*
balanceado(+Arbol_Binario)
  es cierto si, para todo nodo, la diferencia entre
  la altura del Hijo Izquierda y la altura del 
  Hijo derecha es como máximo 1 en valor absoluto.
*/
```
Pasamos a implementarlo. utilizando el **Principio de Inducción**. Éste nos dice:

1. P(n0) 
Necesitamos que la propiedad sea cierta para el árbol más pequeño. En este caso el más pequeño es el árbol nulo. 
El árbol nulo es balanceado y lo escribiremos con el siguiente predicado:
balanceado(nil).
Esto nos sirve para identificar cuándo un árbol es nulo.

2. ∀ n > no, P(n-1)-> P(n)
La segunda parte del principio de inducción nos dice que tenemos que preguntarle al problema quitando un elemento. 
En este caso lo aplicamos a la izquierda y a la derecha y lo escribimos así:

Definimos un árbol 'a' sin etiqueta, que indicamos con una variable anónima '_', y sus hijos, el izquierdo y el derecho.
```
  balanceado(a(_, HI, HD)):-
```
y comprobamos las alturas
```
  altura(HI, AI),
  altura(HD, AD),
  ```
despúes se implementará el predicado **altura**.

Ahora comprobaremos que el valor abosluto de la diferencia de altura entre el hijo de la izquierda
y el de la derecha sea menor o igual que uno.
```
Abs_dif is abs(Dif),
  Abs_dif =< 1,
```

A continuación comprobamos que sea balanceado el hijo de la izquierda y el de la derecha
```
balanceado(HI),
  balanceado(HD).
```
que permite comprobar las diferencias entre las alturas para todo el árbol.

Nos queda implementar el predicado **altura** del árbol, como indicamos anteriormente.
```
/* altura(+Arbol_binario, -Altura)
      es cierto si Altura unifica con la
   altura de Arbol_binario.
*/  
```
Volvemos a utilizar el principio de inducción.
```
P(no) 
```
Necesitamos la altura del árbol más pequeño, la del árbol nulo, que será cero.
```
altura(nil,0).
```
```
∀ n > no, P(n-1)-> P(n)
```
En la segunda parte del principio de inducción no vamos a quitar uno, lo que haremos es preguntar a la izquierda y a la derecha.
El problema más pequeño lo hacemos quitando todos los elementos de una parte primero, de la izquierda, y después de la derecha.

Definimos el predicado altura del árbol, en el que no pondremos etiqueta, definimos los hijos y calculamos las dos alturas. La altura del árbol será el máximo de las dos alturas 
mas uno, para contar la raíz del árbol. 
```
  altura(a(_, HI, HD), R):-
  altura(HI, AI),
  altura(HD, AD),
  A is max(AI, AD),
  R is A+1.
```
El código quedaría ya de la siguiente forma:
```
/*
balanceado(+Arbol_Binario)
  es cierto si, para todo nodo, la diferencia entre
  la altura del Hijo Izquierda y la altura del 
  Hijo derecha es como máximo 1 en valor absoluto.
*/

balanceado(nil).
balanceado(a(_, HI, HD)):-
  altura(HI, AI),
  altura(HD, AD),
  Dif is AI-AD,
  Abs_dif is abs(Dif),
  Abs_dif =< 1,
  balanceado(HI),
  balanceado(HD).

/* altura(+Arbol_binario, -Altura)
      es cierto si Altura unifica con la
   altura de Arbol_binario.
*/  
altura(nil,0).
altura(a(_, HI, HD), R):-
  altura(HI, AI),
  altura(HD, AD),
  A is max(AI, AD),
  R is A+1.
```
  
Probaremos la implentación con los siguientes árboles:
```
   1) 1         2) 1
     / \          / \
    2   3	 2   5
                / \
	       3   4
```

No balanceados
```
   3) 1         4) 1
     /            / \
    2    	 2   5
   / \          /     \
  3   4        3       6  
       \      /         \
        5    4           7
```
que se definirían de la siguiente forma:
```
1)arbol1(a(1,a(2,nil,nil),a(3,nil,nil))).  
2)arbol2(a(1,a(2,a(3,nil,nil),a(4,nil,nil)),a(5,nil,nil))).
3)arbol3(a(1,a(2,a(3,nil,nil),a(4,nil,a(5,nil,nil))),nil)).
4)arbol4(a(1,a(2,a(3,a(4,nil,nil), nil),nil), a(5,nil,a(6,nil,a(7,nil,nil))))).
?- arbol1(A), balanceado(A)
```

 
