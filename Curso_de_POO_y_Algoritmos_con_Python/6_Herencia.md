Fuente: https://ellibrodepython.com/herencia-en-python

# Herencia

La **herencia** es un proceso mediante el cual se puede crear una clase **hija** que hereda de una clase **padre**, compartiendo sus métodos y atributos. Además de ello, una clase hija puede sobreescribir los métodos o atributos, o incluso definir unos nuevos.

Se puede crear una clase hija con tan solo pasar como parámetro la clase de la que queremos heredar. En el siguiente ejemplo vemos como se puede usar la herencia en Python, con la clase `Perro` que hereda de `Animal`. Así de fácil.

```python
# Definimos una clase padre
class Animal:
    pass

# Creamos una clase hija que hereda de la padre
class Perro(Animal):
    pass
```

De hecho podemos ver como efectivamente la clase `Perro` es la hija de `Animal` usando `__bases__`

```python
print(Perro.__bases__)
# (<class '__main__.Animal'>,)
```

De manera similar podemos ver que clases descienden de una en concreto con `__subclasses__`.

```python
print(Animal.__subclasses__())
# [<class '__main__.Perro'>]
```

¿**Y para que queremos la herencia?** Dado que una clase hija hereda los atributos y métodos de la padre, nos puede ser muy útil cuando tengamos clases que se parecen entre sí pero tienen ciertas particularidades. En este caso en vez de definir un montón de clases para cada animal, podemos tomar los elementos comunes y crear una clase Animal de la que hereden el resto.

## Extendiendo y modificando métodos

Continuemos con nuestro ejemplo de perros y animales. Vamos a definir una clase padre `Animal` que tendrá todos los atributos y métodos genéricos que los animales pueden tener. Esta tarea de buscar el denominador común es muy importante en programación. Veamos los atributos:

- Tenemos la **especie** ya que todos los animales pertenecen a una.
- Y la **edad**, ya que todo ser vivo nace, crece, se reproduce y muere.

Y los métodos o funcionalidades:

- Tendremos el método **hablar**, que cada animal implementará de una forma. Los perros ladran, las abejas zumban y los caballos relinchan.
- Un método **moverse**. Unos animales lo harán caminando, otros volando.
- Y por último un método **descríbeme** que será común.

Definimos la clase padre, con una serie de atributos comunes para todos los animales como hemos indicado.

```python
class Animal:
    def __init__(self, especie, edad):
        self.especie = especie
        self.edad = edad

    # Método genérico pero con implementación particular
    def hablar(self):
        # Método vacío
        pass

    # Método genérico pero con implementación particular
    def moverse(self):
        # Método vacío
        pass

    # Método genérico con la misma implementación
    def describeme(self):
        print("Soy un Animal del tipo", type(self).__name__)
```

Tenemos ya por lo tanto una clase genérica `Animal`, que generaliza las características y funcionalidades que todo animal puede tener. Ahora creamos una clase `Perro` que hereda del `Animal`. Como primer ejemplo vamos a crear una clase vacía, para ver como los métodos y atributos son heredados por defecto.

```python
# Perro hereda de Animal
class Perro(Animal):
    pass

mi_perro = Perro('mamífero', 10)
mi_perro.describeme()
# Soy un Animal del tipo Perro
```

Con tan solo un par de líneas de código, hemos creado una clase nueva que tiene todo el contenido que la clase padre tiene, pero aquí viene lo que es de verdad interesante. Vamos a crear varios animales concretos y sobreescrbir algunos de los métodos que habían sido definidos en la clase `Animal`, como el `hablar` o el `moverse`, ya que cada animal se comporta de una manera distinta.

Podemos incluso crear nuevos métodos que se añadirán a los ya heredados, como en el caso de la `Abeja` con `picar()`.

```python
class Perro(Animal):
    def hablar(self):
        print("Guau!")
    def moverse(self):
        print("Caminando con 4 patas")

class Vaca(Animal):
    def hablar(self):
        print("Muuu!")
    def moverse(self):
        print("Caminando con 4 patas")

class Abeja(Animal):
    def hablar(self):
        print("Bzzzz!")
    def moverse(self):
        print("Volando")
    # Nuevo método
    def picar(self):
        print("Picar!")
```

Por lo tanto ya podemos crear nuestros objetos de esos animales y hacer uso de sus métodos que podrían clasificarse en tres:

- Heredados directamente de la clase padre: `describeme()`
- Heredados de la clase padre pero modificados: `hablar()` y `moverse()`
- Creados en la clase hija por lo tanto no existentes en la clase padre: `picar()`

```python
mi_perro = Perro('mamífero', 10)
mi_vaca = Vaca('mamífero', 23)
mi_abeja = Abeja('insecto', 1)

mi_perro.hablar()
mi_vaca.hablar()
# Guau!
# Muuu!

mi_vaca.describeme()
mi_abeja.describeme()
# Soy un Animal del tipo Vaca
# Soy un Animal del tipo Abeja

mi_abeja.picar()
# Picar!
```

## Uso de super()

En pocas palabras, la función `super()` nos permite acceder a los métodos de la clase padre desde una de sus hijas. Volvamos al ejemplo de `Animal` y `Perro`.

```python
class Animal:
    def __init__(self, especie, edad):
        self.especie = especie
        self.edad = edad        
    def hablar(self):
        pass

    def moverse(self):
        pass

    def describeme(self):
        print("Soy un Animal del tipo", type(self).__name__)
```

Tal vez queramos que nuestro `Perro` tenga un parámetro extra en el constructor, como podría ser el `dueño`. Para realizar esto tenemos dos alternativas:

- Podemos crear un nuevo `__init__` y guardar todas las variables una a una.
- O podemos usar `super()` para llamar al `__init__` de la clase padre que ya aceptaba la `especie` y `edad`, y sólo asignar la variable nueva manualmente.

```python
class Perro(Animal):
    def __init__(self, especie, edad, dueño):
        # Alternativa 1
        # self.especie = especie
        # self.edad = edad
        # self.dueño = dueño

        # Alternativa 2
        super().__init__(especie, edad)
        self.dueño = dueño
mi_perro = Perro('mamífero', 7, 'Luis')
mi_perro.especie #mamifero
mi_perro.edad #7
mi_perro.dueño #Luis
```

## Herencia múltiple

En Python es posible realizar **herencia múltiple**. En otros posts hemos visto como se podía crear una clase padre que heredaba de una clase hija, pudiendo hacer uso de sus métodos y atributos. La herencia múltiple es similar, pero una clase **hereda de varias clases** padre en vez de una sola.

Veamos un ejemplo. Por un lado tenemos dos clases `Clase1` y `Clase2`, y por otro tenemos la `Clase3` que hereda de las dos anteriores. Por lo tanto, heredará todos los métodos y atributos de ambas.

```python
class Clase1:
    pass
class Clase2:
    pass
class Clase3(Clase1, Clase2):
    pass
```

Es posible también que una clase herede de otra clase y a su vez otra clase herede de la anterior.

```python
class Clase1:
    pass
class Clase2(Clase1):
    pass
class Clase3(Clase2):
    pass
```

Llegados a este punto nos podemos plantear lo siguiente. Vale, como sabemos de otros posts las clases hijas heredan los métodos de las clases padre, pero también pueden reimplementarlos de manera distinta. Entonces, si llamo a un método que todas las clases tienen en común ¿a cuál se llama?. Pues bien, existe una forma de saberlo.

La forma de saber a que método se llama es consultar el **MRO** o *Method Order Resolution*. Esta función nos devuelve una tupla con el orden de búsqueda de los métodos. Como era de esperar se empieza en la propia clase y se va subiendo hasta la clase padre, de izquierda a derecha.

```python
class Clase1:
    pass
class Clase2:
    pass
class Clase3(Clase1, Clase2):
    pass

print(Clase3.__mro__)
# (<class '__main__.Clase3'>, <class '__main__.Clase1'>, <class '__main__.Clase2'>, <class 'object'>)
```

Una curiosidad es que al final del todo vemos la clase `object`. Aunque pueda parecer raro, es correcto ya que en realidad todas las clases en Python heredan de una clase genérica `object`, aunque no lo especifiquemos explícitamente.

## Polimorfismo

Al ser un lenguaje con tipado dinámico y permitir duck typing, en Python no es necesario que los objetos compartan un interfaz, simplemente basta con que tengan los métodos que se quieren llamar.

Supongamos que tenemos un clase `Animal` con un método `hablar()`.

```python
class Animal:
    def hablar(self):
        pass
```

Por otro lado tenemos otras dos clases, `Perro`, `Gato` que heredan de la anterior. Además, implementan el método `hablar()` de una forma distinta.

```python
class Perro(Animal):
    def hablar(self):
        print("Guau!")

class Gato(Animal):
    def hablar(self):
        print("Miau!")
```

A continuación creamos un objeto de cada clase y llamamos al método `hablar()`. Podemos observar que cada animal se comporta de manera distinta al usar `hablar()`.

```
for animal in Perro(), Gato():
    animal.hablar()

# Guau!
# Miau!
```

En el caso anterior, la variable `animal` ha ido “tomando las formas” de `Perro` y `Gato`. 

## Duck Typing en Python

El duck typing o tipado de pato es un concepto relacionado con la programación que aplica a ciertos lenguajes orientados a objetos, y que tiene origen en la siguiente frase:

> If it walks like a duck and it quacks like a duck, then it must be a duck

Lo que se podría traducir al español como. **Si camina como un pato y habla como un pato, entonces tiene que ser un pato**.

El concepto de duck typing se fundamenta en el razonamiento inductivo, donde una serie de premisas apoyan la conclusión, pero no la garantizan. Si vemos a un animal que parece un pato, habla como tal y anda como tal, sería razonable pensar que se trata de un pato, pero sin un test de ADN nunca estaríamos al cien por cien seguros.

Una vez entendido el origen del concepto, veamos lo que realmente significa esto en Python. En pocas palabras, a Python le dan igual los tipos de los objetos, lo único que le importan son los métodos.

Definamos una clase `Pato` con un método `hablar()`.

```python
class Pato:
    def hablar(self):
        print("¡Cua!, Cua!")
```

Y llamamos al método de la siguiente forma.

```python
p = Pato()
p.hablar()
# ¡Cua!, Cua!
```

Hasta aquí nada nuevo, pero vamos a definir una función `llama_hablar()`, que llama al método `hablar()` del objeto que se le pase.

```python
def llama_hablar(x):
    x.hablar()
```

Como puedes observar, en Python **no es necesario especificar los tipos**, simplemente decimos que el parámetro de entrada tiene el nombre `x`, pero no especificamos su tipo.

Cuando Python entra en la función y evalúa `x.hablar()`, le da igual el tipo al que pertenezca `x` siempre y cuando tenga el método `hablar()`. Esto es el *duck typing* en todo su esplendor.

```python
p = Pato()
llama_hablar(p)
# ¡Cua!, Cua!
```

¿Y qué pasa si usamos otros objetos que no son de la clase `Pato`? Pues bien, como hemos dicho, a la función `llama_hablar()` le da igual el tipo. Lo único que el importa es que el objeto tenga el método `hablar()`.

Definamos tres clases de animales distintas que implementan el método `hablar()`. Nótese que no existe [herencia](https://ellibrodepython.com/herencia-en-python) entre ellas, son clases totalmente independientes. De haberla estaríamos hablando de [polimorfismo](https://ellibrodepython.com/polimorfismo-en-programacion).

```python
class Perro:
    def hablar(self):
        print("¡Guau, Guau!")

class Gato:
    def hablar(self):
        print("¡Miau, Miau!")

class Vaca:
    def hablar(self):
        print("¡Muuu, Muuu!")
```

Y como es de esperar la función `llama_hablar()` funciona correctamente con todos los objetos.

```python
llama_hablar(Perro())
llama_hablar(Gato())
llama_hablar(Vaca())

# ¡Guau, Guau!
# ¡Miau, Miau!
# ¡Muuu, Muuu!
```