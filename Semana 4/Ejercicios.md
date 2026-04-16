# EJERCICIOS SEMANA 4

## Ejercicio 1 Normalización Min-Max

```
import numpy as np

datos = np.array([10, 20, 30, 40, 50])
xmin = datos.min()
xmax = datos.max()

resultado = (datos - xmin) / (xmax - xmin)
print(resultado)

print(resultado.min(), resultado.max())
```

## Ejercicio 2 Estandarización z-socre

Media = μ = 5
Desviación Estándar = σ = 2

```
import numpy as np

datos = np.array([2,4,4,4,5,5,7,9])

mu = np.mean(datos)
sigma = np.std(datos)

z = (datos - mu) / sigma
print(z)

print(np.mean(z))
print(np.std(z))
```

## Ejercicio 3 Comparación de Técnicas

```
from sklearn.preprocessing import MinMaxScaler, StandardScaler
import numpy as np

datos = np.array([100, 200, 300, 400, 500]).reshape(-1,1)

minmax = MinMaxScaler().fit_transform(datos)
standard = StandardScaler().fit_transform(datos)

print("MinMax:\n", minmax)
print("Standard:\n", standard)
```

## Ejercicio 4 Identificación de Valores Faltantes

```
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'A': [1, 2, np.nan, 4, 5],
    'B': [np.nan, 2, 3, 4, np.nan],
    'C': [1, 2, 3, 4, 5]
})

print(df.isnull())

print(df.isnull().sum())

print(df.isnull().mean()*100)

print(df[df.isnull().any(axis=1)])
```

## Ejercicio 5 Estrategias de Imputación

```
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'A': [1, 2, np.nan, 4, 5],
    'B': [np.nan, 2, 3, 4, np.nan],
    'C': [1, 2, 3, 4, 5]
})

display(df)

display(df.dropna())

display(df.dropna(axis=1))

display(df.fillna(df.mean()))

display(df.fillna(df.median()))

display(df.ffill())

display(df.bfill())
```

## Ejercicio 6 Imputación Avanzada

```
import pandas as pd
import numpy as np
from sklearn.impute import SimpleImputer

df = pd.DataFrame({
    'A': [1, 2, np.nan, 4, 5],
    'B': [np.nan, 2, 3, 4, np.nan],
    'C': [1, 2, 3, 4, 5]
})

display(df)

imputer_mean = SimpleImputer(strategy='mean')
df_mean = pd.DataFrame(imputer_mean.fit_transform(df), columns=df.columns)

display(df_mean)

imputer_median = SimpleImputer(strategy='median')
df_median = pd.DataFrame(imputer_median.fit_transform(df), columns=df.columns)

display(df_median)

imputer_freq = SimpleImputer(strategy='most_frequent')
df_freq = pd.DataFrame(imputer_freq.fit_transform(df), columns=df.columns)

display(df_freq)

imputer_const = SimpleImputer(strategy='constant', fill_value=0)
df_const = pd.DataFrame(imputer_const.fit_transform(df), columns=df.columns)

display(df_const)
```

## Ejercicio 7 Imputación Avanzada

```
import numpy as np

datos = np.array([10,12,14,15,16,18,20,22,25,100])

Q1 = np.percentile(datos, 25)
Q3 = np.percentile(datos, 75)

IQR = Q3 - Q1

lim_inf = Q1 - 1.5 * IQR
lim_sup = Q3 + 1.5 * IQR

outliers = datos[(datos < lim_inf) | (datos > lim_sup)]

print(outliers)
```

## Ejercicio 8 Métodod Z-Score

```
from scipy import stats
import numpy as np

datos = np.array([10, 12, 14, 15, 16, 18, 20, 22, 25, 100])

z_scores = stats.zscore(datos)

outliers = np.where(np.abs(z_scores) > 3)

print("Z-scores:", z_scores)
print("Outliers (índices):", outliers)
print("Valores atípicos:", datos[outliers])
```

## Ejercicio 9 Manejo de Outliers

(Según algunos traductores, el texto en Chino que se encuentra en el punto 2 de este ejercicio quiere decir algo como "Buscar / Reemplazar / Modificar el valor límite")

```
import numpy as np
from scipy.stats import boxcox

datos = np.array([10, 12, 14, 15, 16, 18, 20, 22, 25, 100])

Q1 = np.percentile(datos, 25)
Q3 = np.percentile(datos, 75)
IQR = Q3 - Q1

lim_inf = Q1 - 1.5 * IQR
lim_sup = Q3 + 1.5 * IQR

print("Límite inferior: ", lim_inf)
print("Límite superior: ", lim_sup)

datos_sin_outliers = datos[(datos >= lim_inf) & (datos <= lim_sup)]
print(datos_sin_outliers)

datos_capping = np.where(datos > lim_sup, lim_sup,
                 np.where(datos < lim_inf, lim_inf, datos))

print("Reemplazo por Límites: ")
print(datos_capping)

datos_log = np.log(datos)

print("Transformación: ")
print(datos_log)

datos_boxcox, lambda_ = boxcox(datos)

print("Box-Cox: ")
print("Lambda:", lambda_)
print(datos_boxcox)
```

## Ejercicio 10 Codificación de Variables Ctegóricas

```
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
import pandas as pd

df = pd.DataFrame({
    'color': ['rojo', 'azul', 'verde', 'rojo', 'verde'],
    'talla': ['S', 'M', 'L', 'S', 'M']
})

# Label
le = LabelEncoder()
df['color_label'] = le.fit_transform(df['color'])

# One-hot pandas
print(pd.get_dummies(df))

# One-hot sklearn
encoder = OneHotEncoder()
print(encoder.fit_transform(df[['color']]).toarray())
```

## Ejercicio 11 Transformaciones Numéricas

```
import numpy as np
import pandas as pd
from scipy import stats

datos = np.array([1, 2, 3, 4, 5, 10, 20, 30])

log = np.log(datos)
print("Logaritmo: ")
display(log)

sqrt = np.sqrt(datos)
print("Raíz: ")
display(sqrt)

boxcox = stats.boxcox(datos)
print("Box-Cox: ")
display(boxcox)

bins = pd.cut(datos, bins=3, labels=['Bajo', 'Medio', 'Alto'])
print("Discretización: ")
display(bins)
```

## Ejercicio 12 Feature Engineering

```
import pandas as pd
from sklearn.preprocessing import PolynomialFeatures

df_estudio = pd.DataFrame({
    'horas_estudio': [2, 4, 3, 6, 5],
    'horas_descanso': [8, 7, 6, 5, 6],
    'fecha': pd.date_range(start='2024-01-01', periods=5)
})

print("DataFrame Original: ")
print(df_estudio)

df_estudio['ratio_estudio_descanso'] = df_estudio['horas_estudio'] / df_estudio['horas_descanso']

df_estudio['diferencia_horas'] = df_estudio['horas_estudio'] - df_estudio['horas_descanso']

df_estudio['estudio_intenso'] = (df_estudio['horas_estudio'] > 4).astype(int)

poly = PolynomialFeatures(degree=2, include_bias=False)
poly_feat = poly.fit_transform(df_estudio[['horas_estudio', 'horas_descanso']])
poly_df = pd.DataFrame(poly_feat, columns=poly.get_feature_names_out())

print("Polynomial Features: ")
print(poly_df)

df_estudio['año'] = df_estudio['fecha'].dt.year
df_estudio['mes'] = df_estudio['fecha'].dt.month
df_estudio['dia'] = df_estudio['fecha'].dt.day

print("Feature Engineering: ")
print(df_estudio)
```

## Ejercicio 13 Comparar Escaladores

```
from sklearn.preprocessing import MinMaxScaler, StandardScaler, RobustScaler, MaxAbsScaler
import numpy as np
import pandas as pd

data = np.array([[1, 2, 3],
                 [4, 5, 6],
                 [7, 8, 9],
                 [10, 11, 12]])

df = pd.DataFrame(data, columns=['A', 'B', 'C'])

minmax = MinMaxScaler()
standard = StandardScaler()
robust = RobustScaler()
maxabs = MaxAbsScaler()
df_minmax = pd.DataFrame(minmax.fit_transform(df), columns=df.columns)
df_standard = pd.DataFrame(standard.fit_transform(df), columns=df.columns)
df_robust = pd.DataFrame(robust.fit_transform(df), columns=df.columns)
df_maxabs = pd.DataFrame(maxabs.fit_transform(df), columns=df.columns)

display(("Original:", df))
display("MinMaxScaler:", df_minmax)
display("StandardScaler:", df_standard)
display("RobustScaler:\n", df_robust)
display("MaxAbsScaler:\n", df_maxabs)
```

## Ejercicio 14 Pipeline de Procesamiento

```
import pandas as pd
import numpy as np
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.compose import ColumnTransformer

# Nuevo DataFrame: estadísticas de jugadores
df_jugadores = pd.DataFrame({
    'puntuacion': [1200, 2500, 1800, 3000],
    'tiempo_juego': [50, 120, 80, 200],
    'clase_personaje': ['guerrero', 'mago', 'arquero', 'mago']
})

print("Datos originales:")
print(df_jugadores)

columnas_numericas = ['puntuacion', 'tiempo_juego']
columnas_categoricas = ['clase_personaje']

preprocesador = ColumnTransformer(
    transformers=[
        ('escalado', StandardScaler(), columnas_numericas),
        ('codificacion', OneHotEncoder(), columnas_categoricas)
    ]
)

pipeline = Pipeline(steps=[
    ('pipeline_preprocesamiento', preprocesador)
])

resultado = pipeline.fit_transform(df_jugadores)

columnas_finales = (
    columnas_numericas +
    list(
        pipeline.named_steps['pipeline_preprocesamiento']
        .named_transformers_['codificacion']
        .get_feature_names_out(columnas_categoricas)
    )
)

df_final = pd.DataFrame(resultado, columns=columnas_finales)

print("Transformados: ")
print(df_final)
```

## Ejercicio 15 Mejores Prácticas

La preparación de datos es importante porqué es necesario mrjorar la preparación de los modelos y poder de esta manera evitar los resultados incorrectos para que los algoritmos funcionen correctamente y reducir la posibilidad de errores

El data leakage es la filtración de datos casi siempre confidenciales, y se puede evotar mediante la limitación de aquellos con acceso, mejorar la seguridad en el endpoint, y cifrar los datos para dificultar su lectura

Los datos de entrenamiento son aquellos que se utilizan para entrenar al modelo y permitirle identificar patrones, y los de prueba para evaluar el rendimiento final con información nueva y diferente

## Ejercicio 16 Técnicas Avanzadas

El SMOTE para datos desbalanceados es una técnica en la cuál en lugar de duplicar la clase minoritaria, se crean nuevos ejemplos mediante la interpolación

La imputación por K-nearest neighbor es una técnica de procesamiento de datos que se utiliza para calcular valores faltantes en un conjunto de datos

El target encoding es una técnica para transformar variables categoricas en numéricas y crear relaciones directas
