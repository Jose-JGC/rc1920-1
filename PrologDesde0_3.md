# Prolog desde 0
## Comprimir listas

En el día de hoy aprenderemos a resolver el ejercicio que quedo planteado en la anterior [entrega](https://github.com/Jose-JGC/rc1920-1/blob/master/PrologDesde0_2.md) .
Si todavía no has intentado resolverlo a tu manera, te insisto en que lo intentes, ya que es un muy buen ejercicio para darse cuenta de que sin aplicar el principio de inducción
y programar siguiendo la ejecución del código es mucho más dificil conseguir resolverlo.

Nos apoyaremos en este video [006 Prolog: Listas. Comprime](https://www.youtube.com/watch?v=nJ9fRHzsTuk&list=PL_d-XKRO_5G_4k1l6Dz81JhyLnyXRkEsP&index=31) .
En enunciado es el siguiente:
```
/*
  comprime(+Lista, +Resultado)
    
	 Es cierto si Resultado unifica con una lista de la siguiente forma:
     
     comprime([1,2,2,2,3,3,4,5,5,5], Resultado)
     Resultado=[(1,1), (2,3), (3,2), (4,1), (5,3)]
*/
```
De tal forma que el predicado resuelva una lista de números obteniendo como resultado los números que aparecen y a su lado las veces que lo hacen.

Para resolver esto, como ya se ha mencionado antes, es muy importante el uso del principio de inducción. Recordamos como quedaría representado en prolog: 
```
	% p(n-1) -> p(n)
	% P(N) :- N2 is N-1, P(N2).
```
Recordado esto ya podemos empezar a resolver el ejercicio.

Comenzamos por definir las ** reglas o hechos ** bases para comprime. Para ello nos hacemos la siguiente pregunta: 
* ¿Cuál es la lista más pequeña que podemos comprimir? *
Dado que podemos comprimir una lista vacia sin elementos, usaremos ese caso como base.
```
comprime([], []).
```
Pero no solo vale con este caso. Más adelante comentaré el por qué, pero de momento seguimos así.

Aqui tendremos el caso en que el primer elemento y el segundo no sean iguales.
```
comprime([Cab1, Cab2|Resto], ) :-
	Cab1 \= Cab2,
    comprime([Cab2|Resto], R).
```
Dado este ejemplo: [a, b, b, b, c, c] si quitamos el primer elemento de la lista tendremos en R -> [(b,3), (c,2)]. Luego nos preguntaremos: * ¿Qué tengo que hacerle a este caso R para obtener la lista completa comprimida? *
En este ejemplo seria -> [(a,1), (b,3), (c,2)]. Observando las diferencias, podemos notar que lo que le falta a R para que este completa sería el elemento (a,1).
Como el primer elemento es 'a' que es la Cabeza1 y solo hay una (ya que es el caso en que son diferentes los dos primeros elementos), lo que habría que hacer sería concatenar el elemento formado por (Cab1,1) con la lista R.
Luego lo que tendríamos en el hueco en blanco sería ** [(Cab1, 1)|R] ** :
```
comprime([Cab1, Cab2|Resto], [(Cab1,1)|R] ):-
	Cab1 \= Cab2,
    comprime([Cab2|Resto], R).
```
De esta forma quedaría terminado el caso en el que el primero y el segundo fueran distintos.

* ¿Qué sucedería si el primer y segundo elemento fueran iguales? *
```
comprime([Cab, Cab|Resto], ):-
    comprime([Cab|Resto], [(Cab,N)|R]),
	N2 is N + 1.
```
Siguiendo el ejemplo anterior, si tuviesemos la lista [(a,a,b,b,b,c,c)] el resultado sería [(a,2), (b,3), (c,2)].
si tuviesemos la lista [(a,b,b,b,c,c)] R sería [(a,1), (b,3), (c,2)]. 
* ¿En qué se diferencian? *
Se diferencian en que el primer elemento tiene una unidad más en la primera lista. Por lo tanto para obtener el resultado tenemos que sumarle 1 al número del priemer elemento de R.
Por tanto el hueco en blanco sería: ** [(Cab,N2)|R] ** ya que N2 es N + 1.
```
comprime([Cab, Cab|Resto], [(Cab,N2)|R]):-
    comprime([Cab|Resto], [(Cab,N)|R]),
	N2 is N + 1.
```

* ¿Habríamos acabado? *
No, pues como bien dije antes queda un caso base mujy importante. No hemos tenido en cuenta el caso en el que la Lista solo tiene un elemento. Si no implermentamos este caso base el predicado no funcionaria.
```
comprime([E], [(E,1)]).
```

Hecho esto tendriamos ya todos los casos que nuestro predicado necesita para su correcto funcionamiento.
En la siguiente publicación aprenderemos ** árboles **. ¡No te lo puedes perder!