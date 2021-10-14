# Cadenas y entradas

## Cadenas

Las cadenas en Python o `strings` son un tipo inmutable que permite almacenar secuencias de caracteres. Para crear una, es necesario incluir el texto entre comillas dobles `"`. Puedes obtener más ayuda con el comando `help(str).`

```python
>>>s = "Esto es una cadena"
>>>print(s)
Esto es una cadena

>>>print(type(s))
<class 'str'>
```

También es valido declarar las cadenas con comillas simples simples `'`.

```python
>>>s = 'Esto es otra cadena'
>>>print(s)        
Esto es otra cadena

>>>print(type(s)) 
<class 'str'>
```

Las cadenas no están limitadas en tamaño, por lo que el único límite es la memoria de tu ordenador. Una cadena puede estar también vacía.

Algo importante de mencionar es que las cadenas son **inmutables** esto quiere decir que una vez que se declara no pueden alterarse o modificarse. Si se puede reasignar el valor de la variable, que es lo que sucede cuando concatenamos o repetimos la variable, pero la cadena original no puede modificarse. 

## Multiplicar y concatenar strings

Los strings permiten dos tipos de operadores, el de suma y el de multiplicar.

```python
>>>num = "123" * 3
>>>print(num)
123123123
```

Al utilizar el operador de multiplicación ***** en un string, Python copiará esa cadena de caracteres las veces que hayas indicado. En el ejemplo, multiplicamos por 3 y vemos cómo se copió y pegó tres veces el número 123. 

```python
>>>num = "123" + "456"
>>>print(num)
123456
```

Cuando se utiliza el operador de suma **+** lo que se hace es concatenar los strings, esto quiere decir que se junta una cadena con otra. En el ejemplo, se concatena "123" y "456" para obtener "123456".

## Cadena de formato

Podemos utilizar la cadena de formato para realizar operaciones con los strings.

```python
>>> my_str = Erick
>>> "Yo amo a " + my_str
'Yo amo a Erick'

>>> my_str = Erick
>>> f"Yo amo a {my_str}"
'Yo amo a Erick'

>>> my_str = Erick
>>> f"Yo amo a {my_str}, " * 3
'Yo amo a Erick, Yo amo a Erick, Yo amo a Erick'
```

Observa como podemos utilizar la cadena de formato para hacer operaciones con los strings y da los mismos resultados que haciéndolo de manera convencional.

## Algunos métodos para strings

Algunos de los métodos de la clase string.

`len(string)`

El método **len()** devuelve un entero el cual es la longitud de ese string, en otras palabras, cuántos caracteres tiene la cadena. 

```python
>>> my_str = "Hola!!"
>>> len(my_str)
6
```

Para acceder a cada uno de los caracteres hacemos lo siguiente:

```python
>>>my_str[0]
'H'
>>>my_str[1]
'o'
>>>my_str[2]
'l'
```

Al colocar un número dentro de los corchetes Python nos devuelve el carácter que está en esa posición. Nota como Python comienza a contar desde 0, y es por eso que en la primera línea nos devolvió la letra "H". 

También podemos hacer lo siguiente 

```python
>>>my_str[2:]
'la!!'
```

Al agregar los dos puntos, podemos decidir qué pedazo de la cadena Python nos devuelva. En este caso quisimos que nos devolviera desde el carácter 2 hasta el último. 

```python
>>>my_str[:3]
'Hol'
```

Ahora nota como al no incluir un numero al comienzo nos devuelve los primeros tres caracteres . Presta atención que al hacerlo de esta forma Python no incluye el carácter en la posición número 3. 

```python
>>>my_str[:-2]
'Hola'
```

Si se coloca un número negativo Python devolverá todos los caracteres desde  el comienzo menos los últimos dos. 

```python
>>>my_str[::2]
'Hl!'
```

Agregando otros dos puntos podemos decirle a Python que devuelva los caracteres saltándose lugares, en este caso de 2 en 2.

`capitalize()`

El método `capitalize()` se aplica sobre una cadena y la devuelve con su primera letra en mayúscula.

```python
>>>s = "mi cadena"
>>>print(s.capitalize()) 
'mi cadena'
```

`lower()`

El método `lower()` convierte todos los caracteres alfabéticos en minúscula.

```python
>>>s = "MI CADENA"
>>>print(s.lower())
'mi cadena'
```

`swapcase()`

El método `swapcase()` convierte los caracteres alfabéticos con mayúsculas en minúsculas y viceversa.

```python
>>>s = "mI cAdEnA"
>>>print(s.swapcase()) 
'Mi CaDeNa'
```

`upper()`

El método `upper()` convierte todos los caracteres alfabéticos en mayúsculas.

```python
>>>s = "mi cadena"
>>>print(s.upper())
'MI CADENA'
```

`join(<iterable>)`

El método `join()` devuelve la primera cadena unida a cada uno de los elementos de la lista que se le pasa como parámetro.

```python
>>>s = " y ".join(["1", "2", "3"])
>>>print(s)
'1 y 2 y 3'
```

`split(sep=None, maxsplit=-1)`

El método `split()` divide una cadena en subcadenas y las devuelve almacenadas en una lista. La división es realizada de acuerdo a el primer parámetro, y el segundo parámetro indica el número máximo de divisiones a realizar.

```python
>>>s = "Python,Java,C"
>>>print(s.split(","))
['Python', 'Java', 'C']
```

## Entradas

En Python se utiliza la función `input()`para pedirle al usuario que ingrese datos a través del teclado. La función `input()`siempre regresa cadenas, por lo que si se quiere otro tipo de variable será necesario realizar una conversión.

```python
>>> nombre = input("Cual es tu nombre: ")
Cual es tu nombre:
```

En este punto el programa se pausa y espera a que el usuario escriba los datos y después presione `enter` para que el programa pueda continuar.

```python
>>> num = input("Escribe un numero: ")
Escribe un numero: 
>>>print(type(num))
<class 'str'>
```

Observa como la función input devuelve un `sting` y en este caso no nos interesa que sea una cadena si no un entero, para ello se puede utilizar la función `int()` fuera del `input()` para que así se convierta la variable.

```python
>>> num = int(input("Escribe un numero: "))
Escribe un numero: 
>>>print(type(num))
<class 'int'>
```

