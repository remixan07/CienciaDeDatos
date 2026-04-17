# Actividades Semana 4

## Actividad 4.1 Identificación de Valores Faltantes

```
import pandas as pd
import numpy as np

datos_autos = {
    'modelo': ['Sedan', 'SUV', None, 'Pickup'],
    'velocidad_max': [180, np.nan, 200, 170],
    'tipo_combustible': ['gasolina', None, 'diesel', 'gasolina']
}

df_autos = pd.DataFrame(datos_autos)

print("Información Inicial: ")
print(df_autos)

print("Valores Nulos: ")
print(df_autos.isnull())

print("Valores Faltantes: ")
print(df_autos.isnull().sum())

print("Resumen: ")
df_autos.info()

print("Datos Incompletos: ")
print(df_autos[df_autos.isnull().any(axis=1)])
```

## Actividad 4.2 Imputeación de Datos

Dado el anterior datafram

```
df_imp = df_autos.copy()

print("Dataset Antes: ")
print(df_imp)

df_media = df_imp.copy()
df_media['velocidad_max'] = df_media['velocidad_max'].fillna(df_media['velocidad_max'].mean())
print("Imputación: ")
print(df_media)

df_mediana = df_imp.copy()
df_mediana['velocidad_max'] = df_mediana['velocidad_max'].fillna(df_mediana['velocidad_max'].median())
print("\n=== Imputación con mediana ===")
print(df_mediana)

df_moda = df_imp.copy()
df_moda = df_moda.fillna(df_moda.mode().iloc[0])
print(Valor Frecuente: ")
print(df_moda)

df_ffill = df_imp.fillna(method='ffill')
print("Imputación Adelante: ")
print(df_ffill)

df_bfill = df_imp.fillna(method='bfill')
print("Imputación Atrás: ")
print(df_bfill)
```

## Actividad 4.3 Transformación de Datos

```
from sklearn.preprocessing import MinMaxScaler, StandardScaler

df_transform = pd.DataFrame({
    'peso': [1200, 1500, 1000, 1800],
    'potencia': [90, 120, 70, 150],
    'categoria': ['compacto', 'SUV', 'compacto', 'pickup']
})

print("Origianales: ")
print(df_transform)

scaler_minmax = MinMaxScaler()
df_norm = df_transform.copy()
df_norm[['peso', 'potencia']] = scaler_minmax.fit_transform(df_transform[['peso', 'potencia']])

print("Normalizados: ")
print(df_norm)

scaler_std = StandardScaler()
df_std = df_transform.copy()
df_std[['peso', 'potencia']] = scaler_std.fit_transform(df_transform[['peso', 'potencia']])

print("Estandarizados: ")
print(df_std)

df_encoded = pd.get_dummies(df_transform, columns=['categoria'])

print("Codificación Categorica: ")
print(df_encoded)

df_transform['relacion_peso_potencia'] = df_transform['peso'] / df_transform['potencia']

print("Variable Derivada: ")
print(df_transform)
```

## Actividad 4.4 Pipleine de Procesamiento

```
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.impute import SimpleImputer

df_animales = pd.DataFrame({
    'edad': [2, 5, None, 3],
    'peso': [10, None, 5, 8],
    'especie': ['perro', 'gato', 'perro', None]
})

print("Originla: ")
print(df_animales)

num_cols = ['edad', 'peso']
cat_cols = ['especie']

pipeline_num = Pipeline([
    ('rellenar', SimpleImputer(strategy='mean')),
    ('escalar', StandardScaler())
])

pipeline_cat = Pipeline([
    ('rellenar', SimpleImputer(strategy='most_frequent')),
    ('codificar', OneHotEncoder())
])

procesador = ColumnTransformer([
    ('numerico', pipeline_num, num_cols),
    ('categorico', pipeline_cat, cat_cols)
])

pipeline_total = Pipeline([
    ('procesamiento', procesador)
])

resultado = pipeline_total.fit_transform(df_animales)

print("Pipeline: ")
print(resultado)
```
