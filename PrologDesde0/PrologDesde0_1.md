					APRENDIENDO PROLOG DESDE 0
					
Jose Joaquín González Colchero

DÍA 1.
Hoy es el primer dia de aprendizaje de prolog desde 0. Aprenderemos el principio de inducción, ya que es el concepto más basico y el pilar de la programación en prolog.
Para aprender este concepto, visualizaremos el siguiente video: 2.01 Programación lógica con Prolog: [Principio de inducción (Nueva versión 4K!)] (https://www.youtube.com/watch?v=31ypX6BVq2E).
Despues de ver el video, realizaremos un ejercicio y analizaremos su funcionamiento.
**Principio de inducción**
Es un principio que se utiliza mucho en matématicas para probar teoremas. La idea es muy sencilla y necesitamos de un conjunto ordenado S donde tendremos n elementos: *n0, n1, n2, ..., nN*.
Aplicado a los número naturales, *n0* sería el *1*, *n1* el *2* y así sucesivamente. Para listas, el primer elemento será la lista vacía *[]*, el segundo puede ser una lista con un elemento *[a]* y así sucesivamente.Y para árboles será el primero el árbol vacío *nil*, soguiente con un nodo y así sucesivamente.
¿Cómo funciona el principio de inducción?. El principio tiene dos partes:
1) Hay que probar una propiedad para todos los elementos del conjunto. Necesitamos que la propiedad sea cierta para el primer elemento *n0*, ésto es:
```P es cierta para n0
```
2) Y para los sucesivos, si la propiedad es cierta para *n-1* se puede asegurar que también lo será para *n*.
```
   ∀ n > no, P(n-1)-> P(n)
```
Ahora vamos a ver un ejemplo con los números naturales al que aplicaremos el principio de inducción. 
```
/* 
natural(+N)
es cierto si N es natural
*/
```
Para implementar este predicado **natural**, lo primero que se necesita es que la propiedad sea cierta para el primer número natural, ésto es el *1* que en Prolog es:
```
   natural(1).
```
Y a continuación, hay que aplicar la parte dos del principio pero antes veamos cómo se hace la implicación de la forma *a->b*. En Prolog se escribe *b:-a.*, siendo el antecedente *a* y el consecuente *n*. Así, tenemos:
```                               
   natural(N):- N > 1, N2 is N-1, natural(N2).
```

Después de ver cómo funciona el principio de inducción con la implementación de este predicado, vamos a ver cómo trabaja Prolog para llegar a la solución de **natural(5)**. Veremos si es verdad aplicando las dos reglas:
```
   1) natural(1).
   2) natural(N):- N > 1, N2 is N-1, natural(N2).
```
Cogemos el *5*, no podemos aplicar la primera regla y pasamos entonces a la segunda. ¿Es *5>1*? Entonces aplicamos esta parte *N2 is N-1, natural(N)* que sería comprobar si **natural(4)** es cierto para que así lo sea también *natural(5)*. Ahora aplicamos lo mismo con el *4* y así sucesivamente hasta llegar al *1*:
```
   5 → 4 → 3 → 2 → 1
```
Cuando llegamos al *1* podemos aplicar la primera regla y es cierta porque hemos llegado al primer elemento, por lo que aplicando la segunda regla nos dice que el *2* también lo será porque lo es el anterior, el *1* , y así sucesivamente llegamos hasta el *5* confirmando de esta forma que también es natural:
```
  5 → 4 → 3 → 2 → 1
  si← si← si← si← si   
```
Ahora vamos a ver qué sucede si preguntamos por un número negativo, por ejemplo **natural(-3)**. No es el primero, no es el *1*, pero tampoco es mayor que el primero, por tanto no tenemos una regla que dé respuesta a este valor y en este caso Prolog, aplicando la *hipótesis del mundo cerrado*, nos devuelve que es falso directamente.

Concluyendo, hemos visto cómo se aplica el principio de inducción para resolver los ejercicios que se van a resolver siempre de la misma forma, preguntando al caso anterior y llegando hasta el caso *n0* y a partir de ahí respondiendo a esa cadena de preguntas hasta llegar al valor inicial, como hemos visto al resolver el caso del número *5*. Así es como trabaja Prolog.






