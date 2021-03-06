COMPARATIVA DE LOS MODELOS APLICADOS
------------------------------------

### MODELOS DE CLASIFICACIÓN

#### MODELO DE CLASIFICACIÓN CON GLM

Los resultados obtenidos para la clasificación con GLM:

<table style="width:104%;">
<colgroup>
<col width="29%" />
<col width="12%" />
<col width="13%" />
<col width="15%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">AIC</th>
<th align="left">R^2</th>
<th align="left">Accuracy</th>
<th align="left">Precisión</th>
<th align="left">Recall</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">model_train_clas</td>
<td align="left">335.472</td>
<td align="left">0.2720185</td>
<td align="left"><strong>0.6608617</strong></td>
<td align="left">0.3029006</td>
<td align="left">0.006511096</td>
</tr>
<tr class="even">
<td align="left">model_down_clas</td>
<td align="left">139.578</td>
<td align="left">0.299275</td>
<td align="left">0.1950311</td>
<td align="left"><strong>0.7569576 </strong></td>
<td align="left">0.006766421</td>
</tr>
</tbody>
</table>

"model\_train\_clas" En el caso del fichero train en el que la clase
está desequilibrada, cualquier modelo que no tenga ninguna clase de
penalización tenderá a clasificar en la clase mayoritaria, en este caso
0, por lo que el Accuracy tenderá a ser elevado aunque no prediga bien
ya que un alto porcentaje de los datos tienen importe 0.

"model\_down\_train" En el caso del fichero equilibrado (under-sampling)
sucede lo contrario, el Accuracy es menor porque tiende a equilibrar y a
predecir tantos casos de una clase como de la otra. La precisión
aumentará porque el número de TRUE POSITIVE aumenta pero también lo hace
el número de False Positive que es muy elevado, esto sucede porque
clasifica con una probabilidad aproximadamente del 50% para cada clase.

Con esta tabla podemos comprobar que el modelo que mejor se ajusta está
entrenado con el train equilibrado, basándonos en su precisión del 75%.
Su matriz de confusión es la siguiente:

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">no</th>
<th align="left">si</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">no</td>
<td align="left">624705</td>
<td align="left">5790</td>
</tr>
<tr class="even">
<td align="left">si</td>
<td align="left">2647039</td>
<td align="left">18033</td>
</tr>
</tbody>
</table>

Como podemos ver aunque el porcentaje de precisión es alto, la
clasificación no es buena puesto que el número de Falsos Positivos es
muy elevado, con lo que podemos confirmar que con el modelo de Lineal
Generalizado las variables independientes no aportan información
significativa para clasificar.

#### MODELO DE CLASIFICACIÓN CON RANDOM FOREST

Hemos realizado la clasificación tanto con el paquete randomForest como
el paquete Caret con k-folder. Los resultados para los dos ficheros, el
desequilibrado y el equilibrado mediante método Under-Sampling son los
siguientes:

<table>
<thead>
<tr class="header">
<th align="left">MODELO</th>
<th align="left">Accuracy</th>
<th align="left">Precisión</th>
<th align="left">Recall</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">RF Train</td>
<td align="left"><strong>0.730748</strong></td>
<td align="left">0.2409016</td>
<td align="left">0.00655891</td>
</tr>
<tr class="even">
<td align="left">RF Train Caret</td>
<td align="left">0.6445112</td>
<td align="left">0.3096168</td>
<td align="left">0.006345132</td>
</tr>
<tr class="odd">
<td align="left">RF Train down</td>
<td align="left">0.194633</td>
<td align="left">0.7939806</td>
<td align="left">0.007089187</td>
</tr>
<tr class="even">
<td align="left">RF Train down Caret</td>
<td align="left">0.1789495</td>
<td align="left"><strong>0.8170256</strong></td>
<td align="left">0.007153431</td>
</tr>
</tbody>
</table>

En el caso de los ficheros desequilibrados con alto porcentaje de
observaciones con clase 0, el Accuracy suele ser elevado puesto que
tiende a clasificar en la clase mayoritaria, no está clasificando todos
en 0 porque no estamos utilizando el fichero Train Completo, con el
fichero completo ningún modelo clasifica observaciones en la clase 1.

Al equilibrar el fichero tiende a clasificar el mismo número de
observaciones con clase 0 y con clase 1. Esto se suele solucionar
calibrando las probabilidades.

Calibrado de probabilidades para el modelo con mayor precisión
(clasificamos como 1 cuando la probabilidad es mayor que 0.6, 0.7 o 0.95
respectivamente):

<table>
<thead>
<tr class="header">
<th align="left">MODELO</th>
<th align="left">Accuracy</th>
<th align="left">Precisión</th>
<th align="left">Recall</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">RF Train down Caret 60</td>
<td align="left">0.2439089</td>
<td align="left">0.7481426</td>
<td align="left">0.0071190</td>
</tr>
<tr class="even">
<td align="left">RF Train down Caret 70</td>
<td align="left">0.3178382</td>
<td align="left">0.6653654</td>
<td align="left">0.0070261</td>
</tr>
<tr class="odd">
<td align="left">RF Train down Caret 95</td>
<td align="left">0.179567</td>
<td align="left">0.81627</td>
<td align="left">0.00715226</td>
</tr>
</tbody>
</table>

Con las variables aportadas el modelo no clasifica bien, el número de
Falsos Positivos y Falsos Negativos es muy elevado. En el caso de
seleccionar como clase 1 aquellos que tienen una probabilidad mayor del
95% nos da 2.699.415 de observaciones como clase 1 erroneamente (Falsos
Positivos).

### MODELOS DE REGRESIÓN

Pasos realizados:

-   Modelo sobre fichero Train Completo
-   Modelo sobre dichero Train Agregado (Agregadas las observaciones con
    importe 0)
-   Modelo Equilibrado (Under-Sampling)
-   Cálculo R-Squared del modelo
-   Predicción Claim\_Amount fichero Test
-   Cálculo RSME de las predicciones del fichero Test

##### MODELO DE REGRESIÓN LINEAL

Resultados validados con el fichero Test con 3.295.567 observaciones (El
entrenamiento se ha hecho por triplicado: train entero,train agregado y
train reducido con downsample)

<table>
<thead>
<tr class="header">
<th align="left">Fichero Train</th>
<th align="left">R-squared</th>
<th align="left">RMSE</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">model_train_complet(Sin log)</td>
<td align="left">3.31e-05</td>
<td align="left"><strong>39.34202</strong></td>
</tr>
<tr class="even">
<td align="left">model_train_completo (Con log)</td>
<td align="left">0.0005613</td>
<td align="left">39.36571</td>
</tr>
<tr class="odd">
<td align="left">model_train_SinBalan_Sinlog</td>
<td align="left">0.03828</td>
<td align="left">79.15849</td>
</tr>
<tr class="even">
<td align="left">model_train_SinBalan_log</td>
<td align="left">0.1641</td>
<td align="left">39.34774</td>
</tr>
<tr class="odd">
<td align="left">model_downSample</td>
<td align="left">0.05042</td>
<td align="left">162.3858</td>
</tr>
<tr class="even">
<td align="left">model_downSample_log</td>
<td align="left">0.274</td>
<td align="left">39.38087</td>
</tr>
</tbody>
</table>

Cuando creamos el modelo a partir del fichero train completo vemos que
R-squared o el coeficiente de determinación no llega a explicar ni el 1%
de la variable "Claim\_Amount". En nuestro fichero
"Correlaciones\_Graficos\_Datos.Rmd" se puede observar como las
correlaciones entre las variables independientes y la variable
dependiente son casi nulas.

Nuestro coeficiente de determinación mejora cuando aplicamos la
log-transformación a la variable dependiente. Llegando a obtener un
R-Squared de 27,4% cuando aplicamos una técnica de Under-Sampling para
igualar la proporción de las observaciones con importe 0 y con importe
positivo.

**Siendo el objetivo final la mejor predicción para las observaciones
del fichero test, seleccionaríamos la opción con menor Error Cuadrático
Medio (RMSE), en éste caso nos los ha dado el modelo a partir del train
completo sin transformación logarítmica ni técnicas para redimensionar
el dataset.**

#### MODELOS DE REGRESIÓN NO LINEALES

Todos los modelos de predicción no lineales se han realizado a partir de
una muestra aleatoria de 5000 observaciones del fichero Train Agregado y
Train Down Sample, lo hemos realizado de ésta manera por los tiempos
computacionales y para poder ver de una manera rápida si existe relación
entre el tipo de logarítmo que se aplique y el resultado final en cuanto
a Error Cuadrático Medio.

<table>
<thead>
<tr class="header">
<th align="left">MODELO</th>
<th align="left">LOG S/OUTPUT</th>
<th align="left">EQUILIBRADO</th>
<th align="left">RMSE</th>
<th align="left">R^2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">SVM</td>
<td align="left">NO</td>
<td align="left">NO</td>
<td align="left">40.90</td>
<td align="left">0.028</td>
</tr>
<tr class="even">
<td align="left">SVM</td>
<td align="left"><strong>SI</strong></td>
<td align="left">NO</td>
<td align="left"><strong>39.3599</strong></td>
<td align="left"><strong>0.1694</strong></td>
</tr>
<tr class="odd">
<td align="left">SVM</td>
<td align="left">NO</td>
<td align="left">SI</td>
<td align="left">61.23</td>
<td align="left">0.042</td>
</tr>
<tr class="even">
<td align="left">SVM</td>
<td align="left">SI</td>
<td align="left">SI</td>
<td align="left">39.38</td>
<td align="left">0.2959</td>
</tr>
<tr class="odd">
<td align="left">RPART</td>
<td align="left">NO</td>
<td align="left">NO</td>
<td align="left">112.36</td>
<td align="left">0.013</td>
</tr>
<tr class="even">
<td align="left">RPART</td>
<td align="left"><strong>SI</strong></td>
<td align="left">NO</td>
<td align="left"><strong>39.35003</strong></td>
<td align="left"><strong>0.0831</strong></td>
</tr>
<tr class="odd">
<td align="left">RPART</td>
<td align="left">NO</td>
<td align="left">SI</td>
<td align="left">140.93</td>
<td align="left">0.040</td>
</tr>
<tr class="even">
<td align="left">RPART</td>
<td align="left">SI</td>
<td align="left">SI</td>
<td align="left">39.38</td>
<td align="left">0.1609</td>
</tr>
<tr class="odd">
<td align="left">GBM</td>
<td align="left">NO</td>
<td align="left">NO</td>
<td align="left">48.13</td>
<td align="left">0.030</td>
</tr>
<tr class="even">
<td align="left">GBM</td>
<td align="left"><strong>SI</strong></td>
<td align="left">NO</td>
<td align="left"><strong>39.34993</strong></td>
<td align="left"><strong>0.1794</strong></td>
</tr>
<tr class="odd">
<td align="left">GBM</td>
<td align="left">NO</td>
<td align="left">SI</td>
<td align="left">122.68</td>
<td align="left">0.0555</td>
</tr>
<tr class="even">
<td align="left">GBM</td>
<td align="left">SI</td>
<td align="left">SI</td>
<td align="left">39.35612</td>
<td align="left">0.3732</td>
</tr>
<tr class="odd">
<td align="left">RF</td>
<td align="left">NO</td>
<td align="left">NO</td>
<td align="left">55.47</td>
<td align="left">0.02</td>
</tr>
<tr class="even">
<td align="left">RF</td>
<td align="left"><strong>SI</strong></td>
<td align="left">NO</td>
<td align="left"><strong>39.36</strong></td>
<td align="left"><strong>0.1501</strong></td>
</tr>
<tr class="odd">
<td align="left">RF</td>
<td align="left">NO</td>
<td align="left">SI</td>
<td align="left">130.74</td>
<td align="left">0.0373</td>
</tr>
<tr class="even">
<td align="left">RF</td>
<td align="left">SI</td>
<td align="left">SI</td>
<td align="left">39.38</td>
<td align="left">0.3524</td>
</tr>
</tbody>
</table>

Lo primero que llama la atención es que R-Squared no tiene una relación
directa con RMSE, en nuestro caso vamos a seleccionar el mejor RMSE
puesto que nos aporta más información sobre las desviaciones que hemos
tenido entre lo que hemos predicho y lo real.

**Vemos que los modelos que mejores resultados nos dan no tienen porque
estar equilibrados pero si que nos disminuye el RMSE aplicar una
transformación logarítmica a nuestra variable dependiente.**
