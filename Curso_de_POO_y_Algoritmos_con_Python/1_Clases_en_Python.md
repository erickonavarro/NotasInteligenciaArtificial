# Tipos de datos abstractos

En Python todo es un objeto y todo tiene un tipo. Cuando decimos que es un **objeto** se refiere a que cada elemento tiene una representación de memoria, y el **tipo** significa que los datos y comportamiento del elemento pueden ser almacenados en un solo objeto.

Extrapolando lo anterior a la vida podemos dar los siguientes ejemplos de **tipo**:

*  Tipo humano
* Tipo cámara
* Tipo vehículo
* Tipo restaurante

Como te darás cuenta todo alrededor puede ser representado como un **tipo** y a través de la Programación Orientada a Objetos es posible modelar el mundo de esta manera. 

Existen tres formas en las que podemos interactuar con los **objetos**:

* **Creación**: Crear nuevos objetos tantas veces como queramos. 
* **Manipulación**: Ejecutar sus métodos
* **Destrucción**: En Python cuando nadie más en el programa utiliza el objeto, este lo elimina automáticamente.

Algunas ventajas de los **objetos**:

* **Descomposición**: Dividir el objeto en partes más pequeñas
* **Abstracción**: es la habilidad de ignorar los detalles de las partes para enfocar la atención en un nivel más alto de un problema
* **Encapsulación**: es cuando limitamos el acceso o damos un acceso restringido de una propiedad.

## Definiendo clases en Python

Para definir una clase en Python se usa la keyword `class` seguido del nombre de la clase:

```python
class Perro:
    pass
```

Se trata de una clase vacía y sin mucha utilidad práctica, pero es la mínima clase que podemos crear. Nótese el uso del `pass` que no hace realmente nada, pero daría un error si después de los `:` no tenemos contenido.

Ahora que tenemos la **clase**, podemos crear un **objeto** de la misma. Podemos hacerlo como si de una variable normal se tratase. Nombre de la variable igual a la clase con `()`. Dentro de los paréntesis irían los parámetros de entrada si los hubiera.

```python
mi_perro = Perro()
```

## Instancias

Imagina a la `clase` como un  molde con el cual podemos crear 'copias' , y a los objetos creados se les conoce como instancias, los cuales pueden tener atributos diferentes. Imagínate una fábrica de botellas de cristal donde tienen un molde para hacer las botellas. A partir de ese molde pueden crear botellas de la misma forma pero de diferente color. Es lo mismo con las clases y los objetos. 

Los atributos de clase nos permiten:

* Representar datos
* Procedimientos para interactuar con los mismos
* Mecanismos para esconder la representación interna

## Definiendo atributos

A continuación vamos a añadir algunos atributos a nuestra clase. Antes de nada es importante distinguir que existen dos tipos de atributos:

- Atributos de **instancia**: Pertenecen a la instancia de la clase o al objeto. Son atributos particulares de cada instancia, en nuestro caso de cada perro.
- Atributos de **clase**: Se trata de atributos que pertenecen a la clase, por lo tanto serán comunes para todos los objetos.

Empecemos creando un par de **atributos de instancia** para nuestro perro, el `nombre` y la `raza`. Para ello creamos un método `__init__` que será llamado automáticamente cuando creemos un objeto. Se trata del **constructor**.

```python
class Perro:
    # El método __init__ es llamado al crear el objeto
    def __init__(self, nombre, raza):
        print(f"Creando perro {nombre}, {raza}")

        # Atributos de instancia
        self.nombre = nombre
        self.raza = raza
```

Ahora que hemos definido el método *init* con dos parámetros de entrada, podemos crear el objeto pasando el valor de los atributos. Usando `type()` podemos ver como efectivamente el objeto es de la clase `Perro`.

```python
mi_perro = Perro("Toby", "Bulldog")
print(type(mi_perro))
# Creando perro Toby, Bulldog
# <class '__main__.Perro'>
```

Seguramente te hayas fijado en el `self` que se pasa como parámetro de entrada del método. Es una variable que representa la instancia de la clase, y deberá estar siempre ahí.

El uso de `__init__` y el doble `__` no es una coincidencia. Cuando veas un método con esa forma, significa que está reservado para un uso especial del lenguaje. En este caso sería lo que se conoce como **constructor**. 

Por último, podemos acceder a los atributos usando el objeto y `.`. Por lo tanto.

```python
print(mi_perro.nombre) # Toby
print(mi_perro.raza)   # Bulldog
```

Hasta ahora hemos definido atributos de instancia, ya que son atributos que pertenecen a cada perro concreto. Ahora vamos a definir un **atributo de clase**, que será común para todos los perros. Por ejemplo, la especie de los perros es algo común para todos los objetos Perro.

```python
class Perro:
    # Atributo de clase
    especie = 'mamífero'

    # El método __init__ es llamado al crear el objeto
    def __init__(self, nombre, raza):
        print(f"Creando perro {nombre}, {raza}")

        # Atributos de instancia
        self.nombre = nombre
        self.raza = raza
```

Dado que es un atributo de clase, no es necesario crear un objeto para acceder al atributos. Podemos hacer lo siguiente.

```python
print(Perro.especie)
# mamífero
```

Se puede acceder también al atributo de clase desde el objeto.

```python
mi_perro = Perro("Toby", "Bulldog")
mi_perro.especie
# 'mamífero'
```

De esta manera, todos los objetos que se creen de la clase perro compartirán ese atributo de clase, ya que pertenecen a la misma.

## Definiendo métodos

En realidad cuando usamos `__init__` anteriormente ya estábamos definiendo un método, solo que uno especial. A continuación vamos a ver como definir métodos que le den alguna funcionalidad interesante a nuestra clase, siguiendo con el ejemplo de perro.

Es importante no confundir las `funciones` con los `métodos`. Si bien ambas se definen con `def` cada uno tiene un propósito distinto y se declaran en lugares diferentes. Los métodos se definen dentro de las clases únicamente y es parte de la funcionalidad que le damos a un objeto, por lo tanto, siempre va a estar asociado a un objeto.  Por otro lado, las funciones están definidas por sí mismas  no pertenecen a ninguna clase. 

Vamos a codificar dos métodos, ladrar y caminar. El primero no recibirá ningún parámetro y el segundo recibirá el número de pasos que queremos andar. Como hemos indicado anteriormente `self` hace referencia a la instancia de la clase. Se puede definir un método con `def` y el nombre, y entre `()` los parámetros de entrada que recibe, donde siempre tendrá que estar `self` el primero.

```python
class Perro:
    # Atributo de clase
    especie = 'mamífero'

    # El método __init__ es llamado al crear el objeto
    def __init__(self, nombre, raza):
        print(f"Creando perro {nombre}, {raza}")

        # Atributos de instancia
        self.nombre = nombre
        self.raza = raza

    def ladra(self):
        print("Guau")

    def camina(self, pasos):
        print(f"Caminando {pasos} pasos")
```

Por lo tanto si creamos un objeto `mi_perro`, podremos hacer uso de sus métodos llamándolos con `.` y el nombre del método. Como si de una función se tratase, pueden recibir y devolver argumentos.

```python
mi_perro = Perro("Toby", "Bulldog")
mi_perro.ladra()
mi_perro.camina(10)

# Creando perro Toby, Bulldog
# Guau
# Caminando 10 pasos
```

## 

