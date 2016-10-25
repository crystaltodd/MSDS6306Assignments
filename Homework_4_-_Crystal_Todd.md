# Homework 4
Crystal Todd  
October 20, 2016  

Write bootstrap code to illustrate the Central Limit Theorem in R Markdown and push the result to GitHub. Use a normal distribution with two different sample sizes and an exponential distribution with two different sample sizes. Correct code alone is insufficient. Please also comment on the code and explain the results. For help, see the lotsa.medians function in Unit 4. The deliverable is a link to a GitHub repo containing the code.

## Normal Distribution with Sample Size 10


```r
n <- 10           ## Sample Size
nsim <- 1000      ## Number of Times to Resample the Normal Distribution
# Setting vector of means of size nsim
sample_10 <- numeric(nsim)
# Bootstrap Loop
for (i in 1:nsim)
{
  # Taking a random sample with n = 10
  x <- rnorm(n)
  # Taking the mean of that random sample
  sample_10[i] <- mean(x)
}
# Analysis on sample_10
summary(sample_10)
```

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
## -1.163000 -0.209400 -0.011900 -0.004458  0.213300  0.973100
```

```r
length(sample_10)
```

```
## [1] 1000
```

```r
mean(sample_10)
```

```
## [1] -0.004457877
```

```r
# HISTOGRAM with sample size 10
hist(sample_10)
```

![](Homework_4_-_Crystal_Todd_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

This histogram of 1000 resampling of data from the Normal Distribution with sample size 10 does appear to follow a Normal Distribution. Hence, this example illustrates the Central Limit Theorem.

## Normal Distribution with Sample Size 100


```r
n <- 100         ## Sample Size
nsim <- 1000     ## Number of Times to Resample the Normal Distribution
# Setting vector of means of size nsim
sample_100 <- numeric(nsim)
# Bootstrap Loop
for (i in 1:nsim)
{
  # Taking a random sample with n = 100
  x <- rnorm(n)
  # Taking the mean of that random sample
  sample_100[i] <- mean(x)
}
# Analysis on sample_100
summary(sample_100)
```

```
##       Min.    1st Qu.     Median       Mean    3rd Qu.       Max. 
## -0.2909000 -0.0647600 -0.0026600 -0.0006158  0.0667200  0.3205000
```

```r
length(sample_100)
```

```
## [1] 1000
```

```r
mean(sample_100)
```

```
## [1] -0.0006158118
```

```r
# HISTOGRAM with sample size 100
hist(sample_100)
```

![](Homework_4_-_Crystal_Todd_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

This histogram of 1000 resampling of data from the Normal Distribution with sample size 100 does appear to follow a Normal Distribution. Hence, this example illustrates the Central Limit Theorem.

## Exponential Distribution with Sample Size 50


```r
n <- 50           ## Sample Size
nsim <- 1000      ## Number of Times to Resample the Exponential Distribution
# Setting vector of means of size nsim
sample_50 <- numeric(nsim)
# Bootstrap Loop
for (i in 1:nsim){
  # Taking a random sample from Exponential Distribution with n = 50
  x <- rexp(n)
  # Taking the mean of that random sample
  sample_50[i] <- mean(x)
}
# Analysis on sample_50
summary(sample_50)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.6376  0.9081  1.0030  1.0050  1.0960  1.4890
```

```r
length(sample_50)
```

```
## [1] 1000
```

```r
mean(sample_50)
```

```
## [1] 1.005419
```

```r
# HISTOGRAM with sample size 50
hist(sample_50)
```

![](Homework_4_-_Crystal_Todd_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

This histogram of 1000 resampling of data from the Exponential Distribution with sample size 50 does appear to follow a Normal Distribution. Hence, this example illustrates the Central Limit Theorem.

## Exponential Distribution with Sample Size 200


```r
n <- 200          ## Sample Size
nsim <- 1000      ## Number of Times to Resample the Exponential Distribution
# Setting vector of means of size nsim
sample_200 <- numeric(nsim)
# Bootstrap Loop
for (i in 1:nsim){
  # Taking a random sample from Exponential Distribution with n = 200
  x <- rexp(n)
  # Taking the mean of that random sample
  sample_200[i] <- mean(x)
}
# Analysis on sample_200
summary(sample_200)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.7734  0.9535  1.0000  1.0010  1.0460  1.2130
```

```r
length(sample_200)
```

```
## [1] 1000
```

```r
mean(sample_200)
```

```
## [1] 1.00125
```

```r
# HISTOGRAM with sample size 200
hist(sample_200)
```

![](Homework_4_-_Crystal_Todd_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

This histogram of 1000 resampling of data from the Exponential Distribution with sample size 200 does appear to follow a Normal Distribution. Hence, this example illustrates the Central Limit Theorem.
