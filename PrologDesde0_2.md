# Prolog desde 0

## Concatenar listas

En el día de hoy, aprendermos a concatenar dos listas en prolog. Para ello nos basaremos en este [video.]( https://www.youtube.com/watch?v=JqQNd6uFuLs)
Despues de ver el video, comenzaremos a explicar como funciona el predicado implementado con la ayuda del **ejercicio propuesto:**

```
/* concatenar (?Lista1, ?Lista2, ?Resultado)
	es cierto si resultado unifica con una lista
	que contiene los elementos de Lista1,
	seguidos de los elementos de Lista2.
*/

concatenar([], Lista2, Lista2). //si se concatena una lista vacia con otra lista, el resultado sera esa misma lista.
concatenar([Cab|Resto], Lista2, [Cab|R]) :- 
	concatenar(Resto, Lista2,R).
```

Como podemos observar, este problema ha sido resuelto con el [principio de inducción](https://github.com/Jose-JGC/rc1920-1/blob/master/PrologDesde0.md), ya explicado anteriormente, que es el pilar fundamental
para entender la programación en Prolog.

Nuestro *P(n0)* seria el primer predicado ```concatenar([], Lista2, Lista2). ```

Nuestro *∀n>n0, P(n-1)->P(n)* sería el segundo predicado 
```
concatenar([Cab|Resto], Lista2, [Cab|R]) :- 
	concatenar(Resto, Lista2,R).	
```

Como en el predicado inferior R contendrá la concatenacion del resto y lista2, nos haremos la siguiente [pregunta](https://youtu.be/JqQNd6uFuLs?t=286):
>¿Qué tengo que hacerle a esta R resultado de la lista con un elemento menos para que el resultado de la lista completa sea verdad?

En este caso, tendremos que añadirle la cabeza al principio.

Hecho esto el ejercicio queda resuelto. En resumen, tenemos un caso base de concatenación y otro predicado que indica la relación que hay entre el caso con elementos R y el caso con uno menos.

Conclusion: Hoy hemos aprendido a concatenar dos listas usando prolog. Como podemos observar con solo aplicar el principio de inducción el problema se resuelve casi solo.

Lo más **importante** para poder aprender esta nueva forma de programar es entendiendo esto. **Siempre debemos ver las relaciones existentes entre nuestras variables y ver el resultado como algo estático.**
Debemos para ello confiar en el principio de inducción. 

Si todavía **no** te convence el principio de inducción, te planteo este **ejercicio para que lo intentes resolver a tu manera**.
Si lo consigues no necesitas saber nada más. Si no lo consigues deberias seguir con esta guia.

```
/*
  comprime(+Lista, +Resultado)
    
	 Es cierto si Resultado unifica con una lista de la siguiente forma:
     
     comprime([1,2,2,2,3,3,4,5,5,5], Resultado)
     Resultado=[(1,1), (2,3), (3,2), (4,1), (5,3)]
*/
```

