En Python, los **getters** y **setters** no son los mismos que en otros lenguajes de programación orientados a objetos. Básicamente, el propósito principal de usar **getters** y **setters** en los programas orientados a objetos es asegurar la encapsulación de datos. Las variables privadas en Python no son realmente campos ocultos como en otros lenguajes orientados a objetos. Los **getters** y **setters** en Python se utilizan a menudo cuando:

* Utilizamos **getters** & **setters** para añadir lógica de validación en torno a la obtención y establecimiento de un valor.
* Para **evitar el acceso directo** a un campo de la clase, es decir, las variables privadas no pueden ser accedidas directamente o modificadas por un usuario externo.

Veamos el siguiente código:

```python
class Geek:
    def __init__(self, age = 0):
         self._age = age
      
    # método getter 
    def get_age(self):
        return self._age
      
    # método setter 
    def set_age(self, x):
        self._age = x
  
raj = Geek()
  
# estableciendo la edad utilizando el método setter
raj.set_age(21)
  
# obteniendo la edad utilizando el método getter
print(raj.get_age())
  
print(raj._age)
#21
#21
```

En el código anterior las funciones `get_age()` y `set_age()` actúan como funciones normales y no tienen ningún impacto como **getters** y **setters**, para lograr tal funcionalidad Python tiene una función especial `property()`.

## Uso de la función property() para conseguir el comportamiento de getters y setters

En Python `property()` es una función incorporada que crea y devuelve un objeto propiedad. Un objeto propiedad tiene tres métodos, `getter()`, `setter()`, y `delete()`. La función `property()` en Python tiene cuatro argumentos `property(fget, fset, fdel, doc)`:

* `fget ` es una función para recuperar el valor de un atributo. 
* `fset` es una función para establecer el valor de un atributo. 
* `fdel ` es una función para borrar el valor de un atributo. 
* `doc` crea un docstring para el atributo. 

Veamos el siguiente código:

```python
class Geeks:
     def __init__(self):
          self._age = 0
       
     # función para obtener el valor de _age
     def get_age(self):
         print("método getter llamado")
         return self._age
       
     # función para establecer el valor de _age
     def set_age(self, a):
         print("método setter llamado")
         self._age = a
  
     # función para eliminar el atributo _age 
     def del_age(self):
         del self._age
     
     age = property(get_age, set_age, del_age) 
  
mark = Geeks() 
  
mark.age = 10 #linea 23
  
print(mark.age) #linea 25
#método setter llamado
#método getter llamado
#10
```

En el código anterior sólo hay una sentencia de impresión en la línea #25 pero la salida consiste en tres líneas debido al método setter `set_age()` llamado en la línea #23 y al método `get_age() `llamado en la línea #25. Por lo tanto, la edad es un objeto de propiedad que ayuda a mantener el acceso de la variable privada segura.

## Using `@property` decorators to achieve getters and setters behaviour

En el método anterior utilizamos la función `property() ` para conseguir el comportamiento de getters y setters. Sin embargo, como se mencionó anteriormente en este post getters y setters también se utilizan para la validación de la obtención y el establecimiento de valor de los atributos. Hay una forma más de implementar la función `property`, es decir, utilizando un decorador. Python `@property` es uno de los decoradores incorporados. El propósito principal de cualquier decorador es cambiar los métodos o atributos de tu clase de tal manera que el usuario de tu clase no tenga que hacer ningún cambio en su código. Por ejemplo

```python
class Geeks:
     def __init__(self):
          self._age = 0
       
     # utilizando el decorador de property
     # una función getter
     @property
     def age(self):
         print("método getter llamado")
         return self._age
       
     # una función setter
     @age.setter
     def age(self, a):
         if(a > 0):
            raise ValueError("Tu edad debe ser mayor a 0")
         print("método setter llamado")
         self._age = a
  
mark = Geeks()
  
mark.age = 19
  
print(mark.age)

#setter method called
#getter method called
#19
```

En el código anterior queda claro cómo utilizar el decorador` @property` para crear getters y setters. Las líneas 15-16 actúan como un código de validación que lanza un `ValueError `si intentamos inicializar la edad con un valor menor a 0, de esta forma se puede aplicar cualquier tipo de validación en las funciones getter o setter.

En resumen `@property` se utiliza para definir el método getter de la clase, y para definir el método setter es con la sintaxis `@nombreDeLaPropiedad.setter`. 

