---
title: "Método Montecarlo en Python con opencv2"
date: 2025-03-04
categories: [python, algoritmos]
tags: [Python, Algoritmos, Visualización]
---

## Introducción
En esta entrada, mostraremos cómo realizar un Monte Carlo para aproximar y visualizar los resultados en un gráfico.

## Consulta SQL
A continuación, presentamos una consulta SQL simple para contar la cantidad de empleados por departamento en una base de datos empresarial.

## Visualización del Resultado
Para representar los resultados gráficamente, podemos usar Python opencv. Aquí un ejemplo:

```python
import numpy as np
import cv2
import random

def estimar_pi_montecarlo(n, k):
    # Crear imagen blanca (matriz de 255 en escala de grises)
    imagen = np.ones((n, n, 3), dtype=np.uint8) * 255
    
    # Centro y radio del círculo (cuarto de círculo en el primer cuadrante)
    centro = (0, 0)
    radio = n
    dentro_circulo = 0
    
    # Dibujar k puntos aleatorios y contar los que están dentro del círculo
    for _ in range(k):
        x = random.randint(0, n-1)
        y = random.randint(0, n-1)
        
        distancia = np.sqrt(x**2 + y**2)
        if distancia <= radio:
            dentro_circulo += 1
            imagen[y, x] = (0, 255, 0)  # Verde si está dentro del círculo
        else:
            imagen[y, x] = (0, 0, 255)  # Rojo si está fuera
    
    # Calcular estimación de pi
    pi_estimado = (dentro_circulo / k) * 4
    
    # Dibujar el borde del cuarto de círculo
    for x in range(n):
        for y in range(n):
            if np.abs(np.sqrt(x**2 + y**2) - radio) < 1:
                imagen[y, x] = (255, 0, 0)  # Azul para el borde del círculo
    
    
    
    # Mostrar imagen con puntos generados
    cv2.imshow("calculo de Pi con Montecarlo", imagen)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
    
    print(f" puntos dentro del circulo {dentro_circulo}")
    print(f" puntos fuera del circulo {k - dentro_circulo}")
    print(f"Estimación de π: {pi_estimado}")

# Parámetros: tamaño de imagen (n) y cantidad de puntos (k)
n = 500  # Tamaño de la imagen (500x500)
k = 10000   # Número de puntos aleatorios

estimar_pi_montecarlo(n, k)
****
```

## Figura Resultante
A continuación, una imagen que representa la distribución de empleados por departamento.

![Resultado Gráfico](.img/monte_carlo_python_opencv.png)

## Conclusión
Este ejemplo muestra cómo podemos aproximar $ \pi $!
