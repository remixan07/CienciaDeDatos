<sub><sup>Nombre: José Antonio Reséndiz García; 
Matrícula: T03032639; 
Fecha: 3 de Abril de 2026; 
Semestre: 2°; 
Materia: Ciencia de Datos; 
Maestr@: Ricardo Alfredo Monroy Rodríguez

</sup></sub>
# Ejercicios Semana 2

## Ejercicio 2.1- Consultas Básicas

sql
SELECT * FROM empleados;

sql
SELECT nombre, salario
FROM empleados
WHERE departamento = 'IT';

sql
SELECT *
FROM empleados
ORDER BY salario DESC
LIMIT 1;

sql
SELECT departamento, COUNT(*) AS total_empleados
FROM empleados
GROUP BY departamento;

sql
UPDATE empleados
SET salario = 50000
WHERE nombre = 'María';

## Ejercicio 2.2 - Joins

sql
SELECT empleados.id, empleados.nombre, departamentos.nombre AS departamento
FROM empleados
INNER JOIN departamentos
ON empleados.id_departamento = departamentos.id;

sql
SELECT empleados.id, empleados.nombre, departamentos.nombre AS departamento
FROM empleados
LEFT JOIN departamentos
ON empleados.id_departamento = departamentos.id;

sql
SELECT departamentos.nombre AS departamento, COUNT(empleados.id) AS total_empleados
FROM departamentos
LEFT JOIN empleados
ON empleados.id_departamento = departamentos.id
GROUP BY departamentos.nombre;

## Ejercicio 2.3 - Manipulación de JSON

https://github.com/remixan07/CienciaDeDatos/blob/main/Semana%202/Ejercicios/Ejercicio%202.3.ipynb

## Ejercicio 2.4 - Estructuras de Datos en Python

https://github.com/remixan07/CienciaDeDatos/blob/main/Semana%202/Ejercicios/Ejercicio%202.4.ipynb

## Ejercicio 2.5 - Operaciones CRUD

https://github.com/remixan07/CienciaDeDatos/blob/main/Semana%202/Ejercicios/Ejercicio%202.5.ipynb

## Ejercicio 2.6 - Consultas Avanzadas en MongoDB

https://github.com/remixan07/CienciaDeDatos/blob/main/Semana%202/Ejercicios/Ekjercicio%202.6.ipynb

## Ejercicio 2.7 - Tipos de Bases de Datos NoSQL

| Nombre | Qué Es | Se Utiliza | Ventajas | Desventajas |
| :---: | :---: | :---: | :---: | :---: |
| MongoDB | Almacena datos de manera parecida a JSON | Obtener flexibilidad en los fdatos | Estructura flexible y facil de escalar | Puede duplicar datos |
| CouchDB | Almacena datos sincronizados similar a JSON | Datos sincronizados o sin conexión | Trabajo online y replica datos | Mayor lentitud |
| Redis | Base de datos en memoria rápida | Aplicaiones en tiempo real | Rápida y soporta estructuras simples | Los datos crashean constantemente |
| DyanmoDB | AWS en la nube |Tener disponibilidad escalable automática | Buen rendimmiento | Necesita AWS y es costosa |
| Cassandra | Base de grandes dartos | Grandes cantidades de datos | Tolerante a fallos y escalable | Difícil de configurar y limitada |
| HBase | Basse de Datos masivos | Análisis Big data | Grandes volúmenes y escalable | Compleja y gran infraestructura |
| Neo4j | Base de datos en nodos y relaciones | Grandes realciones | Consultas rápidas | No recomendada en datos simples |

## Ejercicio 2.8 - Arquitecturas de Almacenamiento

Los data lakes son repositorios que almacenan datos en crudo para exploraciones de datos, permitiendo escalabilidad e ingesta rápida de datos

Los data warehouse son sistemas que almacenan datos estructurados varios de varias fuentes que mantienen un registro histórico para permitir consultas rápidas y facilitar la analítica

El OLTP sirve más para un procesamiento en transaccicones manejar operaciones actuales y manejar operaciones diarias; mientras que el OLTP es más recomendado para el procesamiento analítico de datos históricos, y la toma de decisiones

El ETL es unn proceso de integración de datos que permite el obtener datos de diversas fuentes. limpiarlos y organizarlos, y guaradrlos en un sistema
