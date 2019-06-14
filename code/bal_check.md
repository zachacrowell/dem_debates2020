First Debate Balance Check
================

``` r
#Config
wd <- "~/Documents/github/"
# Read data in
df <- read.csv(paste0(wd, 'dem_debate2020/data/debate2020.csv'), header = T)

# Create rank
df$rank <- rank(df$standing)

# Check Data
print(df)
```

    ##            name purple standing woman rank
    ## 1         biden      1       37     0 19.0
    ## 2       sanders      1       19     0 18.0
    ## 3        warren      0       11     1 17.0
    ## 4     buttigieg      1        7     0 15.5
    ## 5        harris      1        7     1 15.5
    ## 6       orourke      0        4     0 14.0
    ## 7        booker      0        3     0 13.0
    ## 8     klobuchar      0        2     1 12.0
    ## 9        bennet      1        1     0  7.0
    ## 10       castro      0        1     0  7.0
    ## 11      delaney      0        1     0  7.0
    ## 12      gabbard      0        1     1  7.0
    ## 13   gillibrand      1        1     1  7.0
    ## 14 hickenlooper      1        1     0  7.0
    ## 15      inslsee      0        1     0  7.0
    ## 16         ryan      0        1     0  7.0
    ## 17         yang      1        1     0  7.0
    ## 18    de_blasio      0        0     0  1.5
    ## 19   williamson      1        0     1  1.5

``` r
# Check balance
bal <- glm(purple ~ standing, data = df, family = "binomial")
summary(bal)
```

    ## 
    ## Call:
    ## glm(formula = purple ~ standing, family = "binomial", data = df)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -1.4618  -0.9797  -0.9362   1.2424   1.4395  
    ## 
    ## Coefficients:
    ##             Estimate Std. Error z value Pr(>|z|)
    ## (Intercept) -0.59786    0.58816  -1.016    0.309
    ## standing     0.11322    0.09897   1.144    0.253
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 26.287  on 18  degrees of freedom
    ## Residual deviance: 23.882  on 17  degrees of freedom
    ## AIC: 27.882
    ## 
    ## Number of Fisher Scoring iterations: 5
