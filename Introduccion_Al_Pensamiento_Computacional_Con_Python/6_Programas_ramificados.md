## Programas ramificados

De no ser por las **estructuras de control**, el código en cualquier lenguaje de programación sería ejecutado secuencialmente hasta terminar. Un código, no deja de ser un conjunto de instrucciones que son ejecutadas unas tras otra. Gracias a las estructuras de control, podemos **cambiar el flujo de ejecución de un programa**, haciendo que ciertos bloques de código se ejecuten si y solo si se dan unas condiciones particulares.

## Uso del if

Un ejemplo sería si tenemos dos valores `a` y `b` que queremos dividir. Antes de entrar en el bloque de código que divide `a/b`, sería importante verificar que `b` es distinto de cero, ya que la división por cero no está definida. Es aquí donde entran los condicionales `if`.

```python
>>>a = 4
>>>b = 2
>>>if b != 0:
>>>    print(a/b)
2
```

En este ejemplo podemos ver como se puede usar un `if` en Python. Con el operador `!=` se comprueba que el número `b` sea distinto de cero, y si lo es, se ejecuta el código que está identado. Por lo tanto un `if` tiene dos partes:

- La **condición** que se tiene que cumplir para que el bloque de código se ejecute, en nuestro caso `b!=0`.
- El **bloque de código** que se ejecutará si se cumple la condición anterior.

Es muy importante tener en cuenta que la sentencia `if` debe ir terminada por `:` y el bloque de código a ejecutar debe estar identado. Si usas algún editor de código, seguramente la identación se producirá automáticamente al presionar enter. Nótese que el bloque de código puede también contener más de una línea, es decir puede contener más de una instrucción.

```python
>>>a = 4
>>>b = 2
>>>if b != 0:
>>>    c = a/b
>>>    d = c + 1
>>>    print(d)
3
```

Todo lo que vaya después del `if` y esté identado, será parte del bloque de código que se ejecutará si la condición se cumple. Por lo tanto el segundo `print()` “Fuera if” será ejecutado siempre, ya que está fuera del bloque `if`.

```python
>>>a = 4
>>>b = 2
>>>if b != 0:
>>>    c = a/b
>>>    print("Dentro if")
>>>print("Fuera if")
2
'Dentro if'
'Fuera if'

```

## Uso de else y elif

Es posible que no solo queramos hacer algo si una determinada condición se cumple, sino que además queramos hacer algo de lo contrario. Es aquí donde entra la cláusula `else`. La parte del `if` se comporta de la manera que ya hemos explicado, con la diferencia que si esa condición no se cumple, se ejecutará el código presente dentro del `else`. Nótese que ambos bloque de código son excluyentes, se entra o en uno o en otro, pero nunca se ejecutarán los dos.

```python
>>>x = 5
>>>if x == 5:
>>>    print("Es 5")
>>>else:
>>>    print("No es 5")
'Es 5'
```

Hasta ahora hemos visto como ejecutar un bloque de código si se cumple una instrucción, u otro si no se cumple, pero no es suficiente. En muchos casos, podemos tener varias condiciones diferentes y para cada una queremos un código distinto. Es aquí donde entra en juego el `elif`.

```python
>>>x = 6
>>>if x == 5:
>>>    print("Es 5")
>>>elif x == 6:
>>>    print("Es 6")
>>>elif x == 7:
>>>    print("Es 7")
'Es 6'
```

Con la cláusula `elif` podemos ejecutar tantos bloques de código distintos como queramos según la condición. Traducido al lenguaje natural, sería algo así como decir: si es igual a 5 haz esto, si es igual a 6 haz lo otro, si es igual a 7 haz lo otro.

Se puede usar también de manera conjunta todo, el `if` con el `elif` y un `else` al final. Es muy importante notar que `if` y `else` solamente puede haber uno, mientras que `elif` puede haber varios.

```python
>>>x = 10
>>>if x == 5:
    print("Es 5")
>>>elif x == 6:
    print("Es 6")
>>>elif x == 7:
    print("Es 7")
>>>else:
    print("Es otro")
'Es otro'
```