# Actividad 4:

## 1.-

```
import pandas as pd

import pandas as pd

url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/CarData.zip"
df_vehiculos = pd.read_zip(url)

print(df_vehiculos.head())

print("Columnas: ")
print(df_vehiculos.columns)

print("Información: ")
print(df_vehiculos.info())

import seaborn as sns
import matplotlib.pyplot as plt

print("Generando análisis: ")
sns.pairplot(df_vehiculos[['selling_price', 'km_driven', 'year']])
plt.show()

X_modelo = df_vehiculos[['km_driven', 'year']]
y_modelo = df_vehiculos['selling_price']

print("X (independientes): km_driven, year")
print("y (dependiente): selling_price")

from sklearn.model_selection import train_test_split

X_entrena, X_prueba, y_entrena, y_prueba = train_test_split(
    X_modelo, y_modelo, test_size=0.2, random_state=42
)

print("Entrenamiento:", X_entrena.shape)
print("Prueba:", X_prueba.shape)

from sklearn.linear_model import LinearRegression

modelo_rlm = LinearRegression()
modelo_rlm.fit(X_entrena, y_entrena)

print("Modelo entrenado")
print("Coeficientes:", modelo_rlm.coef_)
print("Intercepto:", modelo_rlm.intercept_)

from sklearn.metrics import r2_score

predicciones_prueba = modelo_rlm.predict(X_prueba)

r2_modelo = r2_score(y_prueba, predicciones_prueba)

print("R² del Modelo:", r2_modelo)

datos_nuevos = pd.DataFrame({
    'km_driven': [30000, 90000],
    'year': [2019, 2010]
})

pred_nuevas = modelo_rlm.predict(datos_nuevos)

print("Predicciones Nuevos Vegículos: ")
print(pred_nuevas)

from sklearn.metrics import mean_squared_error

mse_modelo = mean_squared_error(y_prueba, predicciones_prueba)

print("Error Cuadrático Medio: ", mse_modelo)
```

Conclusioness:
El modelo logra predecir el precio de los vehículos usando el kilometraje y  el año
El año incrementa el precio, mientras que el kilometraje lo reduce
El modelo muestra una relación lineal clara entre las variables independientes y el precio, lo que indica que la regresión lineal es una aproximación adecuada para este problema
El kilometraje tiene un impacto negativo en el precio, lo cual es coherente con el comportamiento real del mercado de vehículos usados
Aunque el modelo es útil, se puede mejorar agregando variables como tipo de combustible o transmisión
El modelo puede presentar limitaciones al no considerar factores como marca, tipo de combustible, o transmisión, lo que podría mejorar la precisión si se incluyen

## 2.-

```
import pandas as pd

url = "https://www.openml.org/data/get_csv/16826755/phpMYEkMl"
df_titanic = pd.read_csv(url)

print("Filas: ")
print(df_titanic.head())

print("Columnas :")
print(df_titanic.columns)

print("Nulos: ")
print(df_titanic.isnull().sum())

columnas_a_eliminar = ['name', 'ticket', 'cabin', 'boat', 'body', 'home.dest']
df_titanic = df_titanic.drop(columns=[col for col in columnas_a_eliminar if col in df_titanic.columns])
df_titanic = df_titanic.dropna()

print("Limpieo Dataset: ")
print(df_titanic.info())

df_titanic['sex'] = df_titanic['sex'].astype('category')
df_titanic['embarked'] = df_titanic['embarked'].astype('category')

df_titanic = pd.get_dummies(df_titanic, drop_first=True)

print("Tras Transformación: ")
print(df_titanic.columns)

import seaborn as sns
import matplotlib.pyplot as plt

print("Relación Variables: ")
sns.pairplot(df_titanic[['survived','age','fare','pclass']])
plt.show()

from scipy.stats import ttest_ind

sobrevivieron = df_titanic[df_titanic['survived'] == 1]['age']
no_sobrevivieron = df_titanic[df_titanic['survived'] == 0]['age']

t_stat, p_value = ttest_ind(sobrevivieron, no_sobrevivieron)

print("t-statistic:", t_stat)
print("p-value:", p_value)

from sklearn.model_selection import train_test_split

X = df_titanic.drop('survived', axis=1)
y = df_titanic['survived']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

print("Entrenamiento:", X_train.shape)
print("Prueba:", X_test.shape)

from sklearn.linear_model import LogisticRegression

modelo_logistico = LogisticRegression(max_iter=1000)
modelo_logistico.fit(X_train, y_train)

print("El modelo ha sido entrenado correctamente")

import numpy as np

coeficientes = pd.DataFrame({
    'Variable': X.columns,
    'Coeficiente': modelo_logistico.coef_[0],
    'Odds Ratio': np.exp(modelo_logistico.coef_[0])
})

print("Coeficientes: [archive (3).zip](https://github.com/user-attachments/files/27108194/archive.3.zip)
")
print(coeficientes.sort_values(by='Odds Ratio', ascending=False))

Conclusiones:
La clase del pasajero tiene un impacto importante, donde los pasajeros de clases más altas presentan mayor probabilidad de sobrevivir
El modelo identifica que las variables como el sexo, la clase y la tarifa influyen significativamente en la supervivencia
Las mujeres y pasajeros de primera clase tienen mayor probabilidad de sobrevivir
El modelo confirma que el género es una de las variables más influyentes en la supervivencia, favoreciendo significativamente a las mujeres
El modelo es útil, pero puede mejorarse con selección de variables y ajuste de hiperparámetros
La edad muestra cierta influencia en la supervivencia, aunque no es tan determinante como otras variables como el sexo o la clase
El modelo logístico es adecuado para este tipo de problema binario, aunque su rendimiento puede mejorar con técnicas de optimización y selección de variables
```
