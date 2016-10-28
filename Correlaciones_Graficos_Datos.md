Carga del fichero
=================

    train <- read.csv("traindf.csv")

Visualizamos las caracteristicas del fichero
============================================

    head(train)

    ##   Blind_Submodel Model_Year Cat1 Cat2 Cat3 Cat4 Cat5 Cat6 Cat7 Cat8 Cat9
    ## 1          A.2.0       1990    E    B    D    A    A    C    A    A    B
    ## 2          A.2.0       1990    E    B    D    A    A    C    A    A    B
    ## 3          A.2.0       1990    E    B    D    A    A    C    A    A    B
    ## 4          A.2.0       1990    E    B    D    A    A    C    A    A    B
    ## 5          A.2.0       1990    E    B    D    A    A    C    A    A    B
    ## 6          A.2.0       1991    E    B    D    A    A    C    A    A    B
    ##   OrdCat       Var1      Var2     Var3      Var4       Var5     Var6
    ## 1      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ## 2      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ## 3      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ## 4      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ## 5      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ## 6      2 -0.5534074 -1.334886 -1.05481 -1.374998 -0.9536453 -1.11337
    ##       Var7       Var8 NVCat     NVVar1     NVVar2     NVVar3     NVVar4
    ## 1 -0.82476 -0.6413755     E -0.2315299 -0.2661168 -0.2723372 -0.2514189
    ## 2 -0.82476 -0.6413755     M -0.2315299 -0.2661168 -0.2723372 -0.2514189
    ## 3 -0.82476 -0.6413755     N -0.2315299  2.7836161 -0.2723372 -0.2514189
    ## 4 -0.82476 -0.6413755     J -0.2315299  4.3084822 -0.2723372 -0.2514189
    ## 5 -0.82476 -0.6413755     O -0.2315299 -0.2661168 -0.2723372 -0.2514189
    ## 6 -0.82476 -0.3345262     O -0.2315299 -0.2661168 -0.2723372 -0.2514189
    ##   Claim_Amount
    ## 1            0
    ## 2            0
    ## 3            0
    ## 4            0
    ## 5            0
    ## 6            0

    str(train)

    ## 'data.frame':    689754 obs. of  26 variables:
    ##  $ Blind_Submodel: Factor w/ 2721 levels "A.2.0","A.3.0",..: 1 1 1 1 1 1 2 3 4 4 ...
    ##  $ Model_Year    : int  1990 1990 1990 1990 1990 1991 1981 1981 1981 1981 ...
    ##  $ Cat1          : Factor w/ 10 levels "A","B","C","D",..: 5 5 5 5 5 5 5 1 1 1 ...
    ##  $ Cat2          : Factor w/ 3 levels "A","B","C": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ Cat3          : Factor w/ 6 levels "A","B","C","D",..: 4 4 4 4 4 4 3 3 3 3 ...
    ##  $ Cat4          : Factor w/ 3 levels "A","B","C": 1 1 1 1 1 1 1 3 3 3 ...
    ##  $ Cat5          : Factor w/ 3 levels "A","B","C": 1 1 1 1 1 1 1 2 2 2 ...
    ##  $ Cat6          : Factor w/ 5 levels "B","C","D","E",..: 2 2 2 2 2 2 1 2 2 2 ...
    ##  $ Cat7          : Factor w/ 4 levels "A","B","C","D": 1 1 1 1 1 1 1 2 2 2 ...
    ##  $ Cat8          : Factor w/ 3 levels "A","B","C": 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ Cat9          : Factor w/ 2 levels "A","B": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ OrdCat        : int  2 2 2 2 2 2 2 2 2 2 ...
    ##  $ Var1          : num  -0.553 -0.553 -0.553 -0.553 -0.553 ...
    ##  $ Var2          : num  -1.33 -1.33 -1.33 -1.33 -1.33 ...
    ##  $ Var3          : num  -1.05 -1.05 -1.05 -1.05 -1.05 ...
    ##  $ Var4          : num  -1.37 -1.37 -1.37 -1.37 -1.37 ...
    ##  $ Var5          : num  -0.954 -0.954 -0.954 -0.954 -0.954 ...
    ##  $ Var6          : num  -1.11 -1.11 -1.11 -1.11 -1.11 ...
    ##  $ Var7          : num  -0.825 -0.825 -0.825 -0.825 -0.825 ...
    ##  $ Var8          : num  -0.641 -0.641 -0.641 -0.641 -0.641 ...
    ##  $ NVCat         : Factor w/ 15 levels "A","B","C","D",..: 5 13 14 10 15 15 5 13 15 13 ...
    ##  $ NVVar1        : num  -0.232 -0.232 -0.232 -0.232 -0.232 ...
    ##  $ NVVar2        : num  -0.266 -0.266 2.784 4.308 -0.266 ...
    ##  $ NVVar3        : num  -0.272 -0.272 -0.272 -0.272 -0.272 ...
    ##  $ NVVar4        : num  -0.251 -0.251 -0.251 -0.251 -0.251 ...
    ##  $ Claim_Amount  : num  0 0 0 0 0 0 0 0 0 0 ...

La correlacción entre Claim\_Amount y Model\_year es de 0.02749687

    cor(train$Claim_Amount, train$Model_Year)

    ## [1] 0.02749687

    jpeg("Correlaccion_ModelYear.jpeg")
    plot(train$Claim_Amount, train$Model_Year)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y OrdCat es de -0.005075587

    cor(train$Claim_Amount, train$OrdCat)

    ## [1] -0.005075587

    jpeg("Correlaccion_OrdCat.jpeg")
    plot(train$Claim_Amount, train$OrdCat)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var1 es de -0.003562823

    cor(train$Claim_Amount, train$Var1)

    ## [1] -0.003562823

    jpeg("Correlaccion_Var1.jpeg")
    plot(train$Claim_Amount, train$Var1)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var2 es de 0.001345127

    cor(train$Claim_Amount, train$Var2)

    ## [1] 0.001345127

    jpeg("Correlaccion_Var2.jpeg")
    plot(train$Claim_Amount, train$Var2)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var3 es de 0.001458461

    cor(train$Claim_Amount, train$Var3)

    ## [1] 0.001458461

    jpeg("Correlaccion_Var3.jpeg")
    plot(train$Claim_Amount, train$Var3)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var4 es de 0.001318163

    cor(train$Claim_Amount, train$Var4)

    ## [1] 0.001318163

    jpeg("Correlaccion_Var4.jpeg")
    plot(train$Claim_Amount, train$Var4)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var5 es de 0.004564181

    cor(train$Claim_Amount, train$Var5)

    ## [1] 0.004564181

    jpeg("Correlaccion_Var5.jpeg")
    plot(train$Claim_Amount, train$Var5)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var6 es de -0.001585308

    cor(train$Claim_Amount, train$Var6)

    ## [1] -0.001585308

    jpeg("Correlaccion_Var6.jpeg")
    plot(train$Claim_Amount, train$Var6)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var7 es de -0.002641458

    cor(train$Claim_Amount, train$Var7)

    ## [1] -0.002641458

    jpeg("Correlaccion_Var7.jpeg")
    plot(train$Claim_Amount, train$Var7)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y Var8 es de 0.0005885435

    cor(train$Claim_Amount, train$Var8)

    ## [1] 0.0005885435

    jpeg("Correlaccion_Var8.jpeg")
    plot(train$Claim_Amount, train$Var8)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar1 es de -0.0436794

    cor(train$Claim_Amount, train$NVVar1)

    ## [1] -0.0436794

    jpeg("Correlaccion_NVVAR1.jpeg")
    plot(train$Claim_Amount, train$NVVar1)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar2 es de -0.04536111

    cor(train$Claim_Amount, train$NVVar2)

    ## [1] -0.04536111

    jpeg("Correlaccion_NVVAR2.jpeg")
    plot(train$Claim_Amount, train$NVVar2)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar3 es de -0.04356654

    cor(train$Claim_Amount, train$NVVar3)

    ## [1] -0.04356654

    jpeg("Correlaccion_NVVAR3.jpeg")
    plot(train$Claim_Amount, train$NVVar3)
    dev.off()

    ## png 
    ##   2

La correlacción entre Claim\_Amount y NVVar4 es de -0.03900727

    cor(train$Claim_Amount, train$NVVar4)

    ## [1] -0.03900727

    jpeg("Correlaccion_NVVAR4.jpeg")
    plot(train$Claim_Amount, train$NVVar4)
    dev.off()

    ## png 
    ##   2
