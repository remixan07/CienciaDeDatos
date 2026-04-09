# Ejericicos Complementarios Semana 3

## Ejercicio 1: Variables y Tipos de Datos

```
entero = 25
decimal = 3.1415926585
booleano = False
string = "Pitáfola de Yaroslav"
diccionario = {"clase": "Historia del Alfabrto Latino en Nauru", "letra": "ʝ"}
lista = [2, 4, 6, 8]

print("entero:", entero)
print("decimal:", decimal)
print("booleano:", booleano)
print("string:", string)
print("diccionario:", diccionario)
print("lista:", lista)
```
```
texto = "25"
entero = int(texto)

decimal = 8.9
decimal_a_entero = int(decimal)

numero = 7
entero_a_decimal = float(numero)

print(entero)
print(decimal_a_entero)
print(entero_a_decimal)
```
```
edad = 452
print(f"El usuario del vehículo con placas N0-S0Y-V4MP1R0 tiene {edad} años")
```

## Ejercicio 2: Control de Flujo

```
numero = float(input("Inserte un número: "))
if numero <= -1:
    print("El número", numero, "es negativo")
if numero == 0:
    print("El número", numero, "es cero")
if numero >= 1:
    print("El número", numero, "es positivo")
```
```
while True:
    print("\nMenú:")
    print("1. Sumar")
    print("2. Restar")
    print("3. Salir")
    opcion = input("Inserte una opción ")
    if opcion=="1":
        num1= float(input("Inserte un número "))
        num2=float(input("Inserte un número "))
        print("La suma es ", num1 + num2)
    elif opcion == "2":
        num1= float(input("Inserte un número"))
        num1= float(input("Inserte un número "))
        print("Resta:", num1 - num2)
    elif opcion =="3":
        print("El programa ha terminado")
        break
    else:
        print("La opción es inválida")
```
```
while True:
    menu()
    opcion= input("Opción:")
    if opcion=="1":
        op_factorial()
    elif opcion=="2":
        op_digitos()
    elif opcion=="3":
        print("Fin del programa")
        break
```

## Ejercicio 3: Funciones

```
radio = float(input("Inserte el radio de tu circulo: "))
pi = 3.1415926585
radio_cuadrado = radio * radio
area = pi * radio_cuadrado
print("El área es", area, "u²")
```
```
n1 = float(input("Inserte los grados celcius a convertir: "))
n2 = n1/5
n3 = n2*9
r = n3+32
print(n1, "°C equivale a", r, "°F")
```
```
suma = 0
contador = 0
maxcalif = 10
while contador <maxcalif:
    entrada=input("Inserte la calificación: ").strip()
    if entrada.lower() == "fin":
        break
    calificacion = float(entrada)
    if 0 <= calificacion <=10:
        suma += calificacion
        contador += 1
    else:
        print("Fuera de rango")
if contador>0:
    p=suma/contador
    print("Promedio:", p)
```
```
def max_min(lista):
    return max(lista), min(lista)

print(max_min([4, 7, 2, 9, 1]))
```

## Ejercicio 4: Operaciones con Arrrays

```
import numpy as np

arr1 = np.array([1, 2, 3, 4, 5])
arr2 = np.array([5, 4, 3, 2, 1])

print(arr1 + arr2)

print(arr1 * 5)

print(np.mean(arr1))
print(np.median(arr1))
print(np.std(arr1))

print(np.unique(arr1))

print(arr1.reshape(1, 5))
```

## Ejercicio 5: Álgebra con NumPy

```
v1 = np.array([1, 2, 3])
v2 = np.array([4, 5, 6])

print(np.dot(v1, v2))

print(np.cross(v1, v2))

print(np.linalg.norm(v1))
print(np.linalg.norm(v2))

print(v1 / np.linalg.norm(v1))
print(v2 / np.linalg.norm(v2))
```

## Ejercicio 6: DataFrames Báscio

```
import pandas as pd

data = {
    'nombre': ['Ana', 'Luis', 'María', 'Carlos', 'Sofia'],
    'edad': [20, 22, 19, 21, 23],
    'carrera': ['Ing', 'Ing', 'Lic', 'Ing', 'Lic'],
    'promedio': [8.5, 9.0, 7.8, 8.2, 9.5]
}

df = pd.DataFrame(data)

print(df['nombre'])

print(df[df['promedio'] > 8.5])

print(df.sort_values(by='edad'))

df['aprobado'] = df['promedio'] >= 7
print(df)

print(df.groupby('carrera')['promedio'].mean())
```

## Ejercicio 7: Manipulación de Datos

```
df.loc[0, 'promedio'] = np.nan
df['promedio'] = df['promedio'].fillna(df['promedio'].mean())

df = df.drop_duplicates()

df['edad_doble'] = df['edad'].apply(lambda x: x * 2)

print(df.loc[0])
print(df.iloc[0:3])

df2 = df.copy()
nuevo_df = pd.concat([df, df2])
print(nuevo_df)
```

## Ejercicio 8: Matplotlib

```
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure()
plt.plot(x, y, label="sin(x)")
plt.title("Gráfico de Línea")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()
plt.show()

plt.figure()
plt.scatter(x, y, label="puntos")
plt.title("Gráfico de Dispersión")
plt.xlabel("X")
plt.ylabel("Y")
plt.legend()
plt.show()

data = np.random.randn(1000)
plt.figure()
plt.hist(data, bins=30, label="datos")
plt.title("Histograma")
plt.legend()
plt.show()

categorias = ['A', 'B', 'C']
valores = [10, 20, 15]
plt.figure()
plt.bar(categorias, valores, label="valores")
plt.title("Gráfico de Barras")
plt.legend()
plt.show()
```

## Ejercicio 9: Análisis Exploratorio

```
```

## Ejercicio 10: Medidas de Tendencia Central

| Datos | Media | Mediana | Moda |
| :---: | :---: | :---: | :---: |
| [5,3,8,3,7] | 5.2 | 5 | 3 |
| [10,20,30,40] | 25 | 25 | --- |
| [1,2,2,3,3,3,4] | 2.57 | 3 | 3 |

## Ejercicio 11: Dispersión

| Datos | Rango | Varianza | Desviación Estándar |
| :---: | :---: | :---: | :---: |
| [2,4,4,4,5,5,7,9] | 7 | 4 | 2 |
| [1,3,5,7,9] | 8 | 8 | 2.8 |

## Ejercicio 12: El Proceso de Data Science

El ciclo crisp-dm es una metodología que se tuiliza para estructurar proyectos y minería de datos que guía al proceso mediante comprensión y preparación del negocio y de los datos; además del modelado, evaluación, e implementación

Los pasos del proceso de ciencia de datos son:
Comprensión del Problema - Definir el Objetivo
Adquisición de Datos - Recopilar
Preparación - Correcciones
Explloración - Analizar
Caracterpisticas - Dar Formato
Modelado - Aplicar algoítmos
Evaluación - Verificar su cumple
Interpretación - Poner los resultados

MVP en Ciencia de Datos se refiere a la simplificación de un modelo analítico que cuenta únicamente con las funcionalidades esenciales para resolver un problema y validar una hipótesus en base a datos reales

## Ejercicio 13: Caso de Estudio

En este caso, Netflix todo el tiempo queiere conocer que contenido ven sus usuarios, esto, para pdoer seguir recomendadno series y películas pra que sus usuarios sigan pagando una siscripción más cara que pagar cable para que luego no tengan todo el contendio o lo quiten, y luego aumenten el precio e incluyan comerciales y ahora tengas que pgar más para verlo sin comerciales y ahora ya no conviene el streaming, está más caro ya que ooagar cable asashahsahshasa (BOPRRAR)

Se buscaba responder: ¿qué contenido revisan más los usuarios?, ¿como ven los usuarios el contenido?. ¿que recomendar a los usuarios en base al contenido?

Se usó análisis de comportamiento, clustering, machine learning y visualización de datos; y lo que descubrí fueron patrones de gustos, horarios de consumo, y preferencias por género, ayudando a mejorar recomendaciones personalizadas
