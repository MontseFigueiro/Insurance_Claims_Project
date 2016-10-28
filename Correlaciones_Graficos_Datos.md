CORRELACIÓN ENTRE VARIABLES CONTINUAS
-------------------------------------

En éste documento vamos a poder visualizar la relación entre la variable
dependiente "Claim\_Amount" y las diferentes variables continuas.

### Carga del fichero

    train <- read.csv("traindf.csv")

### Correlación entre todas las variables

Selección de variables continuas:

    library(corrplot)

    ## Warning: package 'corrplot' was built under R version 3.3.1

    cols <- c("Model_Year","OrdCat","Var1","Var2","Var3","Var4","Var5","Var6","Var7","Var8","NVVar1","NVVar2","NVVar3","NVVar4")
    train_cor <- train[,cols]

Plot Correlación entre variables:

    M <- cor(train_cor)
    corrplot.mixed(M)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-3-1.png)

Los colores oscuros representan mayor correlación, como podemos
comprobar hay variables numéricas altamente correlacionadas entre ellas.

### Correlaciones Individuales

### Variables - Características del vehículo

La correlacción entre Claim\_Amount y Model\_year7

    cor( train$Model_Year,train$Claim_Amount)

    ## [1] 0.02749687

    plot(train$Model_Year,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-4-1.png)
La correlacción entre Claim\_Amount y OrdCat

    cor(train$OrdCat,train$Claim_Amount)

    ## [1] -0.005075587

    plot(train$OrdCat,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-5-1.png)

La correlacción entre Claim\_Amount y Var1

    cor(train$Var1,train$Claim_Amount)

    ## [1] -0.003562823

    plot(train$Var1,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-6-1.png)
La correlacción entre Claim\_Amount y Var2

    cor(train$Var2,train$Claim_Amount)

    ## [1] 0.001345127

    plot(train$Var2,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-7-1.png)
La correlacción entre Claim\_Amount y Var3

    cor(train$Var3,train$Claim_Amount)

    ## [1] 0.001458461

    plot(train$Var3,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-8-1.png)
La correlacción entre Claim\_Amount y Var4

    cor(train$Var4,train$Claim_Amount)

    ## [1] 0.001318163

    plot(train$Var4,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-9-1.png)
La correlacción entre Claim\_Amount y Var5

    cor(train$Var5,train$Claim_Amount)

    ## [1] 0.004564181

    plot(train$Var5,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-10-1.png)
La correlacción entre Claim\_Amount y Var6

    cor(train$Var6,train$Claim_Amount)

    ## [1] -0.001585308

    plot(train$Var6,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-11-1.png)
La correlacción entre Claim\_Amount y Var7

    cor(train$Var7,train$Claim_Amount)

    ## [1] -0.002641458

    plot(train$Var7,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-12-1.png)
La correlacción entre Claim\_Amount y Var8

    cor(train$Var8,train$Claim_Amount)

    ## [1] 0.0005885435

    plot(train$Var8,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-13-1.png)

### Variables - Características de la póliza

La correlacción entre Claim\_Amount y NVVar1

    cor(train$NVVar1,train$Claim_Amount)

    ## [1] -0.0436794

    plot(train$NVVar1,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-14-1.png)
La correlacción entre Claim\_Amount y NVVar2

    cor(train$NVVar2,train$Claim_Amount)

    ## [1] -0.04536111

    plot(train$NVVar2,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-15-1.png)
La correlacción entre Claim\_Amount y NVVar3

    cor(train$NVVar3,train$Claim_Amount)

    ## [1] -0.04356654

    plot(train$NVVar3,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-16-1.png)
La correlacción entre Claim\_Amount y NVVar4

    cor(train$NVVar4,train$Claim_Amount)

    ## [1] -0.03900727

    plot(train$NVVar4,train$Claim_Amount)

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-17-1.png)

Distribución de la Variable Dependiente
---------------------------------------

Observaciones con importe diferente de 0:

    positive <- train[train$Claim_Amount!=0,]
    hist(positive$Claim_Amount,main="Histograma Claim Amount")

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-18-1.png)

Aplicando Transformación logarítmica:

    hist(log(positive$Claim_Amount+1),main="Histograma Log Claim Amount")

![](Correlaciones_Graficos_Datos_files/figure-markdown_strict/unnamed-chunk-19-1.png)

Los resultados que hemos obtenido en nuestros modelos se han ajustado
mejor cuando hemos aplicado el logaritmo sobre la variable dependiente.
