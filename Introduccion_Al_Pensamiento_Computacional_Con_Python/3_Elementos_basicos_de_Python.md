# Elementos básicos de Python



Existen dos categorías para los lenguajes de programácion:

* **Bajo nivel**: Son aquellos que se acercan más a un lenguaje de 1 y 0, un lenguaje que la máquina entiende mejor.
* **Alto nivel**: Son lenguajes que se acerca más a la forma en cómo nos comunicamos los humanos. 

También se dividen dependiendo de su dominio en:

* **General**: Tienen todos los primitivos para poder computar cualquier tipo de algoritmo.
* **Dominio específico**: Tienen aplicaciones especificas.

Por último, tenemos lenguajes interpretados y compilados:

* **Interpretado**: Mientras el programa corre, el lenguaje se traduce al lenguaje máquina para que esta pueda interpretarlo.
* **Compilado** Antes de que se corra el programa, el código se traduce al lenguaje máquina. 

Python es un lenguaje de **alto nivel**, es de **dominio general** y es **interpretado**. 

## Literales y operadores

Los elementos básicos de Python son:

* **Literales**: Estos son números enteros como el 1, 64, 865; números flotantes como 0.4, 54.26, 1.4566477; cadenas de caracteres y booleanos (True y False). 
* **Operadores**: Son los signos que nos permiten realizar operaciones matemáticas, tales como + / * % ** = ==. 

La forma en que se pueden utilizar los **operadores** y las **literales** es con la siguiente sintaxis:

```python
<literal> <operador> <literal>
```

Si no se respeta dicha sintaxis podemos tener errores. Veamos cómo funcionan.

Para hacer una suma simple podemos escribir lo siguiente

```python
1 + 2
```

Lo que dará 3. Ve como sumamos dos números enteros. Sin embargo, si queremos hacer lo siguiente:

```python
5 / 'Platzi'
```

Nos daría un error debido a que estamos intentando dividir un entero entre un string. Por otro lado, si hacemos:

```python
5 * 'Platzi'
```

Dará como resultado

```python
'PlatziPlatziPlatziPlatziPlatzi'
```

Esto es porque hay ciertos operadores que sí se pueden utilizar con los strings, los cuales veremos más adelante.

## Hola, mundo!

Una sentencia es una instrucción que el intérprete de Python puede ejecutar. Hemos visto dos tipos de sentencias: print y assignment.

Cuando escribes una sentencia en la línea de comandos, Python la ejecuta y muestra el resultado, si lo hay. El resultado de una sentencia print es un valor. Las sentencias de asignación no producen un resultado.

Nuestra primera sentencia será el famoso 'Hola, mundo!', para ello sólo escribimos:

```python
print('Hola, mundo!')
```

Este comando no produce un resultado, sino sólo imprime en pantalla lo que está dentro del paréntesis:

```python
Hola, mundo!
```

Una sentencia que sí produce un resultado sería el siguiente 

```
imprimir 1
x = 2
imprimir x
```

produce la salida

```
1
2
```

## Clases y Objetos

Python es un lenguaje de programación orientado a objetos. A diferencia de la programación orientada a procedimientos, donde el énfasis principal está en las funciones, la programación orientada a objetos hace hincapié en los objetos.

Un **objeto** es simplemente una colección de datos (variables) y métodos (funciones) que actúan sobre esos datos. Del mismo modo, una clase es un plano de ese objeto.

Podemos pensar en una **clase** como un boceto (prototipo) de una casa. Contiene todos los detalles sobre los pisos, las puertas, las ventanas, etc. A partir de estas descripciones construimos la casa. La casa es el objeto.

Como se pueden hacer muchas casas a partir de un boceto de casa, podemos crear muchos objetos a partir de una clase. Un objeto también se llama instancia de una clase y el proceso de creación de este objeto se llama instanciación.

En el caso de Python un **objeto** va a ser lo que explicamos anteriormente como una **literal** entonces la sintaxis para utilizarlos sería:

```python
<objeto> <operador> <objeto>
```

Más adelante se verá qué tipo de operadores se pueden utilizar para cada tipo de objeto. 