# Descomposición

La **descomposición** consiste en partir un problema en partes más pequeñas. Por ejemplo, un automóvil puede ser dividido en subpartes: llantas, vidrios, asientos, volante, motor, etc. En la programación se puede hacer lo mismo, un programa puede ser **descompuesto** en partes más pequeñas.

Las clases permiten hacer lo anterior, dividir el programa en subpartes, para así crear mayores abstracciones y que todos los elementos aporten a la solución. Cada clase se va a encargar de una parte del problema haciendo el programa más fácil de entender y de mantener. 

Para este tema retomaremos el tema del automóvil como ejemplo solo para que te des una idea de lo que estamos hablando. 

```python
class Automovil:

    def __init__(self, modelo, marca, color):
        self.modelo = modelo
        self.marca = marca
        self.color = color
        self._estado = 'en_reposo'
        self._motor = Motor(cilindros=4)

    def acelerar(self, tipo='despacio'):
        if tipo == 'rapida':
            self._motor.inyecta_gasolina(10)
        else:
            self._motor.inyecta_gasolina(3)

        self._estado = 'en_movimiento'


class Motor:

    def __init__(self, cilindros, tipo='gasolina'):
        self.cilindros = cilindros
        self.tipo = tipo
        self._temperatura = 0

    def inyecta_gasolina(self, cantidad):
        pass
```

Recuerda que dentro de las clases las variables que empiecen por un guion bajo como `_estado` y `_motor` quiere decir que son variables privadas, por lo tanto, no serán compartidas con el usuario pues será irrelevante que las conozca. Nota como en el método `acelerar` la variable `tipo` ya fue declarada con el valor gasolina, a esto se le conoce como un parámetro por defecto o `default keyword` en donde se le adjudica un valor por defecto desde su creación.

La verdad es que este programa no sirve de mucho para un programador, pero es una mera referencia para que entiendas cómo se puede descomponer un programa.

## 

