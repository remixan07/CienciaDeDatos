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

## Ejercicio 2.5 - Estructuras de Datos en Python

https://github.com/remixan07/CienciaDeDatos/blob/main/Semana%202/Ejercicios/Ejercicio%202.5.ipynb
