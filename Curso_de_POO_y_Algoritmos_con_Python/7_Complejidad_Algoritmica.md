# Complejidad algorítmica

## Introducción a la complejidad algorítmica

La **complejidad algorítmica** nos permite comparar la eficiencia de 2 algoritmos, esto a su vez va a predecir el tiempo que va a tomar resolver un problema. No solamente podemos analizar la complejidad desde la perspectiva **temporal**, también la podemos hacer desde la **espacial**, como por ejemplo cuánto espacio en memoria necesitamos.

La complejidad algorítmica temporal la podemos definir como **T(n)** el cual determinara el tiempo que demora en resolver nuestro algoritmo.

## Aproximaciones

¿Como podríamos aplicar nuestra función **T(n)**?

* Cronometrar el tiempo en el que corre un algoritmo. Sin embargo no es una buena forma de medir los algoritmos, ya que no se puede predecir cuanto demorara a medida que crece nuestros pasos.

* Contar los pasos con una medida abstracta de operación. Nos puede acercar a una medición ideal, sin embargo varia mucho de algoritmo en algoritmo y a medida que crece nuestro dataset existen muchos términos que llegan a ser irrelevantes.

* Contar los pasos conforme nos aproximamos al infinito pero con una medida asintótica.

## Medición temporal

Para una realizar una medida temporal simplemente calculamos la diferencia del tiempo previo y posterior de la ejecución del algoritmo.

```python
import time
import sys

sys.setrecursionlimit(100000)

def factorial(n):
    respuesta = 1

    while n > 1:
        respuesta *= n
        n -= 1

    return respuesta


def factorial_r(n):
    if n == 1:
        return 1

    return n * factorial(n - 1)


if __name__ == '__main__':
    n = 100000

    comienzo = time.time()
    factorial(n)
    final = time.time()
    print(final - comienzo)

    comienzo = time.time()
    factorial_r(n)
    final = time.time()
    print(final - comienzo)
    
#2.3874197006225586
#2.3899195194244385
```

## Conteo abstracto de operación

Con esta técnica contamos los pasos que realiza nuestro algoritmo. En el siguiente ejemplo `contador` tendrá los números de pasos que realiza nuestro código al ejecutar y `respuesta` arroja el resultado del polinomio 1000 + x + 2x^2.

```python
def f(x):

    contador = 0
    respuesta = 0

    contador += 1
    
    
    for i in range(1000):
        respuesta += 1
        contador += 1

    for i in range(x):
        respuesta += 1
        contador += 1

    for i in range(x):
        for j in range(x):
            respuesta += 1
            contador += 1
            respuesta += 1
            contador += 1
 
    
    contador += 1   
    print(f'El valor de contador es contador: ', contador)     
    return respuesta

if __name__ == '__main__':
    print(f'El valor de respuesta es: ', f(5))
    
#El valor de contador es contador:  1057
#El valor de respuesta es:  1055
```

El código anterior nos puede decir cuántas OPERACIONES se realizan para llegar al resultado. La variable `contador` es la encargada de hacer este conteo, cada vez que se realiza una operación, sea de asignar una variable, sumar o de devolver un valor, se le suma un 1. 

Entonces,  `contador` comienza con el valor de `0` y después de la línea de `respuesta = 0` , se la suma 1 a `contador`.  Durante el primer `for` se le va agregando un 1 cada vez que se hace una iteración, y como el valor de `range()` es 1000, entonces se le sumará un 1 esta cantidad de veces. Después en el segundo `for` se le va a sumar un 1 x número de veces, en esta ocasión 5. En el último `for` se le sumará un 1 en cada iteración de `i` y `j`.



## Notación asintótica.

Cuando hablamos de notación asintótica no importan las variaciones pequeñas, el enfoque se centra en lo que pasa conforme el tamaño del problema se acerca al infinito.

Siempre tenemos que estar preparados para cualquier caso, por lo que tenemos que saber medir a nuestro algoritmo en el mejor, promedio y peor de los casos.

Lo mejor que nos permite comparar nuestros algoritmos y su capacidad es medir el peor de los casos, ahí es donde entra el Big O notation, donde lo único que importa es el termino de mayor tamaño, sin importar las constantes que las acompañan.

En el siguiente código es una representación de un crecimiento lineal. 

```python
# Ley de la suma

def f(n):
    for i in range(n):
        print(i)

    for i in range(n):
        print(i)

# En este caso el mayor término es n
# O(n) + O(n) = O(n + n) = O(2n) = O(n)
```

En los siguientes ejemplos podemos ver que la función tiene un crecimiento cuadrático

```python
def f(n):
    for i in range(n):
        print(i)

    for i in range(n * n):
        print(i)

# En este caso el mayor término es n²
# O(n) + O(n * n) = O(n + n²) = O(n²)

def p(n):

    for i in range(n):

        for i in range(n):
            print(i, j)

# En este caso el mayor término es n²
# O(n) + O(n * n) = O(n * n) = O(n²)
```

Por último, un programa donde el crecimiento es exponencial

```python
# Recursividad múltiple

def fibonacci(n):

    if n == 0 or n == 1:
        return 1

    return fibonacci(n - 1) +  fibonacci(n - 2)

# En este caso el mayor término es 2**n (el símbolo ** denota "elevado a"),
# ya que real
```

## Clases de complejidad algorítmica

Existen distintos tipos de complejidad algorítmica:

- **O(1) Constante:** no importa la cantidad de input que reciba, siempre demorara el **mismo tiempo**.
- **O(n) Lineal:** la complejidad crecerá de forma **proporcional** a medida que crezca el input.
- **O(log n) Logarítmica:** nuestra función crecerá de forma **logarítmica** con respecto al input. Esto significa que en un inicio crecerá rápido, pero luego se estabilizara.
- **O(n log n) Log lineal:** crecerá de forma **logarítmica** pero junto con una **constante**.
- **O(n²) Polinomial:** crecen de forma cuadrática. No son recomendables a menos que el input de datos sea pequeño.
- **O(2^n) Exponencial:** crecerá de forma **exponencial**, por lo que la carga es muy alta. Para nada recomendable en ningún caso, solo para análisis conceptual.
- **O(n!) Factorial:** crece de forma **factorial**, por lo que al igual que el exponencial su carga es muy alta, por lo que jamás utilizar algoritmos de este tipo.

A continuación podemos ver la representación gráfica de estas clases conforme se acercan a infinito.

<div align="center"> 
  <img src="Imagenes/big-o-complexity-chart.png" width="70%">
</div>

Para que dimensiones mejor cada una de estas clases veamos la siguiente tabla con una función de cada tipo.

<div align="center"> 
  <img src="Imagenes/grafica_big_o.png" width="70%">
</div>

