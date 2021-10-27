# Assert Statements en Python

Además de manejar errores con try, except y raise, podemos utilizar los **Assert Statements**, osea las afirmaciones en Python. El flujo de un **Assert Statement** es el siguiente:

<img src='https://i.imgur.com/gAe2EUj.png' width="500" align="center">

Tenemos nuestro código, después llega el **Assert statement** y se ejecuta el código dentro de la afirmación, si es verdadero el código sigue, si es falso entonces devuelve un error.

La estructura es la siguiente:

```python
assert condición, mensaje de error
```

Básicmanete se lee como: "Afirmo que esta condición es verdadera, de lo contrario entrega este mensaje".

Ejemplo, tenemos la siguiente función con código normal

```python
>>> def palindrome(string):
>>>     return string == string[::-1]
>>>
>>> print(palindrome(""))
True
```

Podemos utilizar un **Assert Statement** para que devuelve un error en caso de que se ponga una cadena vacía.

```python
>>> def palindrome(string):
>>>     assert len(string) > 0, "No se puede ingresar una cadena vacía"
>>>     return string == string[::-1]
>>> print(palindrome(""))
---------------------------------------------------------------------------
AssertionError                            Traceback (most recent call last)
~\AppData\Local\Temp/ipykernel_20784/3369178012.py in <module>
      2     assert len(string) > 0, "No se puede ingresar una cadena vacía"
      3     return string == string[::-1]
----> 4 print(palindrome(""))

~\AppData\Local\Temp/ipykernel_20784/3369178012.py in palindrome(string)
      1 def palindrome(string):
----> 2     assert len(string) > 0, "No se puede ingresar una cadena vacía"
      3     return string == string[::-1]
      4 print(palindrome(""))

AssertionError: No se puede ingresar una cadena vacía
```

Como comprobamos, nos arroja el mensaje:

```python
AssertionError: No se puede ingresar una cadena vacía
```

Las afirmaciones son para errores del programador, no errores del usuario. Para los errores de los que se puede recuperar (como un archivo que no se encuentra o el usuario ingresa datos no válidos), genere una excepción en lugar de detectarla con una afirmación.

