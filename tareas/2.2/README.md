# Ejercicios de Filtros de Datos - Sección 2.2

Dataset: `dataset_sample.csv` - Datos de pacientes con trastornos genéticos

## 1. Filtros

1. ¿Cuántos pacientes tienen más de 10 años de edad?
2. ¿Qué pacientes tienen entre 5 y 12 años Y están diagnosticados con "Cystic fibrosis"?
3. ¿Qué pacientes no tienen información del gen paterno (valores nulos) y son del género "Female"?
4. ¿Qué pacientes tienen trastorno "Single-gene inheritance diseases" O "Multifactorial genetic inheritance disorders" y están vivos?
5. Obtén la media y desviación estándar del recuento de células sanguíneas (`Blood cell count`) de los pacientes que estén vivos (`Status == "Alive"`) y tengan gen materno "Yes".


## 2.Manejo de valores nulos y ordenamiento

1. ¿Qué columna es la que posee más valores nulos?
2. ¿Cuántos pacientes hay que no tengan ningún valor nulo en cualquiera de sus columnas?
3. ¿Cuántos pacientes no tienen consentimiento informado o no se tiene información al respecto?. Elimina estos registros y guarda el resultado en un nuevo DataFrame ¿Cuántos pacientes quedan después de esta operación?
4. ¿Cuántos pacientes no tienen informado un desorden genético pero si tienen asociada una subclase de desorden genético?
5. Completa los valores nulos con la siguiente información y comprueba como cambian las estadísticas:
   - Valor mínimo
   - Valor máximo
   - "No informado"
   - 0
6. Utilizando el DataFrame generado en el punto 3:
   - Muestra las edades y desorden genético de los 10 pacientes con mayor conteo de glóbulos blancos.
   - Selecciona los cinco pacientes de menor edad que tengan múltiples defectos al nacer y su primer nombre sea Sandra.
   - Ordena los registros por el id del paciente, edad y desorden genético . Se debe ordenar en forma ascendente el id y la edad y de forma descendente el desorden genético Los registros nulos deben quedar al final del DataFrame.
