# Scope o Alcance

El **alcance** o **scope** en Python es el contexto al que pertenece una variable en el programa.  Esto quiere decir que la variable sólo será válida dentro de la región en la cual se declare. Si se intenta llamar a esa variable en una región diferente, Python no la reconocerá. 

## Hay cuatro ámbitos en Python:

* **Local** - Dentro de la función actual
* **Envolvente** - Funciones de envolvente interior
* **Global** - En el nivel superior del módulo
* **Integrado** - el módulo incorporado especial

## Alcance Local

Este es el bloque de código o el cuerpo de cualquier función de Python

```python
1 x = 50 # This is a globally bounded variable
2
3 def local_scope_example():
4 	x = 100 # This is a locally bounded variable
5 	print(x)
6 
7 local_scope_example() # 100
8 print(x) # 50
```

Estas son las preguntas que probablemente debería hacerse ahora mismo:

* ¿Cómo está `local_scope_example()` regresando 100?
* ¿Cómo está `print(x) ` regresando 50?

Analicemos cada línea paso a paso:

* line 1: Declaramos una variable `x` en el global scope
* line 3 : creamos una función llamada `local_scope_example()`
* line 7 : llamamos a `local_scope_example()`
* Siempre que llamamos a una función, creamos una nueva `execution context ` o nueva `scope block`, esto quiere decir que se ejecuta un nuevo contexto encima del actual; entonces ahora volvemos a line 4
* line 4: estamos en un contexto de ejecución completamente nuevo y creamos un número entero y lo asignamos `x` a la referencia de ese número entero, actualmente no tenemos idea de que también hay un número global `x`. 
* line 5: Llamamos a la función `print(x)`, Python buscará dentro de su contexto de ejecución actual para encontrar la variable que está vinculada dentro de `local_scope_example()`, encuentra `x` para que imprima 100. Es muy importante recordar que si no hubiera una variable nombrada `x ` enlazada dentro de `local_scope_example()`
* Line 8: Saltamos de nuevo a `Global Scope` y volvemos a llamar a `print(x)` Nuevamente, Python buscará primero en su propio contexto de ejecución y luego saltará afuera si es necesario. Python encuentra el `x` que está ubicado `line 1` e imprime 100. 

## Alcance adjunto

Este es un ámbito especial que solo existe para funciones anidadas. El alcance adjunto es el alcance de la función externa o adjunta.

```python
def outer_func():
    # This block is the Local scope of outer_func()
    x = 100
    # It's also the enclosing scope of inner_func()

    def inner_func():
        # This block is the Local scope of inner_func()
        x = 50
        print(x) # 50

    inner_func()
    print(x) # 100


outer_func()
```

## Alcance global

Este es el alcance más alto. Los nombres en este ámbito son visibles desde cualquier lugar de su código.

```python
x = 100 # global scope

def func():
    # Doesn't find x within its local execution context, so it jumps to the global scope and finds it there
    print(x)
 
func() # 100
```

## Alcance incorporado

Este alcance contiene nombres como palabras clave, funciones, excepciones y otros atributos que están integrados en Python.

```python
dir()
# Notice how __builtins__ is always present in the global scope
# ['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__']

dir(__builtins__)
# A list of functions available to us in this scope, auto imported by python so we can access from wherever.
# ['ArithmeticError', 'AssertionError', 'AttributeError', ...]
```

