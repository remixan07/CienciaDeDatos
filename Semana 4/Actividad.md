# Actividad 33

```
import pandas as pd
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "jugador": [
        "Andy Pages","Yandy Diaz","CJ Abrams","Chandler Simpson","Xavier Edwards",
        "Ryan O'Hearn","Mauricio Dubon","Wilyer Abreu","Yordan Alvarez","Otto Lopez",
        "Luke Raley","Ben Rice","Nico Hoerner","Shea Langeliers","Vladimir Guerrero Jr.",
        "Drake Baldwin","Jordan Walker","William Contreras","Colt Keith","Brandon Nimmo",
        "Oneil Cruz","Brendan Donovan","Christian Yelich"
    ],
    "bateos": [66,70,62,69,71,63,66,66,67,67,61,55,71,71,65,78,69,63,60,76,76,54,51],
    "carreras": [10,11,12,9,14,9,11,9,16,12,8,16,12,13,7,19,15,9,10,12,15,7,10]
})

print(Datos: ")
print(df)

print("Valores Faltantes: ")
print(df.isnull().sum())

from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df[['bateos_std','carreras_std']] = scaler.fit_transform(df[['bateos','carreras']])

print("Estandarizados: ")
print(df)

correlacion = df["bateos"].corr(df["carreras"])
print("Correlación: ", correlacion)

plt.figure()
plt.scatter(df["bateos"], df["carreras"])
plt.xlabel("Bateos (AB)")
plt.ylabel("Carreras (R)")
plt.title("Bateos vs Carreras: ")
plt.show()

plt.figure()
plt.bar(df["jugador"], df["carreras"])
plt.xticks(rotation=90)
plt.title("Carreras por jugador: ")
plt.show()

plt.figure()
plt.hist(df["bateos"])
plt.title("Distribución de Bateso: ")
plt.show()

X = df[["bateos"]]
y = df["carreras"]

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42
)

from sklearn.linear_model import LinearRegression

modelo = LinearRegression()
modelo.fit(X_train, y_train)

y_pred = modelo.predict(X_test)

print("Predicciones: ")
print(y_pred)

from sklearn.metrics import mean_squared_error, r2_score

mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print("Mse: ", mse)
print("R2:", r2)

plt.figure()
plt.scatter(X_test, y_test)
plt.plot(X_test, y_pred)
plt.title("Regresión lineal")
plt.xlabel("Bateos")
plt.ylabel("Carreras")
plt.show()
