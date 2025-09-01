# Tareas - Sección 2.1: Fundamentos de Polars

## 1. Carga de archivos

Dentro de la carpeta `datos/` encontrarás los siguientes archivos:

1. `empleados.csv`
2. `productos.csv` (pista: piensa en los nombres de columnas)
3. `experimento.csv`
4. `ventas_mensual.csv`
5. `inventario_semanal.csv`

Intenta cargar cada uno de ellos usando pl.read_csv(). Identifica si hay algún problema con la carga de los datos y soluciónalo.

## 2. Selección de columnas

Usando el dataset de prueba del curso:

1. Crea una vista con ID, edad, género y estado vital de los pacientes
2. Encuentra todas las columnas de texto que contengan información sobre el lugar (pista: busca "Place", "Location", "Institute")
3. Crea una tabla solo con las 5 columnas de síntomas
4. ¿Cuantas columnas no numéricas hay?

## 3. Operaciones sobre columnas

1. Calcula estadísticas completas solo para las variables de conteo sanguíneo (las 2 columnas "Blood")
2. ¿Cuántos subtipos diferentes de trastornos hay en el dataset?
3. Cuenta cuántos valores únicos hay en cada una de las columnas de resultados médicos (que contengan "result")
