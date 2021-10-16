# Búsqueda Binaria

La **búsqueda binaria**, también conocida como búsqueda de intervalo medio o búsqueda logarítmica, es un algoritmo de búsqueda que encuentra la posición de un valor en un array ordenado. Compara el valor con el elemento en el medio del array, si no son iguales, la mitad en la cual el valor no puede estar es eliminada y la búsqueda continúa en la mitad restante hasta que el valor se encuentre.

Un resumen del algoritmo de búsqueda binaria sería:

* Ordena la lista o matriz que tienes en orden ascendente.
* El elemento inicial se llama 'L' y el elemento final se llama 'R'. A partir de estos valores intentamos acotar el elemento del medio utilizando la fórmula (L+R)//2. Esta operación consigue el elemento central deseado. 
* El siguiente paso es comprobar si el valor del elemento central es equivalente al valor deseado. Si la respuesta es afirmativa, la búsqueda es satisfactoria y puede terminarse.
* Si el valor deseado es menor que el elemento del medio, se eliminan todos los valores desde el elemento del medio hasta el valor 'R'. Y se repiten los pasos 2 y 3.
* Si el valor deseado es mayor que el elemento central, se eliminan todos los valores desde el elemento central hasta el valor 'L'. Y se repiten los pasos 2 y 3.

El siguiente diagrama es una representación de un array ordenado con 17 elementos. Intentamos localizar la posición del elemento 7. Analicemos el procedimiento paso a paso de cómo se realiza esta tarea.

<img src="https://miro.medium.com/max/700/0*z0or8YYfj3dUmL_h.png" alt="drawing" width="500"/>

El diagrama anterior contiene una lista de 17 elementos que van de 0 a 16. El primer paso es dividir la lista bisecándola en dos mitades con la fórmula antes mencionada de (L+R)//2 que sería (16+0)//2 y devolvería un valor de 8.

El elemento de la 8ª posición es 14, pero el valor deseado es 7. Por lo tanto, se pueden eliminar todos los elementos desde la 8ª posición hasta la última. Y los pasos 2 y 3 pueden repetirse de nuevo. (0+7)//2 devolvería una posición de 3 y el valor de 6. El valor deseado es mayor que el valor encontrado. Por lo tanto, podemos seguir el quinto paso y repetir el paso 2 y el paso 3 de nuevo.

Finalmente, el valor de 4 se puede encontrar con éxito con este procedimiento del algoritmo de búsqueda binaria.

Cabe recalcar que la **búsqueda binaria** sólo funcionará cuando el conjunto esté ordenado, de lo contrario no se puede usar. 

Veamos el siguiente ejemplo:

```python
import time 
start_time = time.time() #para saber el tiempo de ejecución del programa
objetivo = int(input('Escoge un numero: ')) #el usuario ingresa un numero
epsilon = 0.001 # este es el margen de error
bajo = 0.0 # el valor inferior de la cadena
alto = max(1.0, objetivo) #el valor superior de la cadena
respuesta = (alto + bajo) / 2 #se encuentra el valor medio de la cadena


# Compara el valor de la resta del cuadrado de la respuesta menos el
# objetivo con el valor de epsilon, si es mayor el bucle sigue
while abs(respuesta**2 - objetivo) >= epsilon:
    print(f'bajo={bajo}, alto={alto}, respuesta={respuesta}')
    if respuesta**2 < objetivo: # si el objetivo es menor que el cuadrado de respuesta
        bajo = respuesta
    else:
        alto = respuesta

    respuesta = (alto + bajo) / 2 # vuelve a encontrar un valor medio 

print(f'La raiz cuadrada de {objetivo} es {respuesta}')

print("--- %s seconds ---" % (time.time() - start_time)) #imprime los segundos 

```

Comenzamos declarando las variables:

* **objetivo** es el número que el usuario ingresa del cual quiere conocer su raíz cuadrada
* **épsilon** es el margen de error
* **bajo** es el valor inferior, o el valor inicial de la cadena
* **alto** es el valor superior, o el último valor de la cadena. Nota que se ha utilizado la función `max(1.0, objetivo)` la cual devuelve el valor máximo entre estas dos cantidades. Si el número objetivo es menor que 1, entonces el valor de alto será 1, en caso contrario y el valor de objetivo es mayor que 1 entonces el valor de alto es igual a objetivo. 
* **respuesta** es el valor medio de la cadena, se obtiene sumando el valor inferior con el superior y dividendo el resultado entre 2. 

Durante el bucle `while abs(respuesta**2 - objetivo) >= epsilon` se compara si el valor del cuadrado de *respuesta* menos el *objetivo* es mayor o igual que el *margen de error*. En caso de que el *cuadrado de* *respuesta* sea menor que *objetivo* entonces se iguala la variable *bajo* al valor de *respuesta*, de lo contrario se iguala *alto* con *respuesta*. Al final de cada iteración, se vuelve a encontrar el valor medio con `respuesta = (alto + bajo)`.

Entonces, encontremos la raíz cuadrada de 25

```python
Escoge un numero: 25
bajo=0.0, alto=25, respuesta=12.5
bajo=0.0, alto=12.5, respuesta=6.25
bajo=0.0, alto=6.25, respuesta=3.125
bajo=3.125, alto=6.25, respuesta=4.6875
bajo=4.6875, alto=6.25, respuesta=5.46875
bajo=4.6875, alto=5.46875, respuesta=5.078125
bajo=4.6875, alto=5.078125, respuesta=4.8828125
bajo=4.8828125, alto=5.078125, respuesta=4.98046875
bajo=4.98046875, alto=5.078125, respuesta=5.029296875
bajo=4.98046875, alto=5.029296875, respuesta=5.0048828125
bajo=4.98046875, alto=5.0048828125, respuesta=4.99267578125
bajo=4.99267578125, alto=5.0048828125, respuesta=4.998779296875
bajo=4.998779296875, alto=5.0048828125, respuesta=5.0018310546875
bajo=4.998779296875, alto=5.0018310546875, respuesta=5.00030517578125
bajo=4.998779296875, alto=5.00030517578125, respuesta=4.999542236328125
La raiz cuadrada de 25 es 4.9999237060546875
--- 2.5320136547088623 seconds ---
```

Los primeros valores son *bajo=0.0, alto=25, respuesta=12.5*, respuesta es 12.5 porque `respuesta = (alto + bajo) / 2`: 
$$
respuesta = (25 + 0.0) / 2 = 12.5
$$
Y en cada iteración el valor de *respuesta* va cambiando, pero son los valores de *bajo* y *alto* los que cambian dependiendo del resultado de la comparación de `respuesta**2 < objetivo`. Entonces el resultado es 4.9999237060546875, nótese como sólo tardo 2.53 segundos utilizando un margen de error de 0.001. Este método hace que lleguemos al resultado en menos iteraciones, haciendo el algoritmo más rápido comparado con el de **enumeración exhaustiva** o **aproximación de soluciones**. 

Notas para el curso de Introducción al pensamiento computacional con Python
Por Erick Navarro