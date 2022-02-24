# Matrices

## CBind and RBind

Matrices can be created in R in a variety of ways. Perhaps the simplest is to create the columns (just a couple of objects) and then glue them together with the command cbind. For example,

```r
x<-c(5,7,9)
y<-c(6,3,4)
z<-cbind(x,y)
z
#>      x y
#> [1,] 5 6
#> [2,] 7 3
#> [3,] 9 4
```


The dimension of a matrix can be checked with the dim command:

```r
dim(z)
#> [1] 3 2
```

[1] 3 2 i.e., three rows and two columns. There is a similar command, rbind, for building matrices by gluing rows together.  

The functions cbind and rbind can also be applied to matrices themselves (provided the dimensions match) to form larger matrices. For example,

```r
rbind(z,z)
#>      x y
#> [1,] 5 6
#> [2,] 7 3
#> [3,] 9 4
#> [4,] 5 6
#> [5,] 7 3
#> [6,] 9 4
```

### Review Questions

1) Create a matrix made up of two columns showing the GPAs and number of hours studied by seven students. 

2) Recreate the following matrix in R:

```
#>      x   y
#> [1,] 5 3.4
#> [2,] 7 4.0
#> [3,] 2 2.5
#> [4,] 3 3.2
#> [5,] 8 2.8
#> [6,] 4 3.1
#> [7,] 2 3.6
```

3) Using the appropriate function, combine the two matrices you created above.

## Matrix Function

Matrices can also be built by explicit construction via the function matrix. For example,


```r
z<-matrix(c(5,7,9,6,3,4),nrow=3)
```
results in a matrix z identical to z above. Notice that the dimension of the matrix is determined by the size of the vector and the requirement that the number of rows is 3, as specified by the argument nrow=3. As an alternative we could have specified the number of columns with the argument ncol=2 (obviously, it is unnecessary to give both). Notice that the matrix is 'flled up' column-wise. If instead you wish to fill up row-wise, add the option byrow=T. For example,


```r
z<-matrix(c(5,7,9,6,3,4),nr=3,byrow=T)
z
#>      [,1] [,2]
#> [1,]    5    7
#> [2,]    9    6
#> [3,]    3    4
```

Notice that the argument nrow has been abbreviated to nr. Such abbreviations are always possible for function arguments provided it induces no ambiguity - if in doubt always use the full argument name.

As usual, R will try to interpret operations on matrices in a natural way. For example, with z as above, and


```r
y<-matrix(c(1,3,0,9,5,-1),nrow=3,byrow=T)
y
#>      [,1] [,2]
#> [1,]    1    3
#> [2,]    0    9
#> [3,]    5   -1
```

we obtain


```r
y+z
#>      [,1] [,2]
#> [1,]    6   10
#> [2,]    9   15
#> [3,]    8    3
```

and


```r
y*z
#>      [,1] [,2]
#> [1,]    5   21
#> [2,]    0   54
#> [3,]   15   -4
```

Other useful functions on matrices are to transpose a matrix:


```r
z
#>      [,1] [,2]
#> [1,]    5    7
#> [2,]    9    6
#> [3,]    3    4
t(z)
#>      [,1] [,2] [,3]
#> [1,]    5    9    3
#> [2,]    7    6    4
```

As with vectors it is useful to be able to extract sub-components of matrices. In this case, wemay wish to pick out individual elements, rows or columns. As before, the [ ] notation is used to subscript. The following examples should make things clear:


```r
z[1,1]
#> [1] 5
```


```r
z[c(2,3),2]
#> [1] 6 4
```


```r
z[,2]
#> [1] 7 6 4
```

> 

```r
z[1:2,]
#>      [,1] [,2]
#> [1,]    5    7
#> [2,]    9    6
```

So, in particular, it is necessary to specify which rows and columns are required, whilst omitting
the integer for either dimension implies that every element in that dimension is selected.

## Exercises


1. Create this matrix in R


```
#>      [,1] [,2] [,3] [,4] [,5]
#> [1,]    1    7    8   11   -5
#> [2,]    3    8    6    3   -9
#> [3,]    0   11   14   14   14
```

2. Create in R these matrices: 





```r
x
#>      [,1] [,2]
#> [1,]    1    7
#> [2,]    8   11
#> [3,]    5    9
y
#>      [,1] [,2]
#> [1,]    6    8
#> [2,]    2    1
#> [3,]    1   -7
```

3. Calculate the following and check your answers in R:

(a) 2*x
(b) x*x
(c) t(y)


```
#>      [,1] [,2]
#> [1,]    2   14
#> [2,]   16   22
#> [3,]   10   18
#>      [,1] [,2]
#> [1,]    1   49
#> [2,]   64  121
#> [3,]   25   81
#>      [,1] [,2] [,3]
#> [1,]    6    2    1
#> [2,]    8    1   -7
```

4. With x and y as above, calculate the effect of the following subscript operations and check
your answers in R.

(a) x[1,]
(b) x[2,]
(c) x[,2]
(d) y[1,2]
(e) y[,2:3]

