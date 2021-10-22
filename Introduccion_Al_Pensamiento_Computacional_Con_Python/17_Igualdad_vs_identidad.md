# Igualdad vs Identidad

Las personas que son nuevas en el lenguaje de programación Python pueden confundirse un poco con la diferencia entre "==" (igualdad) y la palabra clave de Python "is" (identidad). 

## Igualdad en Python

Muchos lenguajes de programación tienen el concepto de igualdad y varios utilizan el doble signo de igualdad ("==") para designar este concepto. Veamos la igualdad en acción:

```python
>>> num = 1
>>> num_two = num
>>> num == num_two
True
```

Aquí creamos una variable que llamamos `num ` y la asignamos al entero 1. A continuación creamos una segunda variable llamada `num_dos ` y la asignamos al valor de `num`. Finalmente preguntamos a Python si `num` y `num_dos` son iguales. En este caso, Python nos dice que esta expresión es `Verdadera`.

Otra forma de pensar en la igualdad es que estamos preguntando a Python si dos variables contienen lo mismo. En el ejemplo anterior, ambas contienen el número entero 1. Veamos qué ocurre cuando creamos dos listas con los mismos valores:

```python
>>> list_one = [1, 2, 3]
>>> list_two = [1, 2, 3]
>>> list_one == list_two
True
```

Esto ha funcionado como esperábamos.

Ahora veamos qué ocurre si preguntamos a Python por su identidad:

```python
>>> num is num_two
True
>>> list_one is list_two
False
```

¿Qué ha pasado aquí? El primer ejemplo devuelve True, pero el segundo devuelve False. Lo veremos en la siguiente sección.

## Identidad en Python

Cuando se pregunta a Python si un objeto es igual a otro, se está preguntando si tienen la misma identidad. ¿Son realmente el mismo objeto? En el caso de `num `y `num_two`, la respuesta es sí. Python proporciona una manera fácil de demostrarlo a través de su función incorporada `id()`:

```python
>>> id(num)
10914368
>>> id(num_two)
10914368
```

La razón por la que estas dos variables comparten la misma identidad es porque le dijimos a Python que debían hacerlo cuando asignamos `num ` a `num_dos` (es decir,`num_dos`= `num`). Si utilizas la función `id() `de Python en los dos objetos de la lista, verás rápidamente que tienen identidades diferentes:

```python
>>> id(list_one)
140401050827592
>>> id(list_two)
140401050827976
```

Por lo tanto, cuando se le pregunta a Python `list_one is list_two`, se obtiene `False`. Tenga en cuenta que también puede preguntar a Python si un objeto no es otro objeto:

```python
>>> list_one = [1, 2, 3]
>>> list_two = [1, 2, 3]
>>> list_one is not list_two
True
```

