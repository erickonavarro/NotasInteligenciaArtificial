# Aproximación de soluciones

Con la enumeración exhaustiva vimos como el programa te entrega el resultado exacto, y en caso de que no exista simplemente no te da nada o te dice que no hay respuesta. Habrá casos en los que necesitemos una solución aproximada si es que no existe una respuesta exacta, para ello se utiliza el algoritmo de **aproximación de soluciones**. 

Este consiste en entregar un resultado con un margen de error al cual llamaremos **épsilon**. En *computer science* debemos elegir entre precisión o rapidez cuando hablamos de soluciones, no se puede tener ambas. Entonces, hay que hacer un *trade-off* y elegir entre cada una de estas características. Ser **preciso** quiere decir que nuestro error (épsilon) serpa lo más pequeño posible, pero puede que tardemos en llegar a esa respuesta. Ser **rápido**, por otro lado, se traduce a obtener la solución lo más rápido posible pero que el error sea más grande. Entonces es tu trabajo como programador decidir cuál ruta tomar. 

Veamos el siguiente código

```python
import time 
start_time = time.time() #para saber el tiempo de ejecución del programa
objetivo = int(input('Escoge un numero: ')) #el usuario ingresa un numero
epsilon = 0.01 # este es el margen de error
paso = epsilon**2  # valor que incrementará en cada iteración
respuesta = 0.0 # el setpoint, el valor desde el que comenzará la 1ra iteración

# mientras que la resta de respuesta´2 - objetivo sea mayor que el margen
# de error, Y que respuesta sea menor que el numero del cual queremos
# saber la raiz cuadrada
while abs(respuesta**2 - objetivo) >= epsilon and respuesta <= objetivo:
    print(abs(respuesta**2 - objetivo), respuesta)
    respuesta += paso

# si la resta de respuesta´2 - objetivo es mayor que el margen de error
if abs(respuesta**2 - objetivo) >= epsilon: 
    print(f'No se encontro la raiz cuadrada {objetivo}')
else: # si la resta no es mayor entonces el resultado es:
    print(f'La raiz cudrada de {objetivo} es {respuesta}')
print("--- %s seconds ---" % (time.time() - start_time))
```

El código anterior se encarga de encontrar la raíz de un número que el usuario ingrese. Se ha definido el margen de error **épsilon** como 0.01; el **paso** que es el valor que aumentará cada iteración para hacer la operación es épsilon´2, y la **respuesta** es el setpoint del programa osea el valor inicial de la primera iteración. 

El bucle `while abs(respuesta**2 - objetivo) >= epsilon and respuesta <= objetivo` se encarga de realizar la operación de elevar el valor actual de *respuesta* y restarlo con el valor de *objetivo*, el cual es el numero del cual queremos encontrar la raíz cuadrada, lo anterior dará el *margen de error* y entonces se compara con *épsilon* el cual tiene un valor de0.01. Si la resta es mayor que el margen de error (osea de épsilon) entonces la respuesta aún no es lo **suficientemente precisa**, de acuerdo a nuestros criterios, por lo que será necesario otra iteración para minimizar este error. Así que al final de cada iteración se aumentará el valor de *respuesta* con *paso* (para este ejercicio es lo mismo que épsilon  al cuadrado).

Finalmente, si el error de la última iteración ES MAYOR que épsilon entonces  diremos que no se encontró respuesta, pero si el error ES MENOR que épsilon se imprimirá el valor de *respuesta*. 

Corriendo el programa e ingresando el número 4 obtenemos:

```python
...
0.011991000000812768 1.9969999999997965
0.01159159000081278 1.9970999999997965
0.011192160000812912 1.9971999999997965
0.010792710000813166 1.9972999999997965
0.010393240000813098 1.9973999999997964
La raiz cudrada de 4 es 1.9974999999997964
--- 1.1786370277404785 seconds ---
```

La raíz cuadrada de 4 es 1.9974999999997964, y tardó 1.17 segundos en llegar a la respuesta. Si revisamos el valor del error tenemos:
$$
1.9974999999997964´2 - 4 = 0.010393240000813098
$$
El error es 0.010393240000813098 lo cual redondeando es igual a nuestra *épsilon* 0.01.  Ahora, si se quiere ser más preciso será necesario modificar el valor de *épsilon*, sin embargo, la velocidad del programa se hará más lenta. Si disminuimos el margen de error a 0.01 este es el resultado que obtendríamos: 

```python
La raiz cudrada de 4 es 1.999749999925672
--- 3.1019177436828613 seconds ---
```

Llegó al resultado de 1.999749999925672 en 3.10 segundos, si lo comparamos con la respuesta anterior, el número se acerca aún más a 2, pero tardó casi el doble de tiempo en obtenerlo. Si disminuimos *épsilon* a 0.001 obtenemos: 

```python
La raiz cudrada de 4 es 1.999975006212548
--- 64.43787026405334 seconds ---
```

Llegando a la solución 1.999975006212548 ¡pero en 64 segundos!. Con los ejemplos anteriores podemos comprobar que si queremos una respuesta más precisa, se traduce en tiempos más largos para llegar al resultado. 