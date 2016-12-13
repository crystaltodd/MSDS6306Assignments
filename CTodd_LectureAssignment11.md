# CTodd_LectureAssignment11
Crystal Todd  
December 13, 2016  

## Load Library for Time Series and Data

First, we must load the data and the time series library.


```r
library(tseries)
gwphdata <- get.hist.quote('gwph',quote="Close")
```

```
## time series starts 2013-05-01
```

## Calculate Log Returns

Next, we calculate log returns by the following formula.

```r
gwphret <- log(lag(gwphdata)) - log(gwphdata)
```

## Calculate Volatility Measure

Next, we calculate how much the stock is volatile.

```r
gwphvol <- sd(gwphret) * sqrt(250) * 100
```

## Create Function for Volatility over Length of Series

The following function helps calculate and allows us to plot the volatility over the entire length of the series.

```r
Vol <- function(d, logrets)
{
var = 0
lam = 0
varlist <- c()
for (r in logrets)
{
lam = lam*(1 - 1/d) + 1
    		var = (1 - 1/lam)*var + (1/lam)*r^2
    		varlist <- c(varlist, var)
}
sqrt(varlist)
}
```

## Calculate and Plot Volatility Over Entire Length of Series for Various Three Different Decay Factors

We shall calculate the volatility over different decay factors to see analyze the data.

```r
volest <- Vol(5,gwphret)
volest2 <- Vol(25,gwphret)
volest3 <- Vol(50,gwphret)
plot(volest,type="l")
lines(volest2,type="l",col="purple")
lines(volest3, type = "l", col="pink")
```

![](CTodd_LectureAssignment11_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

From the graph it is easy to see that the greater the decay value put in the formula, the less volatile and more stable the stock is.
