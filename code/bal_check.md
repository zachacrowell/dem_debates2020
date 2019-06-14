First Debate Balance Check
================

``` r
#Config
wd <- "~/Documents/github/"
# Read data in
df <- read.csv(paste0(wd, 'dem_debate2020/data/debate2020.csv'), header = T)

# Create rank
df$rank <- rev(rank(df$standing))

# Check Data
print(df)
```

    ##            name purple standing woman rank
    ## 1         biden      1       37     0  6.5
    ## 2       sanders      1       19     0  1.0
    ## 3        warren      0       11     1  6.5
    ## 4     buttigieg      1        7     0  6.5
    ## 5        harris      1        7     1  6.5
    ## 6       orourke      0        4     0  6.5
    ## 7        booker      0        3     0  6.5
    ## 8     klobuchar      0        2     1  6.5
    ## 9        bennet      1        1     0  6.5
    ## 10       castro      0        1     0  6.5
    ## 11      delaney      0        1     0  6.5
    ## 12      gabbard      0        1     1 12.0
    ## 13   gillibrand      1        1     1 13.0
    ## 14 hickenlooper      1        1     0 14.0
    ## 15      inslsee      0        1     0 15.5
    ## 16         ryan      0        1     0 15.5
    ## 17         yang      1        1     0 17.0
    ## 18    de_blasio      0        0     0 18.0
    ## 19   williamson      1        1     1 19.0

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
    ## -1.4843  -0.9706  -0.9246   1.2434   1.3994  
    ## 
    ## Coefficients:
    ##             Estimate Std. Error z value Pr(>|z|)
    ## (Intercept)  -0.6286     0.5979  -1.051    0.293
    ## standing      0.1206     0.1043   1.156    0.248
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 26.287  on 18  degrees of freedom
    ## Residual deviance: 23.733  on 17  degrees of freedom
    ## AIC: 27.733
    ## 
    ## Number of Fisher Scoring iterations: 5
