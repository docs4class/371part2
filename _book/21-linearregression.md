#Machine Learning?

> Have we talked about the Target Pregnancy Story yet?

::: {.rmdimportant}

**How Target Figured Out A Teen Girl Was Pregnant Before Her Father Did**

:::


This is where the fun stuff begins! What we have learned up to this point has barely scratched the surface of what R is capable of. In the world of data science, R is used for three primary purposes, those purposes are **(1) data transformation, (2) data wrangling, (3) machine learning**. The other two purposes have been covered in earlier chapters of this book. The reason we covered the other topics first is that that lay the foundation. In the real world, it is likely you will never be given a clean data set, and you will have to do some wrangling and transformation before anything else is possible. After all, in the experience of many data science students, cleaning the data is the most tedious and time consuming process of a project. 

Enough of the old stuff, what is machine learning? According to the Merriam-Webster Dictionary, machine learning is "the process by which a computer is able to improve its own performance by continuously incorporating new data into an existing statistical model." Let's take a trip back to the Target story discussed in the introductory chapter. The data scientist, or more likely data scientists (collaborative work is essential in this field), that worked on that model were likely experts in machine learning. They were able to train the computer to look through thousands (probably more) of customers' data and the computer, based off the algorithms written by these "data nerds," was able to predict whether a customer was pregnant! Think of other possible applications of this technology? We could predict how well a student will preform on an exam, the risk of someone suffering from a heart attack, or the likelihood that someone will default on a loan. Every field in existence today could find a way to implement machine learning to optimize their business.

There are two branches of machine learning, supervised and unsupervised. Both have their own unique uses, however in this course we will focus on supervised machine learning. Supervised machine learning required us to provide a clean data set with clearly defined variables and instructions. Essentially, we give the computer the information it needs and provide it with specific instructions detailing what we would like to see happen, and it does the rest. Linear regression is typically the first method of supervised learning people are introduced to, and it will be the focus of this chapter. 

Note, these concepts are not all common sense and can be difficult to wrap your head around at times. Be sure to constantly turn to your instructor or peers for assistance and remember that there are hundreds of online resources at your disposal. As with anything though, practice makes perfect. The popular rule states that mastering a skill can take upwards of 10,000 hours! Now, this course is not going to take you 10 years to complete, however the goal is that by the end of this chapter you will know your way around the basics of linear regression. 

# Quick Linear Regression

## Quick Linear regression using `Loblolly`

1. load `Loblolly` and create a scatter plot of the data so plot so that age is the independent variable and height is the
dependent variable.

![](21-linearregression_files/figure-epub3/unnamed-chunk-1-1.png)<!-- -->

2. Notice that R automatically labeled the x- and y-axes, but we also want our scatter plot to
have a main title. To add a title, use the command `title(main = “Loblolly Pine Tree Heights”)`.

![](21-linearregression_files/figure-epub3/unnamed-chunk-2-1.png)<!-- -->

3. To find a linear model that relates the age and height of the loblolly pine trees, we will use the
command `fit1<-lm(Loblolly$height~Loblolly$age)`. 

> Think of `lm(Loblolly$height~Loblolly$age)` as the slope-intercept form (y=mx+b). 

4. To see the model, type `fit1`


```r
fit1 <- lm(Loblolly$height~Loblolly$age)
fit1
#> 
#> Call:
#> lm(formula = Loblolly$height ~ Loblolly$age)
#> 
#> Coefficients:
#>  (Intercept)  Loblolly$age  
#>       -1.312         2.591
```

5. Now we want to add the graph of this line of best fit to our scatter plot. To do this, use the
command `abline(fit1)`. .

![](21-linearregression_files/figure-epub3/unnamed-chunk-4-1.png)<!-- -->

9. The final piece of information we want about our data is the correlation of the age and height
of the Loblolly pine trees. To find the correlation coefficient, use the command `cor(Loblolly$height, Loblolly$age)` 


```
#> [1] 0.9899132
#> 
#> 	Pearson's product-moment correlation
#> 
#> data:  Loblolly$height and Loblolly$age
#> t = 63.272, df = 82, p-value < 2.2e-16
#> alternative hypothesis: true correlation is not equal to 0
#> 95 percent confidence interval:
#>  0.9844505 0.9934631
#> sample estimates:
#>       cor 
#> 0.9899132
```


10.  What does this command do and mean: `plot(Loblolly)`?

![](21-linearregression_files/figure-epub3/unnamed-chunk-6-1.png)<!-- -->

# Linear Regression with mtcars

Remember: **`~`** here means "explained by", so the formula mpg ~ wt means we are predicting mpg as explained by wt. The most helpful way to view the output is with:

## Excercises for **you** 

### `mtcars`

1. Which variable in the `mtcars` dataset do you think best predicts `mpg` and why?
2. What `mpg` would you predict for a car with a displacement of 333?
3. What `mpg` would you predict for a car with a displacement of 12 cylinders?
4. What `mpg` would you predict for a car with a displacement of 333 and 12 cylinders?
5. What `mpg` would you predict for a car with a displacement of 333, 12 cylinders, and weighs 4,000 pounds?


### `trees`

Open the `trees` dataset in R.  

1. What are the variables and what do they mean?
2. Make a plot with Volume on the x axis and Height on the Y and add a best fit line.
3. Use Girth and Height to predict Volume.  What would you predict for a tree with a Girth of 10 and a Height of 100 feet?
4. Use Girth and Height to predict Volume.  What would you predict for a tree with a Girth of 10 and a Height of 15 meters?
5. What is the maximum circumference of a tree in this dataset?

## More Excercises for **you** 

1.Open the `women` data set. Add a new variable (column) to the `women` dataframe called GPA which is these 15 numbers: 1.5, 3.7, 4,1, 3, 2.5, 3.8, 0.8, 2, 4, 1, 3, 2.5, 3.0, 4.0.  You shoud get something that looks similar to mine.



```
FALSE    height weight GPA
FALSE 1      58    115 1.5
FALSE 2      59    117 3.7
FALSE 3      60    120 4.0
FALSE 4      61    123 1.0
FALSE 5      62    126 3.0
FALSE 6      63    129 2.5
FALSE 7      64    132 3.8
FALSE 8      65    135 0.8
FALSE 9      66    139 2.0
FALSE 10     67    142 4.0
FALSE 11     68    146 1.0
FALSE 12     69    150 3.0
FALSE 13     70    154 2.5
FALSE 14     71    159 3.0
FALSE 15     72    164 4.0
```

2. Use GPA and weight to predict the height of a person who is 155 pounds and has a GPA if 3.33. What is your prediction? 

3. Is GPA a significant predictor of height and how do you know? 

4. Create a figure showing a best fit line on of height and GPA.  

5. Install the dplyr package into your Rstudio session.


# Deeper Linear Regression

> Let's chat about why understaning linear regression is so important.

::: {.rmdimportant}

**While there may always seem to be something new, cool, and shiny in the field of AI/ML, classic statistical methods that leverage machine learning techniques remain powerful and practical for solving many real-world business problems.**

:::




Let's look at a very simple model first. For this example, we will need to import the Introduction to Statistical Learning package (ISLR). We will use the "credit" data set that is part of the ISLR package. 


```r
library(ISLR)
data("Credit")
attach(Credit)

M1 <- lm(Balance ~ Limit + Ethnicity)
```

lm is the function we use to create linear regression models. Now, before we discuss interpreting the results we get from this function, we will discuss the different parts of the model. The "~" symbol is the key to this entire equation. We are telling R to predict whatever is on the left side of the tilde using the variables on the right. 


## Interpretation of the Model

Let's run a summary on this model and see what we get.


```r
summary(M1)
#> 
#> Call:
#> lm(formula = Balance ~ Limit + Ethnicity)
#> 
#> Residuals:
#>     Min      1Q  Median      3Q     Max 
#> -677.39 -145.75   -8.75  139.56  776.46 
#> 
#> Coefficients:
#>                      Estimate Std. Error t value Pr(>|t|)
#> (Intercept)        -3.078e+02  3.417e+01  -9.007   <2e-16
#> Limit               1.718e-01  5.079e-03  33.831   <2e-16
#> EthnicityAsian      2.835e+01  3.304e+01   0.858    0.391
#> EthnicityCaucasian  1.381e+01  2.878e+01   0.480    0.632
#>                       
#> (Intercept)        ***
#> Limit              ***
#> EthnicityAsian        
#> EthnicityCaucasian    
#> ---
#> Signif. codes:  
#> 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 234 on 396 degrees of freedom
#> Multiple R-squared:  0.743,	Adjusted R-squared:  0.7411 
#> F-statistic: 381.6 on 3 and 396 DF,  p-value: < 2.2e-16
```

There is a lot of statistical jargon included in our summary that may be unfamiliar to those who have not taken statistics before. That is okay, however, because we are going to breakdown the main statistics we are interested in. Let's start with our variables and their significance in the model. 


### P-Values

The p-value of our model helps us either prove or disprove the null-hypothesis of our test. In the case of this class, the null-hypothesis is that there is no relationship between the variables we are using to make the predictions and the actual variable we are predicting. In other words, the smaller our p-value the higher the level of significance there is between our variables. When we run a summary of our linear regression model we are give multiple p-values. 

First, under coefficients, they are listed for each variable. This can help us optimize our model because we can see what variables are helping make the model more accurate versus those that may be hindering its performance. Also notice the asterisks next to our p-values. R kindly puts up to three stars next to each variable to help us visually tell if they are significant, essentially more stars means a lower p-value and thus a higher correlation. 
The second place we see a p-value is at the bottom of our summary. This p-value will give us the overall correlation that exists in our model. As we see in this case, our p-values for this model is < .00000000000000022, that is a tiny number and frankly a great p-value. Typically we want our p-value to be .05 or smaller. A p-value of .05 tells us that we have a confidence level of 95%. 


### Multiple R-Squared

R-squared tells us how well our model explains the variance in our variable. In other words, is the reason for the change in the independent variable actually due to our model's prediction? The higher the r-squared, the more accurate our model is because the better the data fits it. The maximum value r-squared can be is 1. 

In our model's case, we have a multiple r-squared of .743, this means our model is approximately 74.3% accurate as this is the amount of variance in the data caused by our dependent variable. Our r-squared could certainly be better. In fact, in the real world you typically are aiming for an r-squared above .9 or .95, which means you would have 90%-95% accuracy. 


## Applying the Model to Make Predictions

This type of regression is refereed to as linear for a reason. If we were to visualize our model on a quadratic plane, we would see a line of best fit that would travel along through our data. This means we can simplify the model to fit the slope-intercept equation:

y = m(x)+b

In our case the slope of our line is related to the independent variables. The sum of these slopes will give us the overall slope of our line and the intercept is provided by the equation summary. If we modify this equation to be more applicable to our situation we would get something like this:

y = m<sub>1</sub>x<sub>1</sub> + m<sub>2</sub>x<sub>2</sub> ... + b 

Let's look back at our example model from before


```r
M1 <- lm(Balance ~ Limit + Ethnicity)
summary(M1)
#> 
#> Call:
#> lm(formula = Balance ~ Limit + Ethnicity)
#> 
#> Residuals:
#>     Min      1Q  Median      3Q     Max 
#> -677.39 -145.75   -8.75  139.56  776.46 
#> 
#> Coefficients:
#>                      Estimate Std. Error t value Pr(>|t|)
#> (Intercept)        -3.078e+02  3.417e+01  -9.007   <2e-16
#> Limit               1.718e-01  5.079e-03  33.831   <2e-16
#> EthnicityAsian      2.835e+01  3.304e+01   0.858    0.391
#> EthnicityCaucasian  1.381e+01  2.878e+01   0.480    0.632
#>                       
#> (Intercept)        ***
#> Limit              ***
#> EthnicityAsian        
#> EthnicityCaucasian    
#> ---
#> Signif. codes:  
#> 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
#> 
#> Residual standard error: 234 on 396 degrees of freedom
#> Multiple R-squared:  0.743,	Adjusted R-squared:  0.7411 
#> F-statistic: 381.6 on 3 and 396 DF,  p-value: < 2.2e-16
```

We see that our limit variable has an estimate of 1.718e-01, this is our slope. When dealing with quantitative variables, we simply multiply our slope by the intended independent variable. So, if we wanted to find the balance of someone with a limit of 400, we would multiply 1.718e-01 by 400.

With the qualitative variables, in this case ethnicity, we multiply the estimate of the TRUE values by 1 and FALSE values by 0, thus cancelling the FALSE values out. 

Let's look at an example. If we used our above equation to predict the balance of someone who was Caucasian and has a credit limit of 500, here is the equation we would set up:


```r
y = (1.718e-1*500) + (1.381e+01*1) + (2.835e+01*0) + (-3.078e+02)
y
#> [1] -208.09
```
So, according to our model our customer would have a balance of -208.09. This number may seem funny, but keep in mind that our r-squared was not the best for this model making it inaccurate and the ethnicity of the customer was not highly correlated with the balance. Both of these facts may cause our prediction to be off. If we were actually creating a model that could predict balance, we would want to look at some of the more correlated variables in the data set. 


## Review Questions


1) Create a linear model predicting using the ISLR data set that predicts a customer's credit limit based on their age, current balance, and the number of cards they have. 

2) What is the p-value of this model? What does this tell us?

3) List the variables in order from most correlated to least. How do you know that they are correlated?

4) What is the multiple r-squared of the model? What does this tell us? Is this good or bad?

5) What would be the credit limit of a 29 year old with 5 cards and a total balance of 1500?

6) Explain what the following piece of code does


```r
library(ISLR)
data("Credit")
attach(Credit)
q1 <- lm(Cards ~ Limit + Balance + Education)
```


