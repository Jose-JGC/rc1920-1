# T�CNICAS DE REPRESENTACI�N DEL CONOCIMIENTO EN INTELIGENCIA ARTIFICIAL
##Introducci�n
Representar el conocimiento en Inteligencia Artificial consiste en representar la informaci�n del mundo real para expresarlo en un lenguaje que pueda ser automatizado y se pueda utilizar para resolver problemas de la vida real.
Existen cuatro t�cnicas de representaci�n del conocimiento que veremos a continuaci�n.
<p align="center">
  <img src="imagenes/tecnicas.jpg">
</p>
##Representaci�n L�gica
Es un lenguaje que utiliza reglas definidas de tal forma que no existe ambig�edad en lo que se representa, utilizando proposiciones. Se aplican unas condiciones hasta llegar a la una conclusi�n. Cada proposici�n se traduce a la l�gica utilizando reglas de comunicaci�n definidas en sintaxis y sem�ntica precisas:
**Sintaxis**, son las reglas que determinan
-	C�mo se construyen las frases.
-	Qu� s�mbolos podemos usar.
-	C�mo se escriben esos s�mbolos.
**Sem�ntica**, son reglas que nos permiten
-	Interpretar las sentencias.
-	Asignar un significado a cada sentencia.
#### Ventajas
-	Ayuda al razonamiento l�gico
-	Es la base de los lenguajes de programaci�n
#### Desventajas
-	En ocasiones es dif�cil modelar el lenguaje natural.
-	Genera inferencias que no son eficientes
Veamos un ejemplo de modelado:
<p align="center">
  <img src="imagenes/tabla_modelado_logico.jpg">
</p>
## Redes Sem�nticas
Es otra forma de representaci�n del conocimiento que consiste en representarlo en forma de red gr�fica, donde los nodos  son los objetos y los enlaces son las relaciones entre los objetos. 
Los nodos de una red sem�ntica est�n unidos por los arcos, los cuales representan la relaci�n conceptual que existen entre ellos. 
Existen varias categor�as de redes sem�nticas: Redes IS-A, gr�ficos conceptuales y redes de marco. Veamos un ejemplo de Red IS-A. Representaremos el siguiente conocimiento:
```
-	Las aves tienen plumas y tienen alas.
-	El canario es un ave y come semillas.
-	Piol�n es un canario
-	El halc�n es un ave y tiene patas
-	Pedro es un Halc�n
```
<p align="center">
  <img src="imagenes/ejemplo_redes.jpg">
</p>
#### Ventajas
-	Representaci�n natural del conocimiento
-	Son muy potentes
-	Son simples y f�ciles de comprender
#### Desventajas
-	Poca flexibilidad
-	No son inteligentes y dependen del creador
-	Requieren mucho tiempo de computaci�n en tiempo de ejecuci�n.
-	No es posible construir redes sem�nticas grandes
## Marcos
Un marco es un registro que contienen una colecci�n de atributos y valores para describir una entidad. Divide el conocimiento en subestructuras. Se usan para representar conocimiento estereotipado o construido a  partir de experiencias reales.
Son una forma de expresar las redes sem�nticas. Cada nodo corresponde a un objeto que se convierte en un marco, que consta de una primera l�nea con el nombre del marco y una sucesi�n de l�neas, llamadas ranuras (slots). Los marcos se relacionan unos con otros usando el concepto de herencia.
Hay dos tipos de marcos:
-	Clase: representan conceptos o situaciones gen�ricas. Se describen por propiedades.
-	Instancia: representan objetos concretos o individuos y est�n relacionados con un marco clase. Heredan las propiedades.
<p align="center">
  <img src="imagenes/ejemplo_marcos.jpg">
</p>

#### Ventajas
-	Facilita la programaci�n
-	Muy usado en IA por su flexibilidad.
-	Sintaxis consistente y f�cil de leer
-	Facilidad para agregar nuevos atributos y relaciones.
#### Desventajas
-	Enfoque generalizado
-	El mecanismo de deducci�n puede no ajustarse de forma correcta a nuevas situaciones 
-	El mecanismo puede no ser procesado correctamente

## Reglas de producci�n
En este tipo de representaci�n, el agente comprueba la condici�n y si �sta es cierta, se activa la regla correspondiente y se ejecuta la acci�n. La condici�n determina qu� regla hay que cumplir y la parte de la acci�n lleva a cabo los pasos de la resoluci�n del problema en cuesti�n. A este proceso completo se le conoce como "ciclo de reconocimiento-toma de decisi�n" (recognize-act cycle)
El sistema de reglas est� formado por tres partes:
-	Conjunto de reglas de producci�n.
-	Memoria de trabajo.
-	Ciclo de reconocimiento-toma de decisi�n.
La siguiente figura muestra un ejemplo de las reglas de un sistema de cajero autom�tico
 <p align="center">
  <img src="imagenes/ejemplo_reglas.jpg">
</p>
#### Ventajas
-	Las regalas se pueden implementar en cualquier lenguajes
-	Muy f�cil de representar en l�gica
-	Modular, por que se pueden eliminar o modificar f�cilmente.
#### Desventajas
-	No almacena el resultado del problema para usos futuros
-	Muy ineficiente en grandes sistemas
-	No presenta aprendizaje

## Bibliograf�a
- http://www.cs.us.es/~fsancho/?e=103
- http://roa.ult.edu.cu/bitstream/123456789/236/1/CAP2IA.pdf
- https://sitiointeligenciaa.wordpress.com/redes-semanticas/
- https://www.cs.us.es/~jalonso/cursos/li-03/temas/tema-6.pdf
- https://www.cs.us.es/cursos/ia2-2003/temas/tema-03.pdf
- http://dit.upm.es/~gfer/ssii/rcsi/rcsisu15.html
- https://freedoomforlife.wordpress.com/reglas/

