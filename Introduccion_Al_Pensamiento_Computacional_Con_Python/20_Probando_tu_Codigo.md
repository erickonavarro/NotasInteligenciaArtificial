# Pruebas de caja negra

Las Pruebas de Caja Negra, es una técnica de pruebas de software en la cual la funcionalidad se verifica sin tomar en cuenta la estructura interna de código, detalles de implementación o escenarios de ejecución internos en el software. En las pruebas de caja negra, nos enfocamos solamente en las entradas y salidas del sistema, sin preocuparnos en tener conocimiento de la estructura interna del programa de software. 

Este tipo de pruebas se utilizan principalmente en dos subramas del *testing*:

* **Unit testing**: Consiste en probar función por función para verificar que todas funcionen adecuadamente.
* **Integration testing**: Consiste en verificar que todos los componentes hagan sinergia entre ellos. 

Extrapolando estas subramas a la electrónica, podemos decir que **unit testing** sería verificar que cada LED encienda de manera individual, mientras que **integration testing** sería comprobar que toda la tira de LED funcione de acuerdo a la secuencia de colores programada. 

## Unit testing

Supongamos que estás desarrollando un programa que sabes te llevará varios meses para terminar. Conforme vas escribiéndolo se va haciendo más y más complejo y cada vez creas nuevas funciones. Mientras lo escribes, por alguna razón decides cambiar el código de una función pero a partir de allí rompes la lógica del programa y no sabes por qué no funciona lo demás pero sí esa función en sí. Aquí es donde entra el **unit testing** pues te permitirá comprobar qué partes del código dejaron de funcionar y cuales sí funcionan.

Veamos un ejemplo donde estás desarrollando una calculadora y tienes el siguiente código `calc.py ` hasta el momento:

```python
def add(x, y):
    """Función de suma"""
    return x + y


def subtract(x, y):
    """Función de resta"""
    return x - y


def multiply(x, y):
    """Función de multiplicar"""
    return x * y


def divide(x, y):
    """Función de división"""
    if y == 0:
        raise ValueError('No puedes dividir entre 0')
    return x / y
```

¿Cómo se te ocurre comprobar con cada corrida si está funcionando? Tal vez pienses en escribir la función `print()` y comprobar los resultados de esa manera. 

```python
>>> print(add(5, 10)) 
15
```

Sin embargo, esta práctica puede ser muy tardada si tienes muchas funciones. Además de que no te está diciendo si la función funciona o no, sólo te devuelve un resultado que quizás podría estar mal. En esta ocasión es solo una suma de dos números pero imagínate que fuera algo mucho más complejo, sería más tardado y complicado saber si está bien.

Para hacer el **unit testing** utilizamos el módulo `unittest` de Python. Así que creamos un nuevo archivo `.py` el cual deberá comenzar con la palabra **test** seguido del nombre del archivo que quieres probar en este caso `calc.py` entonces quedaría `test_calc.py`.

Una vez creado el archivo importamos los módulos `unittest` y el nombre del módulo que quieras probar en este caso `calc.`

```python
import unittest
import calc
```

Necesitamos crear algunos casos de prueba o `TestCase` para las funciones que queremos y para crear esos casos de prueba necesitamos primero crear una clase de prueba que herede de `unittest.TestCase`. El nombre de la clase puede ser el que tu quieras pero recuerda que es una buena práctica en nombrarla de acuerdo al contexto.

```python
class TestCalc(unittest.TestCase):
```

Ahora es necesario escribir un método el cual debe empezar con la palabra `test_` seguido de la función que quieras probar `test_add`

```python
	def test_add(self):
```

Seguramente te hayas fijado en el `self` que se pasa como parámetro de entrada del método. Es una variable que representa la instancia de la clase, y deberá estar siempre ahí.

Para poder comprobar el funcionamiento de la función es necesario utilizar uno de los métodos `assert`. La clase TestCase proporciona varios métodos `assert ` para comprobar e informar de los fallos. La siguiente tabla enumera los métodos más utilizados:

| Method                                                       | Checks that            | New in |
| :----------------------------------------------------------- | :--------------------- | :----- |
| [`assertEqual(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertEqual) | `a == b`               |        |
| [`assertNotEqual(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotEqual) | `a != b`               |        |
| [`assertTrue(x)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertTrue) | `bool(x) is True`      |        |
| [`assertFalse(x)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertFalse) | `bool(x) is False`     |        |
| [`assertIs(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIs) | `a is b`               | 3.1    |
| [`assertIsNot(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNot) | `a is not b`           | 3.1    |
| [`assertIsNone(x)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNone) | `x is None`            | 3.1    |
| [`assertIsNotNone(x)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsNotNone) | `x is not None`        | 3.1    |
| [`assertIn(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIn) | `a in b`               | 3.1    |
| [`assertNotIn(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotIn) | `a not in b`           | 3.1    |
| [`assertIsInstance(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertIsInstance) | `isinstance(a, b)`     | 3.2    |
| [`assertNotIsInstance(a, b)`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.assertNotIsInstance) | `not isinstance(a, b)` | 3.2    |

Para la función `add()` utilizaremos el método `assertEqual` que recibe dos parámetros y comprueba que el primero y el segundo sean iguales. Si los valores no se comparan igual, la prueba fallará. 

```python
class TestCalc(unittest.TestCase):
    def test_add(self):
        result = calc.add(10, 5)
        self.assertEqual(result, 15)
```

Finalmente, agregamos el condicional `if __name__ == '__main__':`

```python
if __name__ == '__main__':
    unittest.main()
```

Entonces el código queda así

```python
import unittest
import calc

class TestCalc(unittest.TestCase):
    def test_add(self):
        result = calc.add(10, 5)
        self.assertEqual(result, 15)


if __name__ == '__main__':
    unittest.main()
```

Desde la terminal corremos el programa y obtenemos lo siguiente

```python
>>> py test_calc.py
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

El primer punto `.` significa que el programa realizó una prueba y después de las líneas `Ran 1 test in 0.000s`nos vuelve a indicar cuántas pruebas hizo y en cuánto tiempo. Al último muestra `OK` diciendo que la prueba funcionó. Cambiemos el segundo parámetro de `self.assertEqual(result, 15)` a `self.assertEqual(result, 12)` para ver qué sale en caso de que falle la prueba.

```python
>>> py test_calc.py
F
======================================================================
FAIL: test_add (__main__.TestCalc)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "D:\Archivos Erick\Cursos\Platzi\Python\Pensamiento computacional\test_calc.py", 
line 7, in test_add
    self.assertEqual(result, 12)
AssertionError: 15 != 12

----------------------------------------------------------------------
Ran 1 test in 0.000s

FAILED (failures=1)
```

La terminal nos indica con una `F`de que una prueba falló, y después nos da el Traceback donde dice que que hubo un `AssertionError: 15 != 12`. Finalmente vuelve a indicar cuántas pruebas hizo, en cuanto tiempo y la leyenda `FAILED (failures=1)`.

NOTA: Es importante que las funciones empiecen con `test_` de lo contrario el programa va a correr y aparentemente no mostrar errores pero en realidad fue porque no realizó la prueba. Veamos qué sucede si cambiamos `def test_add(self)` por `def add_test(self):`

```python
>>> py test_calc.py

----------------------------------------------------------------------
Ran 0 tests in 0.000s

OK
```

Nos arroja `OK` pero si te fijas no hizo ninguna prueba pues dice `Ran 0 tests in 0.000s`.

Ya probamos la función con un solo caso, pero queremos asegurarnos de que pueda funcionar para cualquier otro caso. Entonces es una buena práctica agregar algunas otras pruebas dentro del mismo método de `test_add()`. 

```python
    def test_add(self):
        self.assertEqual(calc.add(10, 5), 15)
        self.assertEqual(calc.add(-1, 1), 0)
        self.assertEqual(calc.add(-1, -1), -2)
```

Seguro notaste que se retiró la línea de `result`, en vez de pasar la variable al método `assertEqual ` ose llama la función `calc.add()` directo en el parámetro de `assertEqual `.

Ahora tenemos otros dos casos que se deben de probar: la suma de un número negativo y uno positivo; y la suma de dos números negativos. Al correrlo obtenemos

```python
>>> py test_calc.py
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```

Verás que dice que se corrió una sola prueba y eso es porque los tres casos que escribimos están dentro de la misma prueba que es `test_add()`. Así que no te dejes engañar por ese `Ran 1 test in 0.000s`  pensando que no se hicieron las tres pruebas de `assertEqual`, porque en realidad sí las ejecutó Python. 

Continuemos agregando los métodos para las otras funciones.

```python
    def test_subtract(self):
        self.assertEqual(calc.subtract(10, 5), 5)
        self.assertEqual(calc.subtract(-1, 1), -2)
        self.assertEqual(calc.subtract(-1, -1), 0)

    def test_multiply(self):
        self.assertEqual(calc.multiply(10, 5), 50)
        self.assertEqual(calc.multiply(-1, 1), -1)
        self.assertEqual(calc.multiply(-1, -1), 1)

    def test_divide(self):
        self.assertEqual(calc.divide(10, 5), 2)
        self.assertEqual(calc.divide(-1, 1), -1)
        self.assertEqual(calc.divide(-1, -1), 1)
        self.assertEqual(calc.divide(5, 2), 2.5)
```

Nótese como se cambiaron los valores de acuerdo a cada tipo de función. Si lo corremos obtenemos:

```python
>>> py test_calc.py
....
----------------------------------------------------------------------
Ran 4 tests in 0.000s

OK
```

Se realizaron 4 pruebas y todas funcionaron. Cambiemos un dato apropósito para que falle la tercera prueba `test_multiply`

```python
>>> py test_calc.py
..F.
======================================================================
FAIL: test_multiply (__main__.TestCalc)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "D:\Archivos Erick\Cursos\Platzi\Python\Pensamiento computacional\test_calc.py", 
line 19, in test_multiply
    self.assertEqual(calc.multiply(-1, 1), 2)
AssertionError: -1 != 2

----------------------------------------------------------------------
Ran 4 tests in 0.001s

FAILED (failures=1)
```

Como se observa, todas pasaron menos la tercera.  Para terminar con este tema, hagamos una prueba para los errores tipo `raise` que en este caso se encuentra en la función `divde`

```python
        with self.assertRaises(ValueError):
            calc.divide(10, 0)
```

Para probarlo utilizamos el método `assertRaises` el cual recibe como parámetro el tipo de Error que en este caso es el `ValueError`, después como argumento llamamos a la función `divide(10, 0)` con el cero como divisor para que efectivamente dé el `ValueError`.  Finalmente el código queda:

```python
import unittest
import calc


class TestCalc(unittest.TestCase):

    def test_add(self):
        self.assertEqual(calc.add(10, 5), 15)
        self.assertEqual(calc.add(-1, 1), 0)
        self.assertEqual(calc.add(-1, -1), -2)

    def test_subtract(self):
        self.assertEqual(calc.subtract(10, 5), 5)
        self.assertEqual(calc.subtract(-1, 1), -2)
        self.assertEqual(calc.subtract(-1, -1), 0)

    def test_multiply(self):
        self.assertEqual(calc.multiply(10, 5), 50)
        self.assertEqual(calc.multiply(-1, 1), -1)
        self.assertEqual(calc.multiply(-1, -1), 1)

    def test_divide(self):
        self.assertEqual(calc.divide(10, 5), 2)
        self.assertEqual(calc.divide(-1, 1), -1)
        self.assertEqual(calc.divide(-1, -1), 1)
        self.assertEqual(calc.divide(5, 2), 2.5)

        with self.assertRaises(ValueError):
            calc.divide(10, 0)

if __name__ == '__main__':
    unittest.main()
```

Con el `assertRaises` nuestro programa ya validará si funciona correctamente el programa en caso de que se realice una división entre cero. 

# Pruebas de Caja de Cristal (Regression testing)

A diferencia de las pruebas de caja negra o **user testing** donde no es necesario conocer la estructura del programa para realizarlas, las **pruebas de caja de cristal** asume que conoces la implementación del código. Algunas generalidades de estas pruebas son:

* Se basan en el flujo del programa
* Prueba todos los caminos posibles de una función, de las ramificaciones, de los bucles `for` y `while`, así como de las recursiones.
* Son buenas cuando descubres un bug al correr el programa o **regression testing**.

# Consejos para arreglar tu código

* Encuentra a los sospechosos comunes.
* En lugar de preguntarte por qué un programa no funciona, pregúntate por qué está funcioanndo de esta manera.
* Es posible que el bug no se encuentra donde crees que está.
* Explícale el problema a otra persona. De preferencia que no tenga contexto. Cómprate un pato de hule (Rubber duck debugging
* Lleva un registro de lo que has tratado, preferentemente en la forma de tests
* Vete a dormir



