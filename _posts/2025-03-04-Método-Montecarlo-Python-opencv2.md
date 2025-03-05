---
title: "Ejemplo de Consulta SQL con Visualización"
date: 2025-03-04
categories: [SQL, Tutorial]
tags: [SQL, consultas, visualización]
---

## Introducción
En esta entrada, mostraremos cómo realizar una consulta en SQL para contar el número de registros en una tabla y visualizar los resultados en un gráfico.

## Consulta SQL
A continuación, presentamos una consulta SQL simple para contar la cantidad de empleados por departamento en una base de datos empresarial.

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

Esta consulta agrupa a los empleados por departamento y cuenta cuántos hay en cada uno.

## Visualización del Resultado
Para representar los resultados gráficamente, podemos usar Python y la biblioteca Matplotlib. Aquí un ejemplo:

```python
import matplotlib.pyplot as plt

departments = ["Ventas", "IT", "Marketing", "RRHH"]
employee_counts = [30, 25, 15, 10]

plt.bar(departments, employee_counts, color=['blue', 'red', 'green', 'purple'])
plt.xlabel("Departamento")
plt.ylabel("Número de empleados")
plt.title("Distribución de empleados por departamento")
plt.show()
```

## Figura Resultante
A continuación, una imagen que representa la distribución de empleados por departamento.

![Distribución de empleados](https://via.placeholder.com/600x400.png?text=Grafico+Ejemplo)

## Conclusión
Este ejemplo muestra cómo podemos extraer datos con SQL y representarlos gráficamente para obtener mejores insights visuales. ¡Esperamos que te sea útil!
