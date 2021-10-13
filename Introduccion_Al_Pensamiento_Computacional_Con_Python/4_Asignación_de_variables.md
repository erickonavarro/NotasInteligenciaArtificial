# Asignación de variables

Una **variable** es un nombre que se refiere a un objeto que reside en la memoria. El objeto puede ser de alguno de los tipos vistos (número o cadena de texto), o alguno de los otros tipos existentes en Python.

La forma en que se vinculan las variables es utilizando el operador de **asignación** el cual se representa con el signo de igual **''=''**. Por ejemplo:

```python
a = 2
x = 4
z = (a * x) / 2
```

La primera línea quiere decir que el valor de 2 se lo estamos asignando a la variable con nombre **a**, después el valor de 4 se asigna a la variable **x** y finalmente, el resultado de la operación (a * x) / 2 se asigna a la variable **z**.

Sin embargo, de esta manera el único que podría entender el programa sería el que lo escribió, porque esos nombres de variables podrían representar lo que sea. Es por ello que es una **buena práctica** nombrar las variables de acuerdo al contexto, para que así cualquiera otro que lea el código pueda entender, y también para evitar que al programador se le olvide qué representaba dicha variable. Entonces rescribiendo lo anterior queda:

```python
base = 2
altura = 4
area = (base * altura) / 2
```

Ahora el código tiene sentido, cualquiera sabría que se está calculando el área de un triángulo. Nombrar las variables de acuerdo al contexto te ayudará a leer el programa más rápido y a evitar confusiones.

## Reasignando variables

Al asignar un valor a una variable, lo que sucede a nivel de memoria es que a un sector de la memoria se le asigna el nombre de dicha variable. Por ejemplo:

```python
>>>my_var = 'Hello, world'
>>>print(my_var)
Hello, world

>>> my_var = 3
>>> print(my_var)
3
```

Tenemos la variable *my_var* a la que primero se le asigno el string *Hello, world* y después se le reasignó el valor de 3. A nivel de memoria sucede lo siguiente:

| Nombre | Memoria | Valor          |
| ------ | ------- | -------------- |
| ...    | ...     | ...            |
| my_var | 0x0001  | 'Hello, world' |
|        | 0x0002  | 3              |
| ...    | ...     | ...            |

La primera vez que asignamos la variable *my_var* se vincula al espacio de memoria 0x0001, y cuando se reasigna se pasa al lugar 0x0002

| Nombre | Memoria | Valor          |
| ------ | ------- | -------------- |
| ...    | ...     | ...            |
|        | 0x0001  | 'Hello, world' |
| my_var | 0x0002  | 3              |
| ...    | ...     | ...            |

## Variables en Python

Los nombres de las varaibles en python pueden contener mayúsculas, minúsculas, números (pero no puede comenzar con un número) y, guion bajo. Por otro lado, no pueden llamarse como las palabras reservadas las cuales son:

```
False	class	is	return
None	continue	lambda	try
True	def	nonlocal	while
and	del	not	with
as	elif	or	yield
assert	else	pass	*
break	except	raise	*
```

