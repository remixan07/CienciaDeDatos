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
