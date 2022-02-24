# Filters and packages

Filtering data is one of the very basic operation when you work with data. You want to remove a part of the data that is invalid or simply you’re not interested in. Or, you want to zero in on a particular part of the data you want to know more about

For example, in the `randu` dataset, how many `y` variables are greater than 0.5?  0.6?


```r
length(randu$y[randu$y>0.5])
#> [1] 191
new.randu <- randu$y[randu$y>0.6]
head(new.randu)
#> [1] 0.873416 0.648545 0.826873 0.926590 0.741526 0.846041
length(new.randu)
#> [1] 161
```

In the `randu` dataset, how many `z` variables are greater than 0.9?  Less than 0.1?  Greater than 0.9 or less than 0.1?


```r
length(randu$z[randu$z>0.9])
#> [1] 29
length(randu$z[randu$z<0.1])
#> [1] 37
```

## R packages
> From Wikipedia, the free encyclopedia, and fount of all knowledge

R packages are extensions to the R statistical programming language. R packages contain code, data, and documentation in a standardised collection format that can be installed by users of R, typically via a centralised software repository such as CRAN (the Comprehensive R Archive Network).

The large number of packages available for R, and the ease of installing and using them, has been cited as a major factor in driving the widespread adoption of the language in data science.

## You can install the latest released version from CRAN with:

`install.packages("dplyr")`

## In RStudio 

Installing Packages

- Open RStudio. ...
- In the lower-right pane of RStudio, select the Packages tab and the Install button.
- Type the name of the packages to be installed in the “Packages (separate multiple packages with a space or comma):” box. ...
- Press Install .

## Check this out

[dplyr link](https://dplyr.tidyverse.org/)

https://dplyr.tidyverse.org/
