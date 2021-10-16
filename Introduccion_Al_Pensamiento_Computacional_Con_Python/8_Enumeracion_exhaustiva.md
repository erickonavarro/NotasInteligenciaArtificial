# Enumeración exhaustiva

Es un algoritmo también llamado "adivina y verifica" el cual consiste en enumerar todas las posibilidades. En otras palabras, probará cada posibilidad una por una hasta encontrar la solución. Por ejemplo, el siguiente código se encarga de encontrar si un número tiene raíz cuadrada exacta. 

```python
objetivo = int(input('Escoge un entero: '))
respuesta = 0

while respuesta**2 < objetivo:
    print(f"{respuesta} al cuadrado es {respuesta**2}")
    respuesta += 1

if respuesta**2 == objetivo:
    print(f'La raiz cuadrada de {objetivo} es {respuesta}')
else:
    print(f'{objetivo} no tiene una raiz cuadrada exacta')
```

 La manera en la que funciona es que el programa comenzará desde el 0 a analizar si dicho número es la raíz cuadrada exacta del número que se ha introducido.  Si se introduce el 25 esto es lo que se obtendría:

```python
Escoge un entero: 25
0 al cuadrado es 0
1 al cuadrado es 1
2 al cuadrado es 4
3 al cuadrado es 9
4 al cuadrado es 16
La raiz cuadrada de 25 es 5
```

Observa cómo el programa elevó al cuadrado cada número desde el 0 hasta llegar al 5 y encontrar la respuesta. Si piensas que este método puede ser lento, pues no lo es, debido a que para las máquinas es muy sencillo hacer cálculos de manera rápida. Si pruebas con el número 998,001 el cual su raíz cuadrada es 999, al programa le tomaría sólo una fracción de segundo llegar a la respuesta. 

```python
...
991 al cuadrado es 982081
992 al cuadrado es 984064
993 al cuadrado es 986049
994 al cuadrado es 988036
995 al cuadrado es 990025
996 al cuadrado es 992016
997 al cuadrado es 994009
998 al cuadrado es 996004
La raiz cuadrada de 998001 es 999
```

