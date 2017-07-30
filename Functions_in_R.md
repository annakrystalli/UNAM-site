
# Functions in R

<img src=https://assets.datacamp.com/production/course_1008/shields/original/shield_image_course_1008_20160610-26-1sx1zh9?1465579264 height ="200px" width="200px">


## What are functions

#### Code written to carry out specific task

Functions used to:

- incorporate sets of instructions that we want to use repeatedly
- contain complex code in a neat sub-program
- reduce opportunity for errors
- make code more readable

usually:
- accepts parameters (arguments) <- `INPUT`
- returns value(s) <- `OUTPUT`

## functions in R

### R is a functional programming language!: 
#### it provides many tools for the creation and manipulation of functions.

You can do anything with functions that you can do with vectors:

- assign them to variables 
- store them in lists
- pass them as arguments to other functions 
- create them inside functions
- return them as the result of a function


> “To understand computations in R, two slogans are helpful:
>
> - Everything that exists is an object.
> - Everything that happens is a function call."
> 
> John Chambers

even `+` and indexing through `[ ]`!

```r
`+`(3,4)
```

```
## [1] 7
```

```r
`[`(1:10, 1)
```

```
## [1] 1
```

## function basics

```r
function(arglist){body}
```
in Rstudio, typing the `fun` snippet inserts an R function definition:

```r
name <- function(variables) {
    
}
```
Just try typing `fun` 

## example function

Let's write a function that will calculate the standard deviation of the values in a vector x

```r
std.dev <- function(x){
    n <- length(x)
    xbar <- sum(x)/n
    diff <- x - xbar
    sum.sq <- sum(diff^2)
    var <- sum.sq / (n-1)
    sqrt(var)
}
```


## function environment

- every time a function is called, a new environment is created to host execution.
- each invocation is completely independent of previous ones
- variables used within are ***local***, e.g. their scope lies within - and is limited to - the function itself. They are therefore **invisible outside the function body**

```r
s.d <- std.dev(1:10)
s.d
```

```
## [1] 3.02765
```

```r
xbar
```

```
## Error in eval(expr, envir, enclos): object 'xbar' not found
```



## elements of a function

### function name

This can be any valid variable name, but you should avoid using names that are used elsewhere in R, such as `dir`, `function`, `plot`, etc

- choose descriptive names
- use verbs
- check whether they are already in use: `? function.name`


### arguments

Functions can have **any number of arguments**. These can be **any R object:** numbers, strings, arrays, data frames, of even pointers to other functions; anything that is needed for the function.name function to run.

```r
formals(std.dev)
```

```
## $x
```


The **`...`**, or **ellipsis**, element in the definition of a function allows for other arguments to be passed into the function, and passed onto to another function. 


```r
ellipsis_example <- function(...) {
    input_list <- list(...)
    output_list <- lapply(X=input_list, summary)
    return(output_list)
}
ellipsis_example(a=1:10,b=11:20,c=21:30)
```

```
## $a
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1.00    3.25    5.50    5.50    7.75   10.00 
## 
## $b
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   11.00   13.25   15.50   15.50   17.75   20.00 
## 
## $c
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   21.00   23.25   25.50   25.50   27.75   30.00
```

### body

The function code between the `{}` brackets is run every time the function is called. Ideally functions are short and do just one thing. 

```r
body(std.dev)
```

```
## {
##     n <- length(x)
##     xbar <- sum(x)/n
##     diff <- x - xbar
##     sum.sq <- sum(diff^2)
##     var <- sum.sq/(n - 1)
##     sqrt(var)
## }
```

### return value

The last line of the code is the value that will be returned by the function. It is not necessary that a function return anything, for example a function that makes a plot might not return anything, whereas a function that does a mathematical operation might return a number, or a list.

## arguments & environment

All arguments required for computation must be supplied.


missing arguments not required for computation are fine:

```r
f1 <- function(a, b, c){a + b}
f1(a = 10 , b = 20)
```

```
## [1] 30
```
objects required by function will be sought first in the ***local environment***. If an argument specified in the function is missing, it will return an error, even if such an object exists in the global environment.

```r
b <- 10
f1 <- function(a, b){a + b}
f1(a = 10)
```

```
## Error in f1(a = 10): argument "b" is missing, with no default
```

```r
f1(a = 10 , b = 20)
```

```
## [1] 30
```

Objects required by computation but not specified as function arguments will be sought in the containing environment iteratively until it reaches the ***global environment***.


```r
b <- 10
f2 <- function(a){a + b}
f2(a = 10)
```

```
## [1] 20
```

```r
rm(b) # remove object b
f2(a = 10)
```

```
## Error in f2(a = 10): object 'b' not found
```

Default values for arguments can also be supplied when writing the functions

```r
f3 <- function(a, b = 20){a + b}
f3(a = 10)
```

```
## [1] 30
```

```r
f3(a = 10, b = 10)
```

```
## [1] 20
```



## outputs

A function by default returns the last 'thing' evaluated

```r
f1 <- function(x){x + 10}
f1(10) # returns a value
```

```
## [1] 20
```

```r
f2 <- function(x){
    y <- x + 10}
f2(10) # return an object which needs to be assigned
z <- f2(10)
z
```

```
## [1] 20
```

```r
f3 <- function(x){
    y <- x + 10
    return(y)} 
f3(10) # returns a value
```

```
## [1] 20
```

```r
v <- f3(10)
v
```

```
## [1] 20
```

I generally advise you always use `return()` to specify the outputs of your functions. You can also use it conditionally to return different values or hault evaluation and return back to the calling environment:

```r
f1 <- function(x) {
    y <- x - 10
    if(y < 0){return(NA)}else{
        y <- 2 * y
        return(y)}
}

f1(20)
```

```
## [1] 20
```

```r
f1(5)
```

```
## [1] NA
```


## multiple outputs

If you want to return multiple values, you can collect objects created within a function in a list.

```r
std.dev <- function(x){
    n <- length(x)
    xbar <- sum(x)/n
    diff <- x - xbar
    sum.sq <- sum(diff^2)
    var <- sum.sq / (n-1)
    s.d <- sqrt(var)
    
    return(list(s.d, xbar, n))
}

std.dev(1:10)
```

```
## [[1]]
## [1] 3.02765
## 
## [[2]]
## [1] 5.5
## 
## [[3]]
## [1] 10
```
This is basically what outputs of function like `lm` are, a list.


## Calling a function given a list of arguments

Suppose you had a list of function arguments:


```r
args <- list(c(1:10, NA), na.rm = TRUE)
```
You could you then send that list to `mean()` by using `do.call()`:


```r
do.call(mean, list(1:10, na.rm = TRUE))
```

```
## [1] 5.5
```


## function pipes

If you have a long workflow of computations:
- break it up into logical blocks - write function for each
- write functions so that output from one is the first argument to the next
- use package `dplyr` and the **pipe** shorthand `%>%` to set up **function pipeline**

```r
install.packages("dplyr")
```

Say I want to prepare a vector of values by removing NAs, scaling and centering the values. First I create a list containg the vector of values as well as an element to track the status of the process.

```r
require(dplyr)
```

```
## Loading required package: dplyr
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
l <- list(x = c(1:10, NA), status = NULL)
```

Then I write three functions that will receive and return the list.

```r
rmNAs <- function(X){
    X$x <- na.omit(X$x)
    X$status <- c(X$status, "NAs_removed")
    return(X)
}
         
scaleVector <- function(X){
    X$x <- scale(X$x, scale = T)
    X$status <- c(X$status, "scaled")
    return(X)
}          
          
centerVector <- function(X){
    X$x <- scale(X$x, center = T)
    X$status <- c(X$status, "centered")
    return(X)
}  
```

Then I set up a pipeline with the functions and pass the vector through:

```r
l %>% rmNAs() %>% scaleVector %>% centerVector
```

```
## $x
##             [,1]
##  [1,] -1.4863011
##  [2,] -1.1560120
##  [3,] -0.8257228
##  [4,] -0.4954337
##  [5,] -0.1651446
##  [6,]  0.1651446
##  [7,]  0.4954337
##  [8,]  0.8257228
##  [9,]  1.1560120
## [10,]  1.4863011
## attr(,"scaled:center")
## [1] 0
## attr(,"scaled:scale")
## [1] 1
## 
## $status
## [1] "NAs_removed" "scaled"      "centered"
```

## anonymous functions

If you just want to use a function once, you don't have to name it:

```r
(function(x) x * 10)(10)
```

```
## [1] 100
```
Anonymous functions can be particularly useful in conjunction with vectorising functions like `lapply()`. Here's an unammed function for calculating the mean of a vector `x`. In the following example, the input `x` to the function is each element of the list `l`.

```r
l <- list(1:5, 5:7)
lapply(l, FUN = function(x){sum(x)/length(x)})
```

```
## [[1]]
## [1] 3
## 
## [[2]]
## [1] 6
```


## sourcing functions

I often write functions associated with a particular project

I will save all the functions in a separate `"project.name_functions.R"` script. I'll then call that script to make all the functions available to my workflow.


```r
source("project.name_functions.R")
```

<br>
***

## Avoiding errors

Let's start with another example of a function:

```r
getY <- function(X.matrix, b.vec, a.scalar) {

    # multiply the matrix by the vector using %*% operator
    Xb.prod <- X.matrix %*% b.vec

    # multiply the two resulting objects together to get a final object
    y <- Xb.prod * a.scalar

    # return the result
    return(y)
}
```
Clearly this function requires that the length of the vector and the number of columns in the matrix match.

Let's make some objects to pass to the function:

```r
mat <- cbind(c(1, 3, 4), c(5, 4, 3))
vec <- c(4, 3)

getY(mat, vec, 3)
```

```
##      [,1]
## [1,]   57
## [2,]   72
## [3,]   75
```

In this case the function works because the number of columns of matrix `mat` (2) and the length of `vec` (2) match.

How can we ensure that we don't get errors?
<br>

### 1. sanity checks

We can adapt the function and use the `print()` function to print off values of interest, for example the dimensions of arguments of concern

```r
getY <- function(X.matrix, b.vec, a.scalar) {
    
    # print diagnostics
    print(dim(X.matrix))
    print(length(b.vec))

    # multiply the matrix by the vector using %*% operator
    Xb.prod <- X.matrix %*% b.vec

    # multiply the two resulting objects together to get final y
    y <- Xb.prod * a.scalar
    
    return(y)
}

getY(mat, vec, 3)
```

```
## [1] 3 2
## [1] 2
```

```
##      [,1]
## [1,]   57
## [2,]   72
## [3,]   75
```


### 2. debugging

When you have an error, one thing you can do is use R’s built-in debugger debug() to find at what point the error occurs.

```r
debug(getY)
getY(X.matrix = mat, b.vec = c(2, 3, 6, 4, 1), a.scalar = 9)
```

```
## debugging in: getY(X.matrix = mat, b.vec = c(2, 3, 6, 4, 1), a.scalar = 9)
## debug at <text>#1: {
##     print(dim(X.matrix))
##     print(length(b.vec))
##     Xb.prod <- X.matrix %*% b.vec
##     y <- Xb.prod * a.scalar
##     return(y)
## }
## [1] 3 2
## [1] 5
```

```
## Error in X.matrix %*% b.vec: non-conformable arguments
```

## 3. stopping and error messages

To ensure functions run smoothly you can use functions `stop()` or `stopifnot()` to hault the execution of functions should specific conditions not be met and flag with an appropriate and informative error

#### `stop()`

stops execution and returns error message. Usually used with conditional statements

```r
f1 <- function(x) {
    if(!is.numeric(x)){stop("x is not numeric")}else{
        return(2*x)
    }
}
f1(10)
```

```
## [1] 20
```

```r
f1("a")
```

```
## Error in f1("a"): x is not numeric
```

#### `stopifnot()`
tests the conditional statements supplied as arguments and stops execution if any return `FALSE`

```r
f1 <- function(x) {
    stopifnot(is.numeric(x))
    return(2*x)
}
f1(10)
```

```
## [1] 20
```

```r
f1("a")
```

```
## Error: is.numeric(x) is not TRUE
```

<br>

## Testing

Each function should be easy to test, then you can “freeze” it. Write
test cases, which can be automatically checked.
- [Unit Testing in R: The Bare Minimum](http://www.johnmyleswhite.com/notebook/2010/08/17/unit-testing-in-r-the-bare-minimum/)


<br>

***

## Tips & tricks

- **Keep your functions short.** Remember you can use them to call other functions!
    - code cleaner and easily testable.
    - code easy to update
- **Document** what the inputs to the function are, what the function does, and what the output is.
- **Check for errors** along the way
- Try out your function with **simple examples** to make sure it’s working properly
- **Use debugging and error messages**, as well as sanity checks as you build your function.
- Avoid mixing computation and plotting in the same
function
eg. 

```r
res <- some.computation(par1, par2, par3) 
plot(res)
```

- it can be useful to look at the code of a function. Type the function name without the `( )`

```r
std.dev
```

```
## function(x){
##     n <- length(x)
##     xbar <- sum(x)/n
##     diff <- x - xbar
##     sum.sq <- sum(diff^2)
##     var <- sum.sq / (n-1)
##     s.d <- sqrt(var)
##     
##     return(list(s.d, xbar, n))
## }
```
Will work on any function apart from base functions which are written in C








## Acknowledgements

-[A Tutorial on Using Functions in R!](https://www.datacamp.com/community/tutorials/functions-in-r-a-tutorial#gs.okPRU_w)

- [Advanced R by Hadley Wickham::functions](http://adv-r.had.co.nz/Functions.html)

- [How to write and debug an R function](https://www.r-bloggers.com/how-to-write-and-debug-an-r-function/)
### Sources of material & further reading

[Official R Documentation](https://cran.r-project.org/doc/manuals/R-intro.html#Writing-your-own-functions)

