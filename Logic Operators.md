# Logic operators

### AND operator
There are two AND operators in R: `&` and `&&`. Both operators work similarly, if the right and left operands 
of AND are both TRUE the entire expression is TRUE, otherwise it is FALSE. 

**Differences between `&` and `&&`

You can use the `&` operator to evaluate AND across a vector. 

```R
TRUE & c(TRUE, FALSE, FALSE)
```

`
[1]  TRUE FALSE FALSE
`
This is the equivalent statement as c(TRUE, TRUE, TRUE) & c(TRUE, FALSE, FALSE). However when using '&&':


The `&&` version of AND only evaluates the first member of a vector.

``` R
TRUE && c(TRUE, FALSE, FALSE)
```

`
[1] TRUE
`

The left operand is only evaluated with the first member of the right operand


### OR operator

The `|` version of OR evaluates OR across an entire vector, while the `||` version of OR only evaluates the first member of a vector

**Note**
Arithmetic has an order of operations and so do logical expressions. All AND operators are evaluated before OR operators.


### isTRUE()

The function isTRUE() takes one argument. If that argument evaluates to TRUE, the function will return TRUE. 
Otherwise, the function will return FALSE. 

```R
isTRUE(6 > 4)
```
`
[1] TRUE
`

### xor()

The xor() function stands for exclusive OR. If one argument evaluates to TRUE and one argument evaluates to FALSE, then this 
function will return TRUE, otherwise it will return FALSE. 

``` R
xor(5 == 6, !FALSE)
```

`
[1] TRUE
`

### Logical operators with vectors

``` R
ints <- sample(10)
```

`
 [1]  4  8  7  5  1  3  6  9  2 10
`

``` R
ints > 5
```

`
 [1] FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE  TRUE
`

### which()

The which() function takes a logical vector as an argument and returns the indices of the vector that  are TRUE. Some examples:


```R 
which(c(TRUE, FALSE, TRUE))
```
`
[1] 1 3
`

``` R
which(ints > 7)
```

`
[1]  2  8 10
`

### Any() and All()
Like the which() function, the functions any() and all() take logical vectors as their argument. 

* The any() function will return TRUE if one or more of the elements in the logicalvector is TRUE. 
* The all() function will return TRUE if every element in the logical vector is TRUE.

Example:

``` R
any(ints < 0)
```

`
[1] FALSE
`
