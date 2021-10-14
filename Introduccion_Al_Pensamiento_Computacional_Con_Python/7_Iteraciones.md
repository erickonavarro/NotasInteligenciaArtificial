# Iteraciones

Las iteraciones permiten realizar la misma tarea en varias ocasiones. Las instrucciones de repetición, de iteración o bucles, facilitan la repetición de un bloque de instrucciones, un número determinado de veces o mientras se cumpla una condición.

En programación, existen dos tipos de iteración, la **indefinida** y la **definitiva**:

* En la iteración **indefinida**, el número de veces que se ejecuta el bucle no se especifica explícitamente por adelantado. Más bien, el bloque designado se ejecuta repetidamente mientras se cumpla alguna condición.

* Con la iteración **definida**, el número de veces que se ejecutará el bloque designado se especifica explícitamente en el momento en que se inicia el bucle.

Por lo general, existen dos tipos de estructuras iterativas o bucles en los lenguajes de programación. Encontraremos un tipo de bucle que se ejecuta un número preestablecido de veces, que es controlado por un contador o índice, incrementado en cada iteración. Este tipo de bucle forma parte de la familia `for`.

Por otro lado, encontraremos un tipo de bucle que se ejecuta mientras se cumple una condición. Esta condición se comprueba al principio o el final de la construcción. Esta variante pertenece a la familia `while`. 

Algunas generalidades de las iteraciones:

* Se pueden escribir iteraciones dentro de iteraciones
* Para salir anticipadamente de una iteración utilizas `break`
* Hay que tener cuidado con las iteraciones infinitas

## Bucles `while`

El formato de un bucle `while` rudimentario se muestra a continuación:

```
while <expr>:
    <declaración(es) >
```

`<sentencia(s)> `representa el bloque que se ejecutará repetidamente, a menudo denominado cuerpo del bucle. Esto se denota con sangría, al igual que en una sentencia if.

Recuerde: Todas las estructuras de control en Python usan sangría para definir bloques. Vea la discusión sobre la agrupación de sentencias en el tutorial anterior para repasar.

La expresión de control, `<expr>,` típicamente involucra una o más variables que son inicializadas antes de comenzar el bucle y luego modificadas en alguna parte del cuerpo del bucle.

Cuando se encuentra un bucle ` while`,  `<expr>` se evalúa primero en contexto booleano. Si es verdadero, se ejecuta el cuerpo del bucle. Entonces `<expr>` se comprueba de nuevo, y si sigue siendo cierto, el cuerpo se ejecuta de nuevo. Esto continúa hasta que <expr> se convierte en falso, momento en el que la ejecución del programa procede a la primera sentencia más allá del cuerpo del bucle.

Considere este bucle:

```python
>>>n = 5
>>>while n > 0
>>>    n -= 1
>>>    print(n)
...
4
3
2
1
0
```

Esto es lo que ocurre en este ejemplo:

n es inicialmente 5. La expresión en la cabecera de la sentencia while en la línea 2 es n > 0, que es verdadera, por lo que el cuerpo del bucle se ejecuta. Dentro del cuerpo del bucle en la línea 3, n se decrementa en 1 hasta llegar a 4, y luego se imprime.

Cuando el cuerpo del bucle ha terminado, la ejecución del programa vuelve a la parte superior del bucle en la línea 2, y la expresión se evalúa de nuevo. Sigue siendo verdadera, por lo que el cuerpo se ejecuta de nuevo, y se imprime 3. Esto continúa hasta que n se convierte en 0.

Esto continúa hasta que n se convierte en 0. En ese punto, cuando la expresión se evalúa, es falsa, y el bucle termina. La ejecución se reanudaría en la primera sentencia que sigue al cuerpo del bucle, pero en este caso no hay ninguna.

Observe que la expresión de control del bucle `while `se comprueba primero, antes de que ocurra nada más. Si es falsa al principio, el cuerpo del bucle nunca se ejecutará:

```
>>>n = 0
>>>while n > 0
>>>    n -= 1
>>>    print(n)
...
```

n el ejemplo anterior, cuando se encuentra el bucle, n es 0. La expresión de control n > 0 ya es falsa, por lo que el cuerpo del bucle nunca se ejecuta.

Aquí hay otro bucle while que implica una lista, en lugar de una comparación numérica:

```
>>>a = ['foo', 'bar', 'baz']
>>>while a:
>>>    print(a.pop(-1))
...
baz
bar
foo
```

Cuando una lista se evalúa en un contexto booleano, es verdadera si tiene elementos y falsa si está vacía. En este ejemplo, a es verdadera mientras tenga elementos en ella. Una vez que se han eliminado todos los elementos con el método .pop() y la lista está vacía, a es falso, y el bucle termina.

## Bucles `for`

El bucle `for ` más básico es una simple sentencia de rango numérico con valores iniciales y finales. El formato sería:

```python
for <var> in <iterable>:
    <statement(s)>
```

Aquí, el cuerpo del bucle se ejecuta diez veces. La variable i asume el valor 1 en la primera iteración, 2 en la segunda, y así sucesivamente.

`<iterable> ` es una colección de objetos-por ejemplo, una lista o tupla. La(s) `<sentencia(s)> ` en el cuerpo del bucle se indican con sangría, como en todas las estructuras de control de Python, y se ejecutan una vez por cada elemento de `<iterable>`. La variable de bucle <var> toma el valor del siguiente elemento en `<iterable>` cada vez que se pasa por el bucle.

He aquí un ejemplo representativo:

```
>>>a = ['foo', 'bar', 'baz']
>>>for i in a:
>>>    print(i)
...
foo
bar
baz
```

En este ejemplo, `<iterable>` es la lista a, y `<var>` es la variable i. Cada vez que se pasa por el bucle, i toma un elemento sucesivo de a, por lo que print() muestra los valores 'foo', 'bar' y 'baz', respectivamente. Un bucle `for `como éste es la forma pitónica de procesar los elementos de un iterable.

¿Pero qué es exactamente un iterable? Antes de examinar más a fondo los bucles `for`, será beneficioso profundizar en lo que son los iterables en Python.

## Iterables

En Python, iterable significa que un objeto puede ser utilizado en la iteración. El término se utiliza como:

* **Un adjetivo**: Un objeto puede ser descrito como iterable.
* **Un sustantivo**: Un objeto puede ser caracterizado como iterable.

Si un objeto es iterable, puede pasarse a la función incorporada de Python iter(), que devuelve algo llamado iterador. Sí, la terminología es un poco repetitiva. Pero no te desanimes. Al final todo funciona.

Cada uno de los objetos del siguiente ejemplo es un iterable y devuelve algún tipo de iterador cuando se pasa a `iter()`:



```python
>>>iter('foobar') # String
<objeto iterador_str en 0x036E2750>

>>>iter(['foo', 'bar', 'baz']) # Lista
<objeto list_iterator en 0x036E27D0>

>>>iter(('foo', 'bar', 'baz')) # Tupla
<objeto iter_tupla en 0x036E27F0>

>>>iter({'foo', 'bar', 'baz'}) # Set
<objeto set_iterator en 0x036DEA08>

>>>iter({'foo': 1, 'bar': 2, 'baz': 3}) # Dict
<objeto dict_keyiterator en 0x036DD990>
```

Estos tipos de objetos, en cambio, no son iterables:

```python
>>>iter(42) # Entero
Traceback (most recent call last):
  File "<pyshell#26>", line 1, in <module>
    iter(42)
TypeError: El objeto 'int' no es iterable

>>>iter(3.1) # Float
Traceback (most recent call last):
  File "<pyshell#27>", line 1, in <module>
	iter(3.1)
TypeError: El objeto 'float' no es iterable

>>>iter(len) # Función incorporada
Traceback (most recent call last):
  File "<pyshell#28>", line 1, in <module>
	iter(len)
TypeError: El objeto 'builtin_function_or_method' no es iterable
```

## Iteradores

Bien, ahora sabes lo que significa que un objeto sea iterable, y sabes cómo usar `next()` para obtener un **iterador** de él. Una vez que tienes un iterador, ¿qué puedes hacer con él?

Un **iterador** es esencialmente un productor de valores que devuelve valores sucesivos de su objeto iterable asociado. La función incorporada `next()` se utiliza para obtener el siguiente valor de un iterador.

Aquí hay un ejemplo usando la misma lista de arriba:

```python
>>>a = ['foo', 'bar', 'baz']

>>>itr = iter(a)
>>>itr
<objeto iter de la lista en 0x031EFD10>

>>>next(itr)
'foo'
>>>next(itr)
'bar'
>>>next(itr)
'baz'
```

En este ejemplo, a es una lista iterable e itr es el iterador asociado, obtenido con `iter().` Cada llamada a `next(itr)` obtiene el siguiente valor de itr.

Observa cómo un iterador conserva su estado internamente. Sabe qué valores se han obtenido ya, así que cuando se llama a next(), sabe qué valor devolver a continuación.

¿Qué ocurre cuando el iterador se queda sin valores? Hagamos una llamada más a `next() ` en el iterador anterior:

```
>>>next(itr)
Traceback (most recent call last):
  File "<pyshell#10>", line 1, in <module>
    next(itr)
StopIteration
```

Si ya se han devuelto todos los valores de un iterador, una llamada posterior a `next() ` lanza una excepción StopIteration. Cualquier otro intento de obtener valores del iterador fallará.

## Las sentencias `break ` y `continue`

En cada ejemplo que has visto hasta ahora, el cuerpo completo del bucle while se ejecuta en cada iteración. Python proporciona dos palabras clave que terminan una iteración de bucle prematuramente:

La sentencia `break ` de Python termina inmediatamente un bucle por completo. La ejecución del programa procede a la primera sentencia que sigue al cuerpo del bucle.

La sentencia `continue` de Python termina inmediatamente la iteración actual del bucle. La ejecución salta a la parte superior del bucle, y la expresión de control se reevalúa para determinar si el bucle se ejecutará de nuevo o terminará.

La distinción entre `break ` y `continue ` se demuestra en el siguiente diagrama:

<img src="https://i.imgur.com/0Y8NZ6h.png" alt="drawing" width="500"/>

Aquí hay un archivo de script llamado break.py que demuestra la sentencia `break`:

```python
n = 5
while n > 0:
	n -= 1
	if n == 2:
    	break
    print(n)
print('Loop ended.')
```

La ejecución de break.py desde un intérprete de línea de comandos produce la siguiente salida:

```python
4
3
Loop ended.
```

When `n` becomes `2`, the `break` statement is executed. The loop is terminated completely, and program execution jumps to the `print()` statement on line 7.

The next script, `continue.py`, is identical except for a `continue` statement in place of the `break`:

```
n = 5
while n > 0:
   n -= 1
   if n == 2:
       continue
   print(n)
print('Loop ended.')
```

La salida de continue.py tiene este aspecto:

```python
4
3
1
0
Loop ended.
```

