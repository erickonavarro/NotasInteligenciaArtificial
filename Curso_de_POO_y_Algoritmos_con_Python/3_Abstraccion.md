# Abstracción

La abstracción consiste en aislar un elemento de su contexto o del resto de los elementos que lo acompañan. En programación, el término se refiere al énfasis en el "¿qué hace?" más que en el "¿cómo lo hace?" (característica de caja negra). Dicho en otras palabras, la abstracción consiste en ocultar toda la complejidad que algo puede tener por dentro, ofreciéndonos unas funciones de alto nivel, por lo general sencillas de usar, que pueden ser usadas para interactuar con la aplicación sin tener conocimiento de lo que hay dentro.

Esto nos ayuda a enfocarnos únicamente en la información relevante para resolver el problema. Es útil para separar la información central de los detalles secundarios. Para lograrlo, podemos utilizar variables y métodos. 

Tomemos un ejemplo del mundo real, algo sencillo como una lavadora. Cuanto tú quieres usar la lavadora, no te interesa cómo funciona internamente, lo único que quieres es que tu ropa salga limpia. Para ello solo colocas la ropa dentro de la lavadora, llenas la caja del jabón, presionas unos botones y la máquina empezará a hacer su trabajo y a ti solo te queda esperar a que termine. Entonces, veamos el siguiente código:

```python
class Lavadora:

    def __init__(self):
        pass

    def lavar(self, temperatura='caliente'):
        self._llenar_tanque_de_agua(temperatura)
        self._anadir_jabon()
        self._lavar()
        self._centrifugar()

    def _llenar_tanque_de_agua(self, temperatura):
        print(f'Llenando el tanque con agua {temperatura}')

    def _anadir_jabon(self):
        print('Anadiendo jabon')

    def _lavar(self):
        print('Lavando la ropa')

    def _centrifugar(self):
        print('Centrifugando la ropa')


if __name__ == '__main__':
    lavadora = Lavadora()
    lavadora.lavar()
    
#Llenando el tanque con agua caliente
#Anadiendo jabon      
#Lavando la ropa      
#Centrifugando la ropa
```

En este programa tenemos una clase `Lavadora ` con un método público que es `lavadora()` y los demás privados que son `_llenar_tanque_de_agua(), _anadir_jabon, _lavar()`  y ` _centrifugar() `. Entonces el usuario sólo tiene que llamar a la función `lavar()` para que todo lo demás se haga de manera automática. 

