# Actividades Sema 3

## Actividad 3.1 Refuerzo de Python

```
# no olvidar, es importante importar:
import pandas as pd

try:
    # UnA lIsTa BiEn ToNta:
    numeros = [1, 2, 3, 4, 5]
    print("Lista de Números: ", numeros)

    # Compréndeme:
    lista_comprehensions = [n ** 2 for n in numeros]
    print("Lista de Comprehensions: ", lista_comprehensions)

    # Diccionariorio:
    personas = {
        "A-Yu-Da": 67,
        "Fortunio": 120,
        "Mitridates": 99
    }
    print("Diccionario de personas:", personas)

    # Lambda:
    funcion_lambda = lambda x: x * 2
    numeros_duplicados = [funcion_lambda(n) for n in numeros]
    print("Números duplicados con Lambda: ", numeros_duplicados)

    data_frame = pd.DataFrame({
        "Nombre": list(personas.keys()),
        "Edad": list(personas.values())
    })

    print("DataFrame creado:")
    print(data_frame)

    # I AM ERROR:
    resultado = 10 / 0

except ZeroDivisionError:
    print("E R R O R   . . .   E R R O R   . . .   E R R O R   . . .   E R R O R")
```
```
# Un print básico:
print("Hwllo World")

# Una operación básica:
print(9 * 45)

# Un looooooooop:
for i in range(1, 6):
    print(i)

# MAYOR & menor:
if 24 < 100:
    print("El número 24 es menor que el número 100")

# define:
def saludar(nombre):
    return f"Hola {nombre}"

print(saludar("Ricardo"))
```

## Actividad 3.2 Carga y Exploración de Datos

```

except ZeroDivisionError:
    print("S E   H A   D E T E C T A D O   U N   E R R O R")
