# Functions and apply()

### Functions

Most functions in R return a value. Functions like Sys.Date() return a value based on your computer's environment, 
while other functions manipulate input data in order to compute a return value.

Inputs to functions are often called arguments. Providing arguments to a function is also sometimes called passing arguments to 
at function. Arguments you want to pass to a function go inside the function's parentheses. For example:

``` R
boring_function <- function(x) {
  x
}
```

To invoke a function:

``` R
boring_function("any paraneter here")
```

### Checking the code of a function

``` R
boring_function
```

### Functions with default arguments:

``` R
remainder <- function(num, divisor = 2) {
  num %% divisor
}
```

Different options to invoke this function:

``` R
remainder(divisor = 11, num = 5)
remainder(4, div = 2)
remainder(11, 2)
remainder(5)
```

### Retrieving the arguments of a function

``` R
args(remainder) 
```

`
function (num, divisor = 2) 
NULL
`

**Note**: It is possible to pass a function as an argument to another function

``` R
evaluate <- function(func, dat){
  func(dat)
}
```

In the following example we will pass the standard deviation function as an argument

``` R
evaluate(sd, c(1.4, 3.6, 7.9, 8.8))
```

`
[1] 3.514138
`

### Anonymous functions

It is possible to pass a function as an argument without first defining the passed function. Functions that are not named are 
appropriately known as anonymous functions. For example:

``` R
evaluate(function(x){x+1},6)
```

`
[1] 7
`

The first argument is a tiny anonymous function that takes one argument `x` and returns `x+1`. We passed the number 6 into 
this function so the entire expression evaluates to 7.

Another example, of a function which returns the first element of an array:

``` R
evaluate(function(x){x[1]},c(8, 4, 0))
```

`
[1] 8
`

### Default values for arguments

Notice in the function below that the ellipses is the first argument, and all other arguments after the ellipses have default values

``` R
paste (..., sep = " ", collapse = NULL)
```

**Note**: This is a strict rule in R programming: all arguments after an ellipses must have default values.  Another example:

``` R
telegram <- function(...){
  paste("START",..., end = "STOP")
}
```

``` R
telegram("The", "house", "is on", "fire")
```

`
[1] "START The house in on fire STOP"
`

### Unpacking arguments from an ellipses

 Let's explore how to "unpack" arguments from an ellipses when you use the ellipses as an argument in a function.
 First we must capture the ellipsis inside of a list and then assign the list to a variable. Let's name this variable `args`. 
 For example:

``` R
mad_libs <- function(...){
  args <- list(...)
  place <- args[["place"]]
  adjective <- args[["adjective"]]
  noun <- args[["noun"]]

  paste("News from", place, "today where", adjective, "students took to the streets in protest of the new", noun, "being installed on campus.")
}
```

`` R
mad_libs(place="Xixon", adjetive= "angry", noun = "traffic light")
```

### Defining binary operators

The syntax for creating new binary operators in R is unlike anything else in R, but it allows you to define a new syntax for your 
function. I would only **recommend making your own binary operator if you plan on using it often!**

User-defined binary operators have the following syntax:
     %[whatever]% 
 where [whatever] represents any valid variable name.

If we want that "Good" %p% "job!" will evaluate to: "Good job!" we should define an opperator like:

``` R
"%p%" <- function(left,right){ # Remember to add arguments!
  paste(left,right)
}
```

``` R
'I'%p%'love'%p%'R!'
```

`
[1] "I love R!"
`


### lapply() and sapply() 

Each of the *apply functions will:

1. **SPLIT** up some data into smaller pieces
2. **APPLY** a function to each piece
3. **COMBINE** the results. 

The **lapply()** function takes a **list** as input, applies a function to each element of the list, then returns a list of the same length as the original one. 

Since a data frame is really just a list of vectors (you can see this with as.list(flags)), we can use lapply() to apply the class() 
function to each column of the flags dataset.

``` R
cls_list <- lapply(flags, class)
```

Another example

``` R
lapply(1:3, function(x) x^2)
```
`
[[1]]
[1] 1

[[2]]
[1] 4

[[3]]
[1] 9
`

As expected, we got a list of length 30, one element for each variable/column. This can be simplified and described as a vector. 
For example:

``` R
as.character(cls_list)
```

`
 [1] "factor"  "integer" "integer" "integer" "integer" "integer" "integer" "integer" "integer"
[10] "integer" "integer" "integer" "integer" "integer" "integer" "integer" "integer" "factor" 
[19] "integer" "integer" "integer" "integer" "integer" "integer" "integer" "integer" "integer"
[28] "integer" "factor"  "factor" 
`

It is possible to make this simplification step on apply itself using **sapply()**

``` R
cls_vect <- sapply(flags,class)
```

In general, if the **result** is a **list** where every element is of length one, then `sapply()` returns a **vector**. 
If the **result** is a **list where every element is a vector** of the same length  (> 1), sapply() returns a **matrix**.
If sapply() can't figure things out, then it just returns a list, no different from what lapply() would give you.


In the flag dataset we have several variables which represent colors. If we want to know the total number of countries (in our dataset)
with the colour orange on their flag, we can just add up all of the 1s and 0s in the 'orange' column. For example

``` R
sum(flags$orange)
```

Now we want to repeat this operation for all the colour columns. First we extract the columns which belong to colours: 

``` R
 flag_colors <- flags[, 11:17]
```

Then we pass the subset from flags (that is flag_colors) and the function to apply:

``` R
lapply(flag_colors,sum)
```

`
$`red`
[1] 153
$green
[1] 91
$blue
[1] 99
$gold
[1] 91
…
`

If we want to retrieve the results in a vector format instead of in a list:

``` R
sapply(flag_colors,sum)
```

`
   red  green   blue   gold  white  black orange 
   153     91     99     91    146     52     26 
`

### range()

The range() function returns the minimum and maximum of its first argument, which should be a numeric vector. 
So after using sapply() we will get a matrix

`
shape_mat
         circles crosses saltires quarters sunstars
[1,]       0             0            0        0                0
[2,]       4             2            1        4               50
`

### Some useful combination for data analusis:

``` R
unique_vals <- lapply(flags,unique)
sapply(unique_vals,length)
```

You can pass to apply functions anonymous functions. For example to pick up just the second element of the vector

``` R
lapply(unique_vals, function(elem) elem[2]) 
```

The only difference between previous examples and this one is that we are defining and using our own function right in the call 
to lapply(). Our function has no name and disappears as soon as lapply() is done using it. So-called 'anonymous functions' can 
be very useful when one of R's built-in functions isn't an option.

### vapply

Whereas sapply() tries to 'guess' the correct format of the result, vapply() allows you to **specify the format explicitly**. 
If the result doesn't match the format you specify, vapply() will throw an error, causing the operation to stop. This can prevent 
significant problems in your code that might be caused by getting unexpected return values from sapply(). For example:

``` R
vapply(flags, unique, numeric(1))
```

`
Error in vapply(flags, unique, numeric(1)) : values must be length 1, but FUN(X[[1]]) result is length 194
`


You might think of **vapply() as being 'safer' than sapply()**, since it requires you to specify the format of the output in advance, 
instead of just allowing R to 'guess' what you wanted. In addition,** vapply() may perform faster than sapply() for large datasets**. 
However, when doing data analysis interactively (at the prompt), sapply() saves you some typing and will often be good enough.

### tapply()

As a data analyst, you'll often wish to split your data up into groups based on the value of some variable, then apply a function 
to the members of each group. The next function we'll look at, tapply(), does exactly that.

If you take the arithmetic mean of a bunch of 0s and 1s, you get the proportion of 1s. If we want to get the mean function to the 
'animate' variable separately for each of the six landmass groups, thus giving us the proportion of flags containing an animate 
image WITHIN each landmass group.

``` R
 tapply(flags$animate, flags$landmass, mean)
```

`
1                    2                  3                     4                     5                     6 
0.4193548   0.1764706  0.1142857   0.1346154    0.1538462    0.3000000 
`

Similarly, we can look at a summary of population values (in round millions) for countries with and without the color red on their 
flag with:

``` R
tapply(flags$population, flags$red, summary)
```

`
$`0`
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   0.00    0.00    3.00   27.63    9.00  684.00 
$`1`
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    0.0     0.0     4.0    22.1    15.0  1008.0 
`
