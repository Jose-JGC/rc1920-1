						APRENDIENDO PROLOG DESDE 0
					
Jose Joaquín González Colchero

DÍA 1.
Hoy es el primer dia de aprendizaje de prolog desde 0. Hoy aprenderemos el principio de inducción, ya que es el concepto más basico y el pilar de la programación en prolog.
Para aprender este concepto, visualizaremos el siguiente video: https://www.youtube.com/watch?v=31ypX6BVq2E
Despues de ver el video, realizaremos el ejercicio propuesto por el mismo y analizaremos su funcionamiento.
Teoria importante: principio de inducción viene dado por:
	//https://youtu.be/31ypX6BVq2E?t=215
	P es cierta para n0
	para todo n > n0, p(n-1) -> p(n).
Lo que personalmente he sacado de esta regla matemática es que usaremos un caso base para resolver los casos que sean solicitados.
Ésto quiere decir que llamaremos a la función principal varias veces hasta llegar al predicado original. Si el predicado original es cierto, lo será el resto.
Para entenderlo de forma más grafica con el ejercicio de ejemplo que más tarde resolveremos: https://youtu.be/31ypX6BVq2E?t=548

Ejercicio 1: obtener verdadero si un numero introducido es natural y falso si no lo es.
	natural(1).                               
	natural(N):- N > 1, N2 is N-1, natural(N2).
Este codigo soluciona el ejercicio propuesto.
Desglose del codigo: 
	natural(1). // Es el caso base. Estamos diciendole a prolog que natural de 1 es cierto. Es una afirmación, luego prolog la usará como caso base para resolver las llamadas a natural()
	natural(N):-	//en prolog a->b se escribe como b:-a. https://youtu.be/31ypX6BVq2E?t=257
		N > 1,		// N tiene que ser mayor que 1 para asignar N2 y hacer natural(N2).
		N2 is N-1,	// N2 sera el numero anterior a N
		natural(N2).//de esta forma natural(N2) llamará a natural con N-1. Todo esto se hara varias veces hasta que N2 sea 1. Como hemos afirmado anteriormente que natural(1). es cierto, prolog irá reduciendo N2
					//hasta 1 para luego poder afirmar o no, dependiendo de si consigue obtener 1, que el numero sea natural. De nuevo referencio esta parte del video como ejemplo de este funcionamiento: https://youtu.be/31ypX6BVq2E?t=548
					
En conclusión: El día de hoy hemos aprendido el principio de inducción matemático para aplicarlo a la resolución de problemas en prolog.
Con esto obtenemos la base para realizar ejercicios más elaborados.