# Decoradores

Antes de entrar de lleno con el tema de decoradores es importante mencionar que en Python las funciones son ciudadanos de primera clase, eso quiere decir que una función puede ser asignada a una variable, puede ser utilizada como argumento para otra función, o inclusive puede ser retornada. Veamos un ejemplo.

```python
def saludar(): 
    print('Hola soy una función') 

def super_funcion(funcion): 
    funcion() 

funcion = saludar  # Asignamos la función a una variable!

super_funcion(funcion)
#Hola soy una función
```

Un decorador no es más que una función la cual toma como input una función y a su vez retorna otra función. 

Veamos un ejemplo donde definimos 3 diferentes funciones que utilizaremos de manera conjunta:

```python
def presentarse(nombre):
	return f"Me llamo {nombre}"

def estudiemos_juntos(nombre):
	return f"¡Hey {nombre}, aprendamos Python!"

def consume_funciones(funcion_entrante):
	return funcion_entrante("David")
```

Las primeras dos funciones son obvias en su resultado, donde nos mostrarán un mensaje con el valor de la variable `nombre`. La tercera función puede ser más compleja de predecir, ya que toma otra función como entrada. Veamos que pasa cuando colocamos una función como atributo:

```python
>>> consume_funciones(presentarse)
'Me llamo David'

>>> consume_funciones(estudiemos_juntos)
'¡Hey David, aprendamos Python!'
```

Pongamos atención en cómo la función `consume_funciones()` se escribe con paréntesis para ser ejecutada, mientras que la función `presentarse` y `estudiemos_juntos` solo hace referencia a estas.

## Funciones anidadas

Al igual que los condicionales y bucles también puedes colocar funciones dentro de otra función.

```python
def funcion_mayor():
	print("Esta es una función mayor y su mensaje de salida.")

	def librerias():
		print("Algunas librerías de Python son: Scikit-learn, NumPy y TensorFlow.")

	def frameworks():
		print("Algunos frameworks de Python son: Django, Dash y Flask.")

	frameworks()
	librerias()
```

Si llamamos a la función `funcion_mayor` tendremos la siguiente salida:

```python
>>> funcion_mayor()
Esta es una función mayor y su mensaje de salida.
Algunos frameworks de Python son: Django, Dash y Flask.
Algunas librerías de Python son: Scikit-learn, NumPy y TensorFlow.
```

Debemos considerar que las funciones anidadas dentro de funcion_mayor no se ejecutan hasta que se llama a esta primera, siendo muestra del scope o alcance de las funciones. Si las llamamos obtendremos un error