# Práctica 1 Redes de Neuronas
## Introducción
El objetivo de esta práctica es abordar un problema real de regresión utilizando dos
modelos de redes de neuronas supervisados:

- El modelo lineal Adaline.

- El modelo no-lineal Perceptrón Multicapa.

Se trabajará con el conjunto de datos real de regresión conocido como “Gas Turbine CO
and NOx Emission Data Set”. El dataset consiste en una colección de medidas realizadas
en una turbina de gas a lo largo de 4 años, existiendo medidas de múltiples sensores con
el propósito de predecir las emisiones producidas por la combustión. El conjunto de datos
dispone de un un total de 36733 instancias que representan las mediciones de un total de
11 sensores. Cada instancia representa la media de mediciones durante una hora.

La siguiente lista muestra un desglose de las distintas mediciones del dataset:

- Ambient temperature (AT) medido en grados Celsius, con un valor mínimo de
6.23 un máximo de 37.10 y una media de 17.71.
- Ambient pressure (AP) medido en grados milibares, con un valor mínimo de
985.85 un máximo de 1036.56 y una media de 1013.07.
- Ambient humidity (AH) medido en porcentaje de humedad, con un valor mínimo
de 24.08 un máximo de 100.20 y una media de 77.87.
- Air filter difference pressure (AFDP) medido en milibares, con un valor mínimo
de 2.09 un máximo de 7.61 y una media de 3.93.
- Gas turbine exhaust pressure (GTEP) medido en milibares, con un valor mínimo
de 17.70 un máximo de 40.72 y una media de 25.56.
- Turbine inlet temperature (TIT) medido en grados Celsius, con un valor mínimo
de 1000.85 un máximo de 1100.89 y una media de 1081.43.
- Turbine after temperature (TAT) medido en grados Celsius, con un valor mínimo
de 511.04 un máximo de 550.61 y una media de 546.16.
- Compressor discharge pressure (CDP) medido en grados milibares, con un valor
mínimo de 9.85 un máximo de 15.16 y una media de 12.06.
- Turbine energy yield (TEY) medido en grados megavatios hora, con un valor
mínimo de 100.02 un máximo de 179.50 y una media de 133.51.
- Carbon monoxide (CO) medido en miligramos por metro cubico(mg/m3), con un
valor mínimo de 0 un máximo de 44.10 y una media de 2.37.
- Nitrogen oxides (NOx) medido en miligramos por metro cubico(mg/m3), con un
valor mínimo de 25.90 un máximo de 119.91 y una media de 65.29.

En el caso de la práctica se busca predecir el Rendimiento energético de la turbina,
mostrado en campo TEY, haciendo uso del resto de mediciones de sensores.

En el siguiente enlace puede obtenerse más información sobre los atributos y la variable
de salida:
https://archive.ics.uci.edu/dataset/551/gas+turbine+co+and+nox+emission+data+set
Los datos que serán utilizados para la realización de la práctica podrán descargarse en la
sección Práctica 1 en Aula Global.
