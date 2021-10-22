# Diccionarios

Un diccionario en Python es una colección de elementos, donde cada uno tiene una llave `key` y un valor `value`. Los diccionarios se pueden crear con paréntesis `{}` separando con una coma cada par `key: value`. En el siguiente ejemplo tenemos tres `keys` que son el nombre, la edad y el documento.

```python
d1 = {
  "Nombre": "Sara",
  "Edad": 27,
  "Documento": 1003882
}
print(d1)
#{'Nombre': 'Sara', 'Edad': 27, 'Documento': 1003882}
```

Otra forma equivalente de crear un diccionario en Python es usando `dict()` e introduciendo los pares `key: value` entre paréntesis.

```python
d2 = dict([
      ('Nombre', 'Sara'),
      ('Edad', 27),
      ('Documento', 1003882),
])
print(d2)
#{'Nombre': 'Sara', 'Edad': '27', 'Documento': '1003882'}
```

También es posible usar el constructor `dict()` para crear un diccionario.

```python
d3 = dict(Nombre='Sara',
          Edad=27,
          Documento=1003882)
print(d3)
#{'Nombre': 'Sara', 'Edad': 27, 'Documento': 1003882}
```

Algunas propiedades de los diccionario en Python son las siguientes:

- Son **dinámicos**, pueden crecer o decrecer, se pueden añadir o eliminar elementos.
- Son **indexados**, los elementos del diccionario son accesibles a través del `key`.
- Y son **anidados**, un diccionario puede contener a otro diccionario en su campo `value`.

## Acceder y modificar elementos

Se puede acceder a sus elementos con `[]` o también con la función `get()`

```python
print(d1['Nombre'])     #Sara
print(d1.get('Nombre')) #Sara
```

Para modificar un elemento basta con usar `[]` con el nombre del `key` y asignar el valor que queremos.

```python
d1['Nombre'] = "Laura"
print(d1)
#{'Nombre': Laura', 'Edad': 27, 'Documento': 1003882}
```

Si el `key` al que accedemos no existe, se añade automáticamente.

```python
d1['Direccion'] = "Calle 123"
print(d1)
#{'Nombre': 'Laura', 'Edad': 27, 'Documento': 1003882, 'Direccion': 'Calle 123'}
```

## Iterar diccionario

Los diccionarios se pueden iterar de manera muy similar a las listas u otras estructuras de datos. Para imprimir los `key`.

```python
# Imprime los key del diccionario
>>> dict = {"David":35, 
>>>         "Erika":32, 
>>>         "Pedro":70
>>>        }
>>> for valor in dict.keys():
>>>     print(x)
David
Erika
Pedro
```

Se puede imprimir también solo el `value`.

```python
# Imprime los values del diccionario
>>> dict = {"David":35, 
>>>         "Erika":32, 
>>>         "Pedro":70
>>>        }
>>> for valor in dict.values():
>>>     print(x)
35
32
70
```

O si queremos imprimir el `key` y el `value` a la vez.

```python
# Imprime los key y value del diccionario
>>> dict = {"David":35, 
>>>         "Erika":32, 
>>>         "Pedro":70
>>>        }
>>> for valor in dict.items():
>>>     print(x)
David 35
Erika 32
Pedro 70
```

## Diccionarios anidados

Los diccionarios en Python pueden contener uno dentro de otro. Podemos ver como los valores anidado uno y dos del diccionario `d` contienen a su vez otro diccionario.

```python
pytanidado1 = {"a": 1, "b": 2}
anidado2 = {"a": 1, "b": 2}
d = {
  "anidado1" : anidado1,
  "anidado2" : anidado2
}
print(d)
#{'anidado1': {'a': 1, 'b': 2}, 'anidado2': {'a': 1, 'b': 2}}
```

## Operadores para diccionarios

Podemos utilizar el operador `del` para eliminar un elemento del diccionario, e `in` para ver si un elemento se encuentra dentro del diccionario.

Veamos el siguiente ejemplo donde eliminamos a `David` utilizando `del`

```python
>>> dict = {"David":35, 
>>>         "Erika":32, 
>>>         "Pedro":70
>>>        }
>>> del dict["David"]
>>> print(dict)
{'Erika': 32, 'Pedro': 70}
```

 Ahora para revisar si se encuentra `Erika` en el diccionario utilizamos `in`

```python
>>> print(dict)
{'Erika': 32, 'Pedro': 70}
>>> "Erika" in dict
True
>>> "Juan" in dict
False
```

Como vemos, devolvió `True` porque "Erika" sí se encuentra en el diccionario, pero al buscar por "Juan" devuelve `False` porque no se encuentra. 

## Dictionary comprehensions

Se comporta igual que las `list comprehensions`, pero con la diferencia de que se guardan llaves y valores.

La estructura de los `dict compregensions` es la siguiente:

```python
{key:value for value in iterable if condition}
```

- **key:value**: Representa a cada una de las llaves y valores a poner en el nuevo diccionario
- **for value in iterable**: Ciclo a partir del cual se extraerán elementos cualquier iterable
- **if condition**: Condición opcional para filtrar los elementos del ciclo

Para cada elemento en un iterable, se coloca una llave y un valor solo si se cumple la condición.

Por ejemplo:

```python
{i: i**3 for i in range(1, 101) if i % 3 != 0}
```

Para cada i en el rango de 1 hasta 100 se va a guardar i como la llave y a i al cubo como su valor, si y solo si, i es divisible por 3.

```python
div_3 = {i: i**3 for i in range(1, 101) if i % 3 == 0}
for i in div_3:
    print(i)
```



## Métodos diccionarios Python

`clear()`

El método `clear()` elimina todo el contenido del diccionario.

```python
d = {'a': 1, 'b': 2}
d.clear()
print(d) #{}
```

`get(<key>[,<default>])`

El método `get()` nos permite consultar el `value` para un `key` determinado. El segundo parámetro es opcional, y en el caso de proporcionarlo es el valor a devolver si no se encuentra la `key`.

```python
d = {'a': 1, 'b': 2}
print(d.get('a')) #1
print(d.get('z', 'No encontrado')) #No encontrado
```

`items()`

El método `items()` devuelve una lista con los `keys` y `values` del diccionario. Si se convierte en `list` se puede indexar como si de una lista normal se tratase, siendo los primeros elementos las `key` y los segundos los `value`.

```python
d = {'a': 1, 'b': 2}
it = d.items()
print(it)             #dict_items([('a', 1), ('b', 2)])
print(list(it))       #[('a', 1), ('b', 2)]
print(list(it)[0][0]) #a
```

`keys()`

El método `keys()` devuelve una lista con todas las `keys` del diccionario.

```python
d = {'a': 1, 'b': 2}
k = d.keys()
print(k)       #dict_keys(['a', 'b'])
print(list(k)) #['a', 'b']
```

`values()`

El método `values()` devuelve una lista con todos los `values` o valores del diccionario.

```python
d = {'a': 1, 'b': 2}
print(list(d.values())) #[1, 2]
```

`pop(<key>[,<default>])`

El método `pop()` busca y elimina la `key` que se pasa como parámetro y devuelve su valor asociado. Daría un error si se intenta eliminar una `key` que no existe.

```python
d = {'a': 1, 'b': 2}
d.pop('a')
print(d) #{'b': 2}
```

También se puede pasar un segundo parámetro que es el valor a devolver si la `key` no se ha encontrado. En este caso si no se encuentra no habría error.

```python
d = {'a': 1, 'b': 2}
d.pop('c', -1)
print(d) #{'a': 1, 'b': 2}
```

`popitem()`

El método `popitem()` elimina de manera aleatoria un elemento del diccionario.

```python
d = {'a': 1, 'b': 2}
d.popitem()
print(d)
#{'a': 1}
```

`update(<obj>)`

El método `update()` se llama sobre un diccionario y tiene como entrada otro diccionario. Los `value` son actualizados y si alguna `key` del nuevo diccionario no esta, es añadida.

```python
d1 = {'a': 1, 'b': 2}
d2 = {'a': 0, 'd': 400}
d1.update(d2)
print(d1)
#{'a': 0, 'b': 2, 'd': 400}
```