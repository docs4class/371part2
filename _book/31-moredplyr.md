# More DPLYR 

## Introduction

For more help **PLEASE** check out  [Introduction to dplyr](https://cran.r-project.org/web/packages/dplyr/vignettes/dplyr.html) introducing the key functionality of the dplyr package.

> Your life is about to change.  **For the better, even.**

## Single table verbs

`dplyr` aims to provide a function for each basic verb of data manipulation. These verbs can be organised into three categories based on the component of the dataset that they work with:

Rows:

- `filter()` chooses rows based on column values.
- `slice()` chooses rows based on location.
- `arrange()` changes the order of the rows.
    
Columns:

- `select()` changes whether or not a column is included.
- `rename()` changes the name of columns.
- `mutate()` changes the values of columns and creates new columns.
- `relocate()` changes the order of the columns.
    Groups of rows:
- `summarise()` collapses a group into a single row.  Itâs not that useful until we learn `group_by()`
- `group_by()` usually works with `summarise()`

## More with the pipe

All of the `dplyr` functions take a data frame (or tibble) as the first argument. Rather than forcing the user to either save intermediate objects or nest functions, dplyr provides the `%>%` operator from `magrittr`. One step is then âpipedâ into the next step. You can use the pipe to rewrite multiple operations that you can read left-to-right, top-to-bottom (reading the pipe operator as âthenâ).

> What is this: `%>%`?

## Loading `dplyr` and the `starwars` dataset


```r
# You should already have done this but you'll need it
install.packages("dplyr")
```






```r
library(dplyr)

starwars %>% 
  filter(species == "Droid")


starwars %>% 
  select(name, ends_with("color"))


starwars %>% 
  mutate(name, bmi = mass / ((height / 100)  ^ 2)) %>%
  select(name:mass, bmi)


starwars %>% 
  arrange(desc(mass))

starwars %>%
  group_by(species) %>%
  summarise(
    n = n(),
    mass = mean(mass, na.rm = TRUE)
  ) %>%
  filter(
    n > 1,
    mass > 50
  )
```

## `starwars` Excercises

Please use the `starwars` dataset from the `dplyr` package to answer the following questions:

1. How may humans are in this dataset?
2. How many characters are taller than 89 cm?
3. How many characters are taller than 37 inches?
4. How many characters are taller than 37 inches and weigh more than 55 pounds?
6. How many characters are not human or droid?
6. How many characters are not human or droid and are taller than 47 inches?
1. Which species has the most individuals included in this data set?
2. Which species has the tallest individuals on average?
3. What is the tallest individual for each species?
4. Calculate the BMI for each individual and determine which individual has the highest BMI.  Use the formula `bmi = mass/((height/100)^2)` to calculate bmi.
5. Which homeworld has the most individuals included in this data set?
6. Which homeworld has the tallest individuals on average?
7. What is the tallest individual for each eye color?
