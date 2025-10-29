# Tarea Final 1: Manipulación y Transformación de Datos con Polars

## Objetivo

Aplicar los conocimientos adquiridos en la sección de Polars para manipular y transformar datos en un conjunto de datos real.

## Recursos

Encontrarás los siguientes archivos en https://github.com/JacquelineAldridge/data-visualization-notebooks/tree/main/tareas/1.final/data:

- `dataset_1.csv`: Archivo CSV usado en clases anteriores.
- `dataset_2.tsv`: Archivo TSV con información de pacientes adicionales.
- `institute_neighborhoods.csv`: Archivo CSV que contiene información de vecindarios asociados a institutos.
- `last_visit_info.csv`: Archivo CSV con información de las últimas visitas de los pacientes.

## Entrega

Entrega un archivo `.py` o `.ipynb` que contenga el código necesario para realizar las tareas descritas en la sección de detalle. Asegúrate de que sólo esté el código necesario para resolver las tareas, sin incluir códigos de pruebas o salidas intermedias. Añade comentarios explicativos en caso de ser necesario.

**Fecha de Entrega: 21 de octubre de 2025**

## Detalle

### 1. Clasificación de desórdenes genéticos

Usando `dataset_2.tsv`, crea una nueva columna llamada "Disorder Subclass" y asigna valores según el tipo de desorden genético de cada registro:

- Cuando el desorden genético sea "Multifactorial genetic inheritance disorders", asigna "Diabetes" en la columna disorder subclass.
- Cuando el desorden genético sea "Mitochondrial genetic inheritance disorders", asigna "Mitochondrial myopathy" en la columna disorder subclass.
- Cuando el desorden genético sea "Single-gene inheritance diseases", asigna "Cystic fibrosis" en la columna disorder subclass.

### 2. Integración y transformación de datos

Une verticalmente `dataset_1` y `dataset_2` en un único DataFrame (concatenación) y utiliza este DataFrame resultante para realizar las siguientes operaciones:

- Selecciona solo aquellos pacientes que cuenten con consentimiento de los padres y cuyo lugar de nacimiento haya sido un instituto.

- Añade una nueva columna (`age_group`) que clasifique a los pacientes por grupo etario. Para ello, utiliza la siguiente clasificación:

  - "Newborn": 0 años
  - "Early childhood": 1 - 7 años
  - "Late childhood": 8 años o más

- Integra la información del vecindario de cada paciente a partir del archivo `institute_neighborhoods.csv`. Excluye aquellos registros que no tengan información de vecindario. Deja los valores de todos los vecindarios en mayúsculas.

- Cambia el tipo de dato de todas las columnas que puedan representarse con un tipo más apropiado:

  - Aquellas columnas que puedan representarse con un tipo lógico (True / False) y no lo estén, cámbialas a tipo booleano.
  - Aquellas columnas que almacenan valores numéricos enteros y se encuentren con otro tipo de dato (como float o string), transfórmalas a entero.

### 3. Tabla resumen de pacientes

Con base en el DataFrame creado en el punto 2, crea una tabla resumen que presente la cantidad de pacientes agrupados por desorden genético, categorización de edad, vecindario y género. Descarta los registros que no tengan información del desorden genético o del género. El DataFrame debe tener la siguiente estructura:

| genetic_disorder                             | age_group       | neighborhood | male | female | ambiguous | total |
| :------------------------------------------- | --------------- | ------------ | ---- | ------ | --------- | ----- |
| Multifactorial genetic inheritance disorders | Newborn         | ROXBURY      | 35   | 27     | 20        | 82    |
| Multifactorial genetic inheritance disorders | Early childhood | SOUTH END    | 3    | 6      | 8         | 17    |
| Mitochondrial genetic inheritance disorders  | Newborn         | ROSLINDALE   | 29   | 28     | 26        | 83    |
| ...                                          |                 |              |      |        |           |       |

La columna `total` debe contener la suma de las columnas `male`, `female` y `ambiguous`. Rellena con 0 los valores faltantes en las columnas de conteo. Ordena la tabla descendentemente según la columna `total`.

### 4. Análisis de factores de riesgo

Genera un DataFrame que contenga tres columnas: `birth_defects`, `history_of` y `count`. La columna `history_of` debe contener la información:

- H/O serious maternal illness
- H/O radiation exposure (x-ray)
- H/O substance abuse

Cuando no haya defectos de nacimiento, la columna `birth_defects` debe contener el valor "No". La columna `count` debe contener la cantidad de registros en los que la columna correspondiente de historial (`history_of`) tenga un valor positivo. Descarta los registros que contengan valores inválidos o faltantes como "-99", "-", espacios vacíos, etc.

Añade la columna `percentage_by_ho` con el porcentaje que representa cada fila con respecto al total de registros por H/O.

### 5. Procesamiento de información de visitas

En el archivo `last_visit_info.csv` encontrarás el detalle de las últimas visitas de los pacientes. Este archivo contiene dos columnas:

- `Patient Id`: Identificador del paciente, que coincide con la columna `Patient ID` del DataFrame creado en el punto 2.
- `LastVisitInfo`: Información de la última visita en formato JSON. Contiene la fecha de la última visita, nombre del doctor, razón, entre otros.

Extrae la fecha de la última visita del JSON y guárdala en una nueva columna llamada `last_visit_date`, y haz lo mismo con `next_appointment`. Posteriormente, integra esta información al DataFrame creado en el punto 2 usando el identificador del paciente.

Finalmente, responde: ¿Cuántos pacientes del grupo etario "Early childhood" tienen una cita programada para noviembre o diciembre de 2025, y además la diferencia en días entre su última visita y la cita programada es menor a 150 días?

**Tips:**

- Para cargar los datos en formato JSON, puedes usar el módulo `json` de Python:

  ```python
  import json

  # Transforma `json_string` en un diccionario de Python
  data = json.loads(json_string)
  ```

- Puedes extraer elementos del tipo fecha en Polars usando el espacio de nombres `dt`, por ejemplo: `pl.col("last_visit_date").dt.total_days()`.
