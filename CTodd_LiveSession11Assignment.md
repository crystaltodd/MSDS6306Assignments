# CTodd_LiveSession11Assignment
Crystal Todd  
November 21, 2016  

## Plot the Time Series. Can you Identify Seasonal Fluctuations and/or a Trend?




```r
data(ukcars)
plot(ukcars)
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

From the above plot, there is a decrease in by about 200,000 cars produced in the UK from 1977 to 1980. Then, there was a steady increase to almost 500,000 cars produced in 2000 with a dramatic drop of nearly 150,000 thousand cars in the same year. The number of cars produced in the UK has remained relatively steady around 400,000. Also, there is a seasonal trend within each year that the third quarter historically has less cars produced than the rest of the year.

## Classical Decomposition to Calculate the Trend-Cycle and Seasonal Indices


```r
fitd <- decompose(ukcars)
plot(fitd)
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

## Do the Results Support the Graphical Interpretation from Part A?

From the above "Trend" plot, we can see that the trend described in the first part is shown in the graphical interpretation in Part B.

## Compute and Plot the Seasonally Adjusted Data


```r
ukadj <- seasadj(fitd)
plot(ukadj, main = "Seasonally Adjusted UK Passenger Vehicle Production",
     ylab = "Thousands of Cars", xlab = "Year")
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

## Change One Observation to be an Outlier and Recompute the Seasonally Adjusted Data. What is the effect of the outlier?


```r
ukcars2 <- ts(c(ukcars[1:54],ukcars[55]+200,ukcars[56:length(ukcars)]),start=c(min(time(ukcars)),1),frequency=4)
plot(ukcars2)
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

```r
fitd2 <- decompose(ukcars2)
ukadj2 <- seasadj(fitd2)
plot(ukadj2, main = "Seasonally Adjusted UK Passenger Vehicle Production with Middle Outlier",
     ylab = "Thousands of Cars", xlab = "Year")
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-4-2.png)<!-- -->

The outlier at 1990 for the third quarter drastically changed the seasonally adjusted data and made this point which is not the maximum into a maximum for this new adjusted data set. This means that the outlier is even more of an outlier to the third quarter in a year than if the outlier had been in a different quarter of the year.

## Does it Make any Difference if the Outlier is Near the End Rather Than in the Middle of the Time Series?


```r
ukcars3 <- ts(c(ukcars[1:90],ukcars[91]+200,ukcars[92:length(ukcars)]),start=c(min(time(ukcars)),1),frequency=4)
plot(ukcars3)
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

```r
fitd3 <- decompose(ukcars3)
ukadj3 <- seasadj(fitd3)
plot(ukadj3, main = "Seasonally Adjusted UK Passenger Vehicle Production with End Outlier",
     ylab = "Thousands of Cars", xlab = "Year")
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-5-2.png)<!-- -->

It only made a difference to each outlier, but the rest of the data set was not observed to be affected by the outlier. Thus, the outlier didn't matter whether it was near the end or in the middle of the time series.

## Use STL to Decompose the Series


```r
fit <- stl(ukcars, s.window=5)
plot(fit)
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

```r
plot(ukcars, col="blue",
     main = "UK Passenger Vehicle Production",
     ylab = "Thousands of Cars", xlab = "Year")
lines(fit$time.series[,2],col="red",ylab="Trend")
```

![](CTodd_LiveSession11Assignment_files/figure-html/unnamed-chunk-6-2.png)<!-- -->
