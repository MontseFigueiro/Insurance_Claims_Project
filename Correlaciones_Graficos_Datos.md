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

Plot:

    jpeg("Correlaccion_variables.jpeg",width = 900, height = 800,quality = 1000)
    M <- cor(train_cor)
    corrplot.mixed(M)
    dev.off()

    ## png 
    ##   2

[](D:\master\data\Montse\carinsurance\Graficos\Correlaccion_variables.jpeg)

Los colores oscuros representan mayor correlación, como podemos
comprobar

### Correlaciones Individuales

### Variables - Características del vehículo

La correlacción entre Claim\_Amount y Model\_year7

    cor( train$Model_Year,train$Claim_Amount)

    ## [1] 0.02749687

    jpeg("Correlaccion_ModelYear.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Model_Year,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y OrdCat

    cor(train$OrdCat,train$Claim_Amount)

    ## [1] -0.005075587

    jpeg("Correlaccion_OrdCat.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$OrdCat,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var1

    cor(train$Var1,train$Claim_Amount)

    ## [1] -0.003562823

    jpeg("Correlaccion_Var1.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var1,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var2

    cor(train$Var2,train$Claim_Amount)

    ## [1] 0.001345127

    jpeg("Correlaccion_Var2.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var2,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var3

    cor(train$Var3,train$Claim_Amount)

    ## [1] 0.001458461

    jpeg("Correlaccion_Var3.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var3,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var4

    cor(train$Var4,train$Claim_Amount)

    ## [1] 0.001318163

    jpeg("Correlaccion_Var4.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var4,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var5

    cor(train$Var5,train$Claim_Amount)

    ## [1] 0.004564181

    jpeg("Correlaccion_Var5.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var5,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var6

    cor(train$Var6,train$Claim_Amount)

    ## [1] -0.001585308

    jpeg("Correlaccion_Var6.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var6,train$Claim_Amount)
    dev.off

    ## function (which = dev.cur()) 
    ## {
    ##     if (which == 1) 
    ##         stop("cannot shut down device 1 (the null device)")
    ##     .External(C_devoff, as.integer(which))
    ##     dev.cur()
    ## }
    ## <bytecode: 0x0000000008b36d18>
    ## <environment: namespace:grDevices>

La correlacción entre Claim\_Amount y Var7

    cor(train$Var7,train$Claim_Amount)

    ## [1] -0.002641458

    jpeg("Correlaccion_Var7.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var7,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var8

    cor(train$Var8,train$Claim_Amount)

    ## [1] 0.0005885435

    jpeg("Correlaccion_Var8.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$Var8,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

### Variables - Características de la póliza

La correlacción entre Claim\_Amount y NVVar1

    cor(train$NVVar1,train$Claim_Amount)

    ## [1] -0.0436794

    jpeg("Correlaccion_NVVAR1.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$NVVar1,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar2

    cor(train$NVVar2,train$Claim_Amount)

    ## [1] -0.04536111

    jpeg("Correlaccion_NVVAR2.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$NVVar2,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar3

    cor(train$NVVar3,train$Claim_Amount)

    ## [1] -0.04356654

    jpeg("Correlaccion_NVVAR3.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$NVVar3,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar4

    cor(train$NVVar4,train$Claim_Amount)

    ## [1] -0.03900727

    jpeg("Correlaccion_NVVAR4.jpeg",width = 800, height = 800,quality = 1000)
    plot(train$NVVar4,train$Claim_Amount)
    dev.off()

    ## png 
    ##   2
