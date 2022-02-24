# Summaries and Subscripting

## Introduction

Let's suppose we've collected some data from an experiment and stored them in an object x:


```r
x<-c(7.5,8.2,3.1,5.6,8.2,9.3,6.5,7.0,9.3,1.2,14.5,6.2)
```

Some simple summary statistics of these data can be produced:

```r
mean(x)
#> [1] 7.216667
var(x)
#> [1] 11.00879
sd(x)
#> [1] 3.317949
summary(x)
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>   1.200   6.050   7.250   7.217   8.475  14.500
```

which should all be self explanatory. 

It may be, however, that we subsequently learn that the first 6 data points correspond to measurements made on one machine, and the second six on another machine.

This might lead us to want to summarize the two sets of data separately, so we would need to extract from
x the two relevant subvectors. This is achieved by subscripting:


```r
x[1:6]
#> [1] 7.5 8.2 3.1 5.6 8.2 9.3
x[7:12]
#> [1]  6.5  7.0  9.3  1.2 14.5  6.2
summary(x[1:6])
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>   3.100   6.075   7.850   6.983   8.200   9.300
summary(x[7:12])
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>   1.200   6.275   6.750   7.450   8.725  14.500
```

Other subsets can be created in the obvious way. For example:

```r
x[c(2,4,9)]
#> [1] 8.2 5.6 9.3
```

Negative integers can be used to exclude particular elements. For example

```r
x[-(1:6)]
#> [1]  6.5  7.0  9.3  1.2 14.5  6.2
```

has the same effect as 

```r
x[7:12]
#> [1]  6.5  7.0  9.3  1.2 14.5  6.2
```

## Exercises (Summaries and Subscripting)
1. If x<- c(5,9,2,3,4,6,7,0,8,12,2,9) decide what each of the following is and use R to
check your answers:
(a) x[2]
(b) x[2:4]
(c) x[c(2,3,6)]
(d) x[c(1:5,10:12)]
(e) x[-(10:12)]
2. The data y<-c(33,44,29,16,25,45,33,19,54,22,21,49,11,24,56) contain sales of milk
in gallons for 5 days in three different shops (the frst 3 values are for shops 1,2 and 3 on
Monday, etc.) Produce a statistical summary of the sales for each day of the week and also
for each shop.
