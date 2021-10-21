# Tuplas

Las tuplas o `tuples` en Python son un tipo o estructura de datos que permite almacenar datos de una manera muy parecida a las listas, con la salvedad de que son **inmutables**.

Algunas generalidades:

* Son secuencias inmutables de objetos, es decir, no se pueden modificar.
* Pueden contener cualquier tipo de objetos.
* Pueden devolver varios valores en una función
* Se definen utilizando los paréntesis `()`

Un ejemplo de una tupla sería el siguiente:

```python
>>> tupla = (1, 2, 3)
>>> print(tupla)
(1, 2, 3)
```

También pueden declararse sin `()`, separando por `,` todos sus elementos.

```python
>>> tupla = 1, 2, 3
>>> print(type(tupla)) 
<class 'tuple'>
>>> print(tupla)       
(1, 2, 3)
```

Es importante aclarar que si queremos declarar una tupla con un sólo elemento debe incluirse la coma `,` después de este, de lo contrario esa variable no será declarada como una tupla. Por ejemplo,

```python
>>> no_es_tupla = (1)
>>> print(type(no_es_tupla))
<class 'int'>
>>> es_tupla = (1,)
>>> print(type(es_tupla))
<class 'tuple'>
```

El tipo de variable de `no_es_tupla` arroja que es un entero debido a que no incluimos la coma, al agregarla en `es_tupla` ya Python la declara como una tupla.

Como se mencionó anteriormente no se pueden modificar y si lo intentamos obtendremos un error. Veamos qué sucede si intentamos modificarla:

```python
>>> tupla = (1, 2, 3)
>>> tupla[0] = 5
Error! TypeError
```

Al igual que las listas, las tuplas también pueden ser anidadas.

```python
>>> tupla = 1, 2, ('a', 'b'), 3
>>> print(tupla)       
(1, 2, ('a', 'b'), 3)
>>> print(tupla[2][0]) 
a
```

Y también es posible convertir una lista en tupla haciendo uso de al función `tuple()`.

```python
>>> lista = [1, 2, 3]
>>> tupla = tuple(lista)
>>> print(type(tupla)) 
<class 'tuple'>
>>> print(tupla)       
(1, 2, 3)
```

Se puede **iterar** una tupla de la misma forma que se hacía con las listas.

```python
>>> tupla = [1, 2, 3]
>>> for t in tupla:
>>>     print(t) 
1
2
3
```

Y se puede también asignar el valor de una tupla con `n` elementos a `n` variables.

```python
>>> tupla = (1, 2, 3)
>>> x, y, z = tupla
>>> print(x, y, z) 
1 2 3
```

Por último, también es posible concatenar dos tuplas.

```python
>>> tupla_uno = (1,)
>>> tupla_dos = (2, 3, 4)
>>> tupla_uno += tupla_dos
>>> print(tupla_uno)
(1, 2, 3, 4)
```

## Devolviendo una tupla en una función

Se puede devolver una tupla como resultado de una función. 

```python
>>> def cordenadas():
>>>     return (5, 4)
>>>
>>> coordenada = coordenadas()
>>> print(coordenada)
(5, 4)
>>> x, y = coordenadas()
>>> print(x, y)
5 4 
```

## Métodos tuplas

`count(<obj>)`

El método `count()` cuenta el número de veces que el objeto pasado como parámetro se ha encontrado en la lista.

```python
>>> tupla = [1, 1, 1, 3, 5]
>>> print(l.count(1))
3
```

`index(<obj>[,index])`

El método `index()` busca el objeto que se le pasa como parámetro y devuelve el índice en el que se ha encontrado.

```python
>>> tupla = [7, 7, 7, 3, 5]
>>> print(l.index(5)) 
4
```

En el caso de no encontrarse, se devuelve un `ValueError`.

```python
>>> tupla = [7, 7, 7, 3, 5]
>>> print(l.index(35)) 
Error! ValueError
```

El método `index()` también acepta un segundo parámetro opcional, que indica a partir de que índice empezar a buscar el objeto.

```python
>>> tupla = [7, 7, 7, 3, 5]
>>> print(l.index(7, 2)) 
2
```