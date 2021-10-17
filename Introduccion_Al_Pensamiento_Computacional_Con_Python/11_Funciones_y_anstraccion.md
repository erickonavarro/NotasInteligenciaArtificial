# Funciones y abstracción

## Abstracción

En programación, la **abstracción** se refiere al énfasis en el ¿qué se hace? en vez del ¿cómo se hace? en otras palabras, no es necesario que entiendas cómo funciona algo para poder utilizarlo. 

Una analogía del mundo real podría ser la televisión. Se trata de un dispositivo muy complejo donde han trabajado gran cantidad de ingenieros de diversas disciplinas como telecomunicaciones o electrónica. ¿Os imagináis que para cambiar de canal tuviéramos que saber todos los entresijos del aparato?. Pues bien, se nos ofrece una abstracción de la televisión, un **mando a distancia**. El mando nos abstrae por completo de la complejidad de los circuitos y señales, y nos da una interfaz sencilla que con unos pocos botones podemos usar.

Algo muy parecido sucede en la programación orientada a objetos. Si tuviéramos una clase `Televisor`, en su interior podría haber líneas y líneas de código super complejas, pero una buena abstracción sería la que simplemente ofreciera los métodos `encender()`, `apagar()` y `cambiar_canal()` al exterior.

## Decomposición

Permite dividir el código en componentes que colaboran con un fin en común. Esto quiere decir que dentro de un programa puede tener una serie de sub-programas dentro del mismo. En la electrónica, por ejemplo, se tienen una serie de componentes como transistores, capacitores, resistencias, que se acomodan de cierta manera para lograr un fin común. 

## Funciones en Python

Anteriormente hemos usado funciones nativas que vienen con Python como `len()` para calcular la longitud de una lista, pero al igual que en otros lenguajes de programación, también podemos definir **nuestras propias funciones**. Para ello hacemos uso de `def`.

```python
def nombre_funcion(argumentos):
    código
    return retorno
```

Cualquier función tendrá:

* **Nombre**, el cual sigue los mismos lineamentos para nombrar variables: no empezar con un número, admite mayúsculas y minúsculas, al igual que guiones bajos. 
* **Argumentos de entrada**, son argumentos que el usuario debe ingresar pues son las variables con las que la función trabajará.
* **Código**, la serie de operaciones o tareas a ejecutar 
* **Parámetros de salida**, el resultado de la función. Este se define con la función `return`, y si no se incluye la función devuelve el tipo `None`. 

Al igual que las funciones matemáticas, en programación nos permiten realizar diferentes operaciones con la entrada, para entregar una determinada salida que dependerá del código que escribamos dentro. Por lo tanto, es totalmente análogo al clásico `y=f(x)` de las matemáticas.

```python
>>>def f(x):
>>>    return 2*x
>>>y = f(3)
>>>print(y) 
6
```

El nombre de la función es `f()`, toma como argumento la variable `x`. y devuelve el valor de `x` por 2. 

Algo que diferencia en cierto modo las funciones en el mundo de la programación, es que no sólo realizan una operación con sus entradas, sino que también parten de los siguientes principios:

- El principio de **reusabilidad**, que nos dice que si por ejemplo tenemos un fragmento de código usado en muchos sitios, la mejor solución sería pasarlo a una función. Esto nos evitaría tener código repetido, y que modificarlo fuera más fácil, ya que bastaría con cambiar la función una vez.
- Y el principio de **modularidad**, que defiende que en vez de escribir largos trozos de código, es mejor crear módulos o funciones que agrupen ciertos fragmentos de código en funcionalidades específicas, haciendo que el código resultante sea más fácil de leer.

## Pasando argumentos de entrada

Empecemos por la función más sencilla de todas. Una función sin parámetros de entrada ni parámetros de salida.

```python
def di_hola():
    print("Hola")
```

Hemos declarado la función. El siguiente paso es llamarla con `di_hola()`. Si lo realizamos veremos que se imprime Hola.

```python
>>>di_hola()
'Hola'
```

Vamos a complicar un poco las cosas pasando un argumento de entrada. Ahora si pasamos como entrada un nombre, se imprimirá Hola y el nombre.

```python
>>>def di_hola(nombre):
>>>    print("Hola", nombre)
>>>
>>>di_hola("Juan")
'Hola Juan'
```

Python permite pasar argumentos también de otras formas. A continuación las explicamos todas.

## Argumentos por posición

Los argumentos por posición o **posicionales** son la forma más básica e intuitiva de pasar parámetros. Si tenemos una función `resta()` que acepta dos parámetros, se puede llamar como se muestra a continuación.

```python
>>>def resta(a, b):
>>>    return a-b
>>>
>>>r = resta(5, 3)
>>>print(r)
2
```

Al tratarse de parámetros posicionales, se interpretará que el primer número es la `a` y el segundo la `b`. El número de parámetros es fijo, por lo que si intentamos llamar a la función con solo uno, dará error.

```python
resta(1) # Error! TypeError
```

Tampoco es posible usar mas argumentos de los tiene la función definidos, ya que no sabría que hacer con ellos. Por lo tanto si lo intentamos, Python nos dirá que toma 2 posicionales y estamos pasando 3, lo que no es posible.

```python
TypeError: resta() takes 2 positional arguments but 3 were given
resta(5,4,3) # Error
```

### Argumentos por nombre

Otra forma de llamar a una función, es usando el nombre del argumento con `=` y su valor. El siguiente código hace lo mismo que el código anterior, con la diferencia de que los argumentos no son posicionales.

```python
>>>r = resta(a=3, b=5)
>>>print(r)
-2
```

Al indicar en la llamada a la función el nombre de la variable y el valor, el orden ya no importa, y se podría llamar de la siguiente forma.

```python
>>>r = resta(b=5, a=3)
>>>print(r)
-2
```

Como es de esperar, si indicamos un argumento que no ha sido definido como parámetro de entrada, tendremos un error.

```python
>>>resta(b=5, c=3)
Error!
resta() got an unexpected keyword argument 'c'
```

### Argumentos por defecto

Tal vez queramos tener una función con algún parámetro opcional, que pueda ser usado o no dependiendo de diferentes circunstancias. Para ello, lo que podemos hacer es asignar un valor **por defecto** a la función. En el siguiente caso `c` valdría cero salvo que se indique lo contrario.

```python
>>>def suma(a, b, c=0):
>>>    return a+b+c
>>>
>>>r = suma(5,5,3)
>>> print(r)
13
```

Dado que el parámetro `c` tiene un valor por defecto, la función puede ser llamada sin ese valor.

```python
>>>r = suma(4,3)
>>>print(r)
7
```

Podemos incluso asignar un valor por defecto a todos los parámetros, por lo que se podría llamar a la función sin ningún argumento de entrada.

```python
>>>def suma(a=3, b=5, c=0):
>>>    return a+b+c
>>>
>>>r = suma()
>>>print(r)
8
```

Las siguientes llamadas a la función también son válidas

```python
>>>r = suma(1) # 1 + 5 + 0 = 6
>>>print(r)
6
>>>r = suma(4,5)   # 4 + 5 + 0 = 9
>>>print(r)
9
>>>r = suma(5,3,2) # 5 + 3 + 2 = 10
>>>print(r) 
10
```

O haciendo uso de lo que hemos visto antes y usando los nombres de los argumentos.

```python
>>>r = suma(a=5, b=3)  # 5 + 3 + 0 = 8
>>>print(r) 
8
```

## Argumentos de longitud variable

En el ejemplo con argumentos por defecto, hemos visto que la función puede ser llamada con diferente número de argumentos de entrada, pero esto no es realmente una función con argumentos de longitud variable, ya que existe un número máximo.

Imaginemos que queremos una función `suma()` como la de antes, pero en este caso necesitamos que sume todos los números de entrada que se le pasen, sin importar si son 3 o 100. Una primera forma de hacerlo sería con una lista.

```python
>>>def suma(numeros): #numeros es una lista
>>>    total = 0
>>>    for n in numeros: #se suman todos los elementos de la lista
>>>        total += n
>>>    return total
>>>
>>>r = suma([1,3,5,4]) # 1 + 3 + 5 + 4 = 13
>>>print(r) 
13
```

La forma es válida y cumple nuestro requisito, pero realmente no estamos trabajando con argumentos de longitud variable. En realidad tenemos un solo argumento que es una lista de números.

Por suerte, Python tiene una herramienta muy potente. Si declaramos un argumento con `*`, esto hará que el argumento que se pase sea empaquetado en una tupla de manera automática. No confundir `*` con los punteros en otros lenguajes de programación, no tiene nada que ver.

```python
>>>def suma(*numeros):
>>>    print(type(numeros))
>>>    total = 0
>>>    for n in numeros:
>>>        total += n
>>>    return total
>>>
>>>r = suma(1, 3, 5, 4)
>>>print(r) 
<class 'tuple'> #comprobamos que *numeros es una tupla
13
```

El resultado es igual que el anterior, y podemos ver como efectivamente `numeros` es de la clase `tuple`. También podemos hacer otras llamadas con diferente número de argumentos

```python
>>>r = suma(6)
>>>print(r) 
6
>>>r = suma(6, 4, 10)
>>>print(r) 
20
>>>r = suma(6, 4, 10, 20, 4, 6, 7)
>>>print(r) 
57
```

Usando doble `**` es posible también tener como parámetro de entrada una lista de elementos almacenados en forma de clave y valor. En este caso podemos iterar los valores haciendo uso de `items()`.

```python
>>>def suma(**kwargs):
>>>    suma = 0;
>>>    for key, value in kwargs.items():
>>>        print(key, value)
>>>        suma += value
>>>    return suma
>>>
>>>r = suma(a=5, b=20, c=23)
>>>print(r) 
a 5
b 20
c 23
48
```

De igual manera, podemos pasar un diccionario como parámetro de entrada.

```python
>>>def suma(**kwargs):
>>>    suma = 0
>>>    for key, value in kwargs.items():
>>>        print(key, value)
>>>        suma += value
>>>    return suma
>>>di = {'a': 10, 'b':20}
>>>r = suma(**di)
a 10
b 20
30
```

## Sentencia return

El uso de la sentencia `return` permite realizar dos cosas:

- Salir de la función y transferir la ejecución de vuelta a donde se realizó la llamada.
- Devolver uno o varios parámetros, fruto de la ejecución de la función.

En lo relativo a lo primero, una vez se llama a `return` se para la ejecución de la función y se vuelve o retorna al punto donde fue llamada. Es por ello por lo que el código que va después del `return` no es ejecutado en el siguiente ejemplo.

```python
>>>def mi_funcion():
>>>    print("Entra en mi_funcion")
>>>    return
>>>    print("No llega")
>>>mi_funcion()
'Entra en mi_funcion'
```

Por ello, sólo llamamos a `return` una vez hemos acabado de hacer lo que teníamos que hacer en la función.

Por otro lado, se pueden **devolver parámetros**. Normalmente las funciones son llamadas para realizar unos cálculos en base a una entrada, por lo que es interesante poder devolver ese resultado a quien llamó a la función.

```python
>>>def di_hola():
>>>    return "Hola"
>>>di_hola()
'Hola'
```

También es posible devolver mas de una variable, separadas por `,`. En el siguiente ejemplo tenemos una función que calcula la suma y media de tres números, y devuelve su resultado.

```python
>>>def suma_y_media(a, b, c):
>>>    suma = a+b+c
>>>    media = suma/3
>>>    return suma, media
>>>suma, media = suma_y_media(9, 6, 3)
>>>print(suma)  
>>>print(media)
18
6.0

```

