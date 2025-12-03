---
title: Tarea final
publish: true
---

## Objetivo

Aplicar los conocimientos adquiridos en la sección de visualización para crear gráficos informativos y estéticamente agradables a partir de un conjunto de datos real.

## Recursos

Encontrarás el archivo `data/exoplanets.csv` en el repositorio del curso.
Este dataset cuenta con información sobre avistamientos de exoplanetas, incluyendo características orbitales, físicas y estelares.

El dataset puede incluir múltiples entradas por exoplaneta debido a diferentes métodos de detección o actualizaciones. Para las visualizaciones que requieran datos únicos por exoplaneta, utiliza únicamente el registro más reciente de cada exoplaneta. Para ello, agrupa por `planet_name` y conserva el registro con la `last_update_date` más reciente.

## Entrega

Entrega un archivo `.ipynb` que contenga el código necesario para realizar las tareas descritas en la sección de detalle y las visualizaciones logradas.
Asegúrate de que solo esté el código necesario para resolver las tareas, sin incluir códigos de pruebas o salidas intermedias.
Añade comentarios explicativos en caso de ser necesario.
No es necesario incluir las figuras exportadas, pero los comandos para guardarlas sí deben estar presentes en el notebook.

## Detalle

1. Crea un histograma que muestre la distribución de los radios planetarios (en radios terrestres).

   - Solo grafica planetas con radio menor a 25 radios terrestres para una mejor visualización.
   - Añade una curva KDE superpuesta.
   - Incluye líneas verticales de referencia que indiquen el radio de la Tierra y el de Júpiter.

2. Crea un gráfico de dispersión que muestre la relación entre la masa y el radio planetario, incluyendo distribuciones en los márgenes del gráfico.

   - Utiliza escala logarítmica en ambos ejes.
   - Colorea los puntos según el número de planetas en el sistema (agrupa como "4+" los sistemas con 4 o más planetas).
   - Excluye los registros con valores nulos en masa o radio para una mejor visualización.

3. Crea un gráfico compuesto con 3 paneles centrado en los descubrimientos de exoplanetas:

   - Distribución temporal de descubrimientos. Utiliza un gráfico de líneas que muestre el número de exoplanetas descubiertos por año.
   - Total de exoplanetas descubiertos por método de detección. Utiliza un gráfico de barras horizontales con escala logarítmica y añade etiquetas con el valor al final de cada barra.
   - Un gráfico adicional de tu elección que aporte información complementaria sobre los descubrimientos.

4. Crea un gráfico de distribución en 2 dimensiones (histograma 2D o hexbin) que muestre la densidad de exoplanetas en el espacio definido por la temperatura efectiva estelar (`stellar_effective_temperature_k`) y la temperatura de equilibrio del planeta (`equilibrium_temperature_k`).

   - Filtra planetas con temperatura de equilibrio menor a 4000 K.
   - Añade una banda horizontal semitransparente indicando la "zona habitable" aproximada (250-350 K).
   - Incluye una línea vertical de referencia para la temperatura del Sol (5778 K).

5. Construye una figura compuesta que muestre los avistamientos de exoplanetas por año e instalación. Extrae el año a partir de `last_update_date`. Excluye el telescopio Kepler (para evitar sesgo por su alta productividad) y las instalaciones con menos de 30 avistamientos. La figura debe tener la siguiente disposición en forma de grilla:

   - Superior izquierda: gráfico de barras con el total de exoplanetas por año (solo años presentes en el heatmap). Debe ocupar 1/5 de la altura total.
   - Inferior izquierda: heatmap del total de exoplanetas por año y por instalación de descubrimiento (`discovery_facility`). Minimiza el efecto de outliers en la escala de color.
   - Inferior derecha: barra de color del heatmap en panel independiente, ocupando 1/10 del ancho total.
   - Superior derecha: dejar vacío o invisible.

6. Crea una visualización que muestre la posición de los exoplanetas en coordenadas celestes (ascensión recta `ra_deg` y declinación `dec_deg`). Analiza brevemente: ¿se observan concentraciones en ciertas regiones del cielo? Investiga si alguna de las variables del dataset puede explicar estas concentraciones y añade esta información a la visualización.

7. Define criterios para identificar exoplanetas "potencialmente habitables": temperatura de equilibrio entre 200-350 K y radio entre 0.5-2 radios terrestres. Crea una visualización que permita explorar comparativamente estos planetas con el resto del catálogo, destacando en qué se diferencian (considera propiedades como masa, período orbital, temperatura estelar, etc.). También evalúa la distancia a la que están estos exoplanetas de la Tierra. En las visualizaciones que elijas, incluye el valor referencial de la Tierra y/o Sol cuando sea pertinente.

## Requisitos generales

- Utiliza títulos descriptivos y etiquetas en los ejes.
- Asegúrate de que la leyenda esté presente si se necesita para comprender el gráfico y que no obstruya la visualización de los datos.
- Guarda cada gráfico en dos formatos: uno vectorial y otro no vectorial de alta resolución. Utiliza solo un formato por cada tipo (por ejemplo, .svg o .pdf para vectorial y .png o .jpg para no vectorial).
