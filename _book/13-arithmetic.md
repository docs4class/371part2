# Objects and Arithmetic

## Introduction

R stores information and operates on objects. The simplest objects are scalars, vectors and matrices.
But there are many others: lists and dataframes for example. In advanced use of R it can also be
useful to define new types of object, specific for particular application. We will stick with just the
most commonly used objects here.
An important feature of R is that it will do different things on different types of objects. For
example, type:


```r
4+6
#> [1] 10
```


So, R does scalar arithmetic returning the scalar value 10. (In actual fact, R returns a vector of
length 1 - hence the [1] denoting first element of the vector.
We can assign objects values for subsequent use. For example:


```r
x<-6
y<-4
z<-x+y
```

would do the same calculation as above, storing the result in an object called z. We can look at
the contents of the object by simply typing its name:


```r
z
#> [1] 10
```

Storing things such as calculations as objects is extremely useful, especially in longer scripts. Mainly because you will likely call the same equation multiple times and if you need to revise it in any way you only need to change the initial assignment rather than every line. 

## Basic Functions

At any time we can list the objects which we have created:


```r
ls()
#> [1] "x" "y" "z"
```


Notice that ls is actually an object itself. Typing ls would result in a display of the contents of
this object, in this case, the commands of the function. The use of parentheses, ls(), ensures that
the function is executed and its result - in this case, a list of the objects in the directory - displayed.
More commonly a function will operate on an object, for example:


```r
sqrt(16)
#> [1] 4
```

calculates the square root of 16. Objects can be removed from the current workspace with the rm
function:


```r
rm(x,y)
```

for example.


There are many standard functions available in R, and it is also possible to create new ones.
Vectors can be created in R in a number of ways. We can describe all of the elements:

```r
z<-c(5,9,1,0)
```


Note the use of the function c to concatenate or glue together individual elements. This function
can be used much more widely, for example


```r
x<-c(5,9)
y<-c(1,0)
z<-c(x,y)
```


would lead to the same result by gluing together two vectors to create a single vector.


Sequences can be generated as follows:


```r
x<-1:10
```

while more general sequences can be generated using the seq command. For example:


```r
seq(1,9,by=2)
#> [1] 1 3 5 7 9
seq(8,20,length=6)
#> [1]  8.0 10.4 12.8 15.2 17.6 20.0
```


These examples illustrate that many functions in R have optional arguments, in this case, either the step length or the total length of the sequence (it doesn't make sense to use both). If you leave out both of these options, R will make its own default choice, in this case assuming a step length
of 1. So, for example,


```r
seq(8,20,length=6)
#> [1]  8.0 10.4 12.8 15.2 17.6 20.0
x<-seq(1,10)
x
#>  [1]  1  2  3  4  5  6  7  8  9 10
```

also generates a vector of integers from 1 to 10.


At this point it's worth mentioning the help facility. If you don't know how to use a function,
or don't know what the options or default values are, type help(functionname) where functionname is the name of the function you are interested in. This will usually help and will often include examples to make things even clearer.


Another useful function for building vectors is the rep command for repeating things. For
example:


```r
rep(0,100)
#>   [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
#>  [28] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
#>  [55] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
#>  [82] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
rep(1:3,6)
#>  [1] 1 2 3 1 2 3 1 2 3 1 2 3 1 2 3 1 2 3
rep(1:3,c(6,6,6))
#>  [1] 1 1 1 1 1 1 2 2 2 2 2 2 3 3 3 3 3 3
```

which we could also simplify cleverly as:


```r
rep(1:3,rep(6,3))
#>  [1] 1 1 1 1 1 1 2 2 2 2 2 2 3 3 3 3 3 3
```


As explained above, R will often adapt to the objects it is asked to work on. For example:


```r
x<-c(6,8,9)
y<-c(1,2,4)
x+y
#> [1]  7 10 13
```

and


```r
x*y
#> [1]  6 16 36
```

showing that R uses componentwise arithmetic on vectors. R will also try to make sense if objects
are mixed. For example:


```r
x<-c(6,8,9)
x+2
#> [1]  8 10 11
```

though care should be taken to make sure that R is doing what you would like it to in these circumstances.

Two particularly useful functions worth remembering are length which returns the length of a vector (i.e. the number of elements it contains) and sum which calculates the sum of the elements of a vector.


## Statistics and Summaries

One of the most useful functions of R is its ability to perform statistical analysis on large pieces of data. Later in this book we will cover how this analysis can be used to build complex models and test their accuracy. For now, the focus will be on how to perform basic statistical analysis and the definitions of the more basic terms.

### Statistical Analysis

You've undoubtedly have heard the terms mean, median, standard deviation and variance. However, if asked to define these terms and provide examples of their usefulness, what would you say? This section is going to answer the first part of that question. 

Mean is a pretty straight forward concept for most. Commonly referred to as the "average", you find this number by adding all the numbers in your data set together and then divide by the total number of points you used. This is easily done on a calculator if you are working with less then 20 digits, however this is almost never the case in data science. Often, especially with R, you will be dealing with data sets with hundreds, thousands, or maybe even hundreds of thousands of data points. Fortunately, R takes the pain away from this process and offers a very simple function that will do this for you. Start by creating an object that contains a list of numbers, and then simply use the mean function to calculate the average of your variable. 


```r
a <- c(3.8,4,3.1,2.1,12.6,17,8.43,11,2,3,9,5,3,0.5)

mean(a)
#> [1] 6.037857
```

The median of a data set is data point that fall in the middle of all the other points when they are ordered from lowest to highest. Again, something easily found even without a calculator if you have small data sets, however humans can miscount and some data sets are just too massive for us to do on our own. R never makes these counting mistakes and by using a simple function you save yourself hours of mundane counting. Start the same way you found mean by creating an object with various numbers and then simply use the `median` function. 


```r
b <- c(3.8,4,3.1,2.1,12.6,17,8.43,11,2,3,9,5,3,0.5)

median(b)
#> [1] 3.9
```

Many people have heard of standard deviation, but not many can provide an accurate definition. Standard deviation is the measure of variance (see next paragraph) between numbers in a data set and that data set's mean. Typically a lower standard deviation is what you want to see as this proves there is little variance in your data set and that typically means a higher correlation. If you wanted to find this by hand you would have to find the square root of the variance between each point and the mean. This is easy if you have all the numbers you need, but that is almost never the case and thus you would have to calculate all that variance by hand and that is too much work. Why take all those extra steps when R can do it for you? The `sd()` function does all the work without any hassle, all you have to do is identify the object you want it to find the standard deviation of. 


```r
d <- c(3.8,4,3.1,2.1,12.6,17,8.43,11,2,3,9,5,3,0.5)

sd(d)
#> [1] 4.821066
```

Finally, we can cover variance. Variance is the measure of distance between two numbers. This statistic is often used to measure how spread out your data is and can be used to determine your model's accuracy. Typically, a higher variance means your model is inaccurate. So, when building models and reviewing your summary statistics, you want your variance to be as low as possible. There is a var() function that will find the variance of a variable for you, however typically you will create a confusion matrix (discussed in a later section) that will help you determine the variance, and thus accuracy of your model. 

### Anscombe's Quartet

You may be asking now, why bother visualizing data if I have all these numbers that will tell me what I need to know about my data? You are correct in saying that statistical data is very useful, and in many cases essential, however visualization is equally as important. Anscombe's Quartet is a statistical phenomenon where four sets of data have very similar statistical properties, but very are completely different when graphed. Let's take a look at the data:


```
#>    x1 x2 x3 x4    y1   y2    y3    y4
#> 1  10 10 10  8  8.04 9.14  7.46  6.58
#> 2   8  8  8  8  6.95 8.14  6.77  5.76
#> 3  13 13 13  8  7.58 8.74 12.74  7.71
#> 4   9  9  9  8  8.81 8.77  7.11  8.84
#> 5  11 11 11  8  8.33 9.26  7.81  8.47
#> 6  14 14 14  8  9.96 8.10  8.84  7.04
#> 7   6  6  6  8  7.24 6.13  6.08  5.25
#> 8   4  4  4 19  4.26 3.10  5.39 12.50
#> 9  12 12 12  8 10.84 9.13  8.15  5.56
#> 10  7  7  7  8  4.82 7.26  6.42  7.91
#> 11  5  5  5  8  5.68 4.74  5.73  6.89
```


```
#>                    x1        x2        x3        x4
#> nobs        11.000000 11.000000 11.000000 11.000000
#> NAs          0.000000  0.000000  0.000000  0.000000
#> Minimum      4.000000  4.000000  4.000000  8.000000
#> Maximum     14.000000 14.000000 14.000000 19.000000
#> 1. Quartile  6.500000  6.500000  6.500000  8.000000
#> 3. Quartile 11.500000 11.500000 11.500000  8.000000
#> Mean         9.000000  9.000000  9.000000  9.000000
#> Median       9.000000  9.000000  9.000000  8.000000
#> Sum         99.000000 99.000000 99.000000 99.000000
#> SE Mean      1.000000  1.000000  1.000000  1.000000
#> LCL Mean     6.771861  6.771861  6.771861  6.771861
#> UCL Mean    11.228139 11.228139 11.228139 11.228139
#> Variance    11.000000 11.000000 11.000000 11.000000
#> Stdev        3.316625  3.316625  3.316625  3.316625
#> Skewness     0.000000  0.000000  0.000000  2.466911
#> Kurtosis    -1.528926 -1.528926 -1.528926  4.520661
#>                    y1        y2        y3        y4
#> nobs        11.000000 11.000000 11.000000 11.000000
#> NAs          0.000000  0.000000  0.000000  0.000000
#> Minimum      4.260000  3.100000  5.390000  5.250000
#> Maximum     10.840000  9.260000 12.740000 12.500000
#> 1. Quartile  6.315000  6.695000  6.250000  6.170000
#> 3. Quartile  8.570000  8.950000  7.980000  8.190000
#> Mean         7.500909  7.500909  7.500000  7.500909
#> Median       7.580000  8.140000  7.110000  7.040000
#> Sum         82.510000 82.510000 82.500000 82.510000
#> SE Mean      0.612541  0.612568  0.612196  0.612242
#> LCL Mean     6.136083  6.136024  6.135943  6.136748
#> UCL Mean     8.865735  8.865795  8.864057  8.865070
#> Variance     4.127269  4.127629  4.122620  4.123249
#> Stdev        2.031568  2.031657  2.030424  2.030579
#> Skewness    -0.048374 -0.978693  1.380120  1.120774
#> Kurtosis    -1.199123 -0.514319  1.240044  0.628751
```

As you can see from the table, the summary statistics for the four tables look very similar, however let's graph these and see what kind of visualizations we get.



![](13-arithmetic_files/figure-epub3/unnamed-chunk-23-1.png)<!-- -->

Pretty rad right? So yes, statistical data is vital, however it should not be the only thing you look at, sometimes a visualization can help you understand the data more! Later in this book, and in the upper level data analytics courses, we will cover visualizations more and how they can be useful.


## Exercises

1. Define

```r
x<-c(4,2,6)
y<-c(1,0,-1)
```


2. Decide what the result will be of the following:
    + length(x)
    + sum(x)
    + sum(x^2)
    + x+y
    + x*y
    + x-2
    + x^2
3. Use R to check your answers.
4. Decide what the following sequences are and use R to check your answers:
    + 7:11
    + seq(2,9)
    + seq(4,10,by=2)
    + seq(3,30,length=10)
    + seq(6,-4,by=-2)
5. Determine what the result will be of the following R expressions, and then use R to check if	you are right:
    + rep(2,4)
    + rep(c(1,2),4)
    + rep(c(1,2),c(4,4))
    + rep(1:4,4)
    + rep(1:4,rep(3,4))
6. Use the rep function to define simply the following vectors in R.
    + 6,6,6,6,6,6
    + 5,8,5,8,5,8,5,8
    + 5,5,5,5,8,8,8,8
