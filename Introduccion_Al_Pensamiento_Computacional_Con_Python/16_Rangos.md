# Rangos

Uno de las iteraciones mas comunes que se realizan, es la de iterar un número entre por ejemplo 0 y `n`. Pongamos que queremos iterar una variable `i` de 0 a 5. Haciendo uso de lo que hemos visto anteriormente, podríamos hacer lo siguiente.

```python
for i in (0, 1, 2, 3, 4, 5):
    print(i) #0, 1, 2, 3, 4, 5
```

Sin embargo, hay otras formas de hacer esto en Python, haciendo uso del `range()`.

```python
for i in range(6):
    print(i) #0, 1, 2, 3, 4, 5
```

El `range()` genera una secuencia de números que van desde 0 por defecto hasta el número que se pasa como parámetro menos 1. En realidad, se pueden pasar hasta tres parámetros separados por coma, donde el primer es el inicio de la secuencia, el segundo el final y el tercero el salto que se desea entre números. Por defecto se empieza en 0 y el salto es de 1.

```python
range(inicio, fin, salto)
```

Por lo tanto, si llamamos a `range()` con `(5,20,2)`, se generarán números de 5 a 20 de dos en dos. 

```python
for i in range(5, 20, 2):
    print(i) #5,7,9,11,13,15,17,19
```

Se pueden generar también secuencias inversas, empezando por un número mayor y terminando en uno menor, pero para ello el salto deberá ser negativo.

```python
for i in range (5, 0, -1):
    print(i) #5,4,3,2,1
```

Algunas generalidades de `range()`:

* Al igual que las cadenas y las tuplas, los rangos son inmutables
* Muy eficientes en uso de memoria
* Normalmente utilizados en `for` loops

