# Especificaciones del código

Cuando se crea un código y quiere ser compartido es necesario que expliquemos de manera concisa cómo funciona nuestro código y así otras personas puedan entenderlo. 

Los **docstrings** de Python son los literales de cadena que aparecen justo después de la definición de una función, método, clase o módulo. Tomemos un ejemplo.

Veamos un ejemplo:

```python
def square(n):
    '''Toma un número n, devuelve el cuadrado de n'''
    return n**2
```

Dentro de las comillas triples está el `docstring ` de la función ` square()` tal y como aparece justo después de su definición.

Si desde la consola de Python escribimos `help(square)` entonces imprimirá lo siguiente:

```python
Help on function square in module __main__:
square(n)
	Toma un número n, devuelve el cuadrado de n
```

También podemos utilizar las comillas triples `"""` para crear `docstrings`.

## Python Comments vs Docstrings

Comentarios en Python

Los comentarios son descripciones que ayudan a los programadores a entender mejor la intención y funcionalidad del programa. Son completamente ignorados por el intérprete de Python.

En Python, usamos el símbolo `#` para escribir un comentario de una sola línea. Por ejemplo,

```python
# Program to print "Hello World"
print("Hello World") 
```

## Python __doc__ attribute

Cuando los literales de cadena están presentes justo después de la definición de una función, módulo, clase o método, se asocian al objeto como su atributo `__doc__`. Más tarde podemos utilizar este atributo para recuperar este `docstring`.

Por ejemplo,

```python
def square(n):
    '''Toma un número n, devuelve el cuadrado de n'''
    return n**2

print(square.__doc__)
```

Al ejecutar el código anterior obtendremos

```python
Toma un número n, devuelve el cuadrado de n
```

## Docstrings de una línea en Python

Los docstrings de una sola línea son los documentos que caben en una sola línea.

Las convenciones estándar para escribir docstrings de una sola línea:

* Aunque sean de una sola línea, seguimos utilizando las comillas triples alrededor de estos docstrings, ya que pueden ampliarse fácilmente más adelante.
* Las comillas de cierre están en la misma línea que las de apertura.
* No hay ninguna línea en blanco ni antes ni después del docstring.
* No deben ser descriptivos, sino que deben seguir la estructura "Haz esto, devuelve aquello" terminando con un punto.

## Docstrings de varias líneas en Python

Las docstrings de varias líneas constan de una línea de resumen, igual que una docstring de una línea, seguida de una línea en blanco, seguida de una descripción más elaborada.

### Docstrings para módulos de Python

* Los docstrings para los módulos de Python deben listar todas las clases, funciones, objetos y excepciones disponibles que se importan cuando se importa el módulo.
* También deben tener un resumen de una línea para cada elemento.

### Docstrings para funciones de Python

* El docstring de una función o método debe resumir su comportamiento y documentar sus argumentos y valores de retorno.
* También debe listar todas las excepciones que se pueden plantear y otros argumentos opcionales.

### Docstrings para clases de Python

* Los docstrings de las clases deben resumir su comportamiento y listar los métodos públicos y las variables de instancia.
* Las subclases, los constructores y los métodos deben tener sus propios docstrings.

### Docstrings para scripts de Python

* Los docstrings para scripts de Python deben documentar las funciones del script y la sintaxis de la línea de comandos como un mensaje utilizable.
* Debe servir como una referencia rápida a todas las funciones y argumentos.

### Docstrings para paquetes Python

La documentación de un paquete Python se escribe en el archivo __init__.py del paquete.

* Debe contener todos los módulos y subpaquetes disponibles exportados por el paquete.

