# Práctica 1 Redes de Neuronas
## 1.- Introducción
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

## 2.- Trabajo a realizar
### 2.1.- Preparación de datos
Antes de realizar el aprendizaje de las redes, hay que realizar un preproceso de los datos
disponibles:

- Normalización: Es recomendable normalizar las variables de entrada y salida en
el rango [0, 1]. Para la normalización se calculará el valor mínimo y máximo de
cada variable i y se aplicará la siguiente transformación lineal:
![image](https://github.com/cabamarcos/P1-RRNN/assets/98906745/96b29619-f144-43d8-849f-62bc6c68279d)

- Aleatorización: Para que el entrenamiento de las redes se realice en condiciones
adecuadas es importante desordenar o ‘aleatorizar’ los datos.
- Separación de tres conjuntos de datos:
  · Datos de entrenamiento (70% del total de datos) para realizar el
aprendizaje de la red.
  · Datos de validación (15% del total de datos) que serán utilizados para
elegir los valores óptimos de los hiperparámetros de la red (razón de
aprendizaje, número de ciclos, número de neuronas en Perceptrón
Multicapa).
  · Datos de test (15% del total de datos) para evaluar la capacidad de
generalización de la red. Por tanto, cuando finalice esta fase, deberá
disponerse de tres ficheros (entrenamiento, validación y test) con los datos
normalizados y que serán usados para entrenar tanto los modelos lineales
(Adaline) como los no lineales (Perceptrón Multicapa).

### 2.2.- Parte 1: Desarrollo y experimentación con Adaline
Debido a la sencillez de esta red, no se utilizarán librerías, sino que se desarrollará un
programa que realice desde cero el aprendizaje y evaluación de Adaline, explicado en las
clases de teoría. Dicho programa se puede desarrollar en el lenguaje de programación que
los alumnos decidan. El objetivo es comprender con todo detalle el funcionamiento de
esta red sencilla. Esto ayudará a comprender redes más complejas que ya no habrá que
programar, sino que se usarán las librerías correspondientes.
Para verificar que el programa funciona correctamente, es aconsejable mostrar en pantalla
el error medio a lo largo de los ciclos de aprendizaje (como se muestra en la siguiente
tabla). El error de entrenamiento debe ir decreciendo o permanecer constante. El error de
validación debe ir decreciendo, aunque pudiera aumentar, lo que significa que se está
produciendo sobreaprendizaje.
![image](https://github.com/cabamarcos/P1-RRNN/assets/98906745/35677c4e-859e-4313-b41a-14c83be1acf6)

Además de realizar el aprendizaje de la red, el programa debe:

- Calcular el error sobre el conjunto de test una vez finalizado el aprendizaje.
- Guardar en fichero las salidas de la red para todas las instancias de test.
- Guardar en fichero el modelo, es decir, los pesos y el umbral (bias) de la red una
vez finalizado el aprendizaje.

Con los datos procesados y el programa desarrollado, se realizarán diferentes
experimentos cambiando el valor de la razón de aprendizaje, con el objetivo de encontrar
el valor más adecuado para el problema dado. El valor óptimo se elegirá utilizando el
error de validación. El número de ciclos de aprendizaje más adecuado para cada razón de
aprendizaje hay que ajustarlo a cada experimento para conseguir la estabilización del
error de entrenamiento y validación. Se obtendrá de la siguiente manera:

- Se entrena la red durante un número de ciclos máximo.
- Se obtiene el número de ciclos que minimiza el error de validación (número de
ciclos óptimo). Nuestro modelo final entrenado será el que corresponda con el
menor error de validación. Esto podrá conseguirse de cualquiera de las siguientes
formas:

  · Se repite el entrenamiento con los mismos valores aleatorios iniciales,
pero solo el número de ciclos que minimizaban el error de validación.
  · Se entrena la red una sola vez, pero en cada ciclo guardamos el modelo si
el error de validación es menor que el obtenido hasta este momento.
Cuando lleguemos al número de ciclos máximo tendremos guardado el
mejor modelo.
- Con este modelo final entrenado, se utilizará el conjunto de test para comprobar
la capacidad de generalización de la red.

## 2.3 Parte 2: Experimentación con el Perceptrón Multicapa
Para el uso de Perceptrón Multicapa (PM) se utilizará el entorno Google Colab con Keras,
utilizando el lenguaje Python. En aula Global se facilitará un documento donde se facilita
un script básico que habrá que modificar para realizar la experimentación pedida.

En la experimentación con el PM se realizarán diferentes pruebas, cambiando el número
de neuronas ocultas y la razón de aprendizaje, con el objetivo de encontrar los valores
más adecuados para el problema que se pretende resolver. Los valores óptimos se elegirán
utilizando el error de validación. El profesor dará en clase indicaciones sobre el número
de experimentos recomendable. Igual que con Adaline, el número de ciclos de aprendizaje
más adecuado para cada configuración hay que ajustarlo a cada experimento para
conseguir minimizar el error de validación.

Una vez finalizado el aprendizaje, se utilizará el conjunto de test para comprobar la
capacidad de generalización de la red.
NOTA IMPORTANTE: Para poder comparar los resultados del PM con los resultados de
Adaline, debe utilizarse el mismo tipo de error en ambos modelos. Se recomienda utilizar
el error medio absoluto (MAE) o el error cuadrático medio (MSE).

