# Recursividad

Cuando se habla de **recursividad** en el contexto de un algoritmo se refiere a la forma de crear soluciones mediante la división del problema en subtareas cuya funcionalidad es la misma. En el mundo de la programación,  **recursividad** es una técnica mediante la cual una función se llama a sí misma.

 El ejemplo más fácil para entender la recursividad sería con los factoriales. Veamos el siguiente código

```python
def factorial_normal(n):
    r = 1
    i = 2
    while i <= n:
        r *= i
        i += 1
    return r

factorial_normal(5) # 120
```

Dado que el factorial es una tarea que puede ser dividida en subtareas del mismo tipo (multiplicaciones), podemos darle un enfoque recursivo y escribir la función de otra manera.

```python
def factorial_recursivo(n):
    if n == 1:
        return 1
    else:
        return n * factorial_recursivo(n-1)

factorial_recursivo(5) # 120
```

Lo que realmente hacemos con el código anterior es llamar a la función `factorial_recursivo()` múltiples veces. Es decir, `5!` es igual a `5 * 4!` y `4!` es igual a `4 * 3!` y así sucesivamente hasta llegar a 1.

Algo muy importante a tener en cuenta es que si realizamos demasiadas llamadas a la función, podríamos llegar a tener un error del tipo `RecursionError`. Esto se debe a que todas las llamadas van apilándose y creando un contexto de ejecución, algo que podría llegar a causar un `stack overflow`. Es por eso por lo que Python lanza ese error, para protegernos de llegar a ese punto.