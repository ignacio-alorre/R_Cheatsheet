# Vectors

### Introduction

### Assigning a vector in R

```R
 z <- c(1.1, 9, 3.14)
```
### Concatenating vectors:

``` R
Zz <-  c(z,555,z)
```

`
[1]   1.10   9.00   3.14   555.00   1.10   9.00   3.14
`

When given two vectors of the same length, R simply performs the specified arithmetic operation (`+`, `-`, `*`,  etc.) element-by-element.
If the vectors are of different lengths, R 'recycles' the shorter vector until it is the same length as the longer vector.

**For example**

If we do  

```R
z * 2 + 100 
```
z was a vector of length 3, but technically 2 and 100 are each vectors of length 1.

Behind the scenes, R is 'recycling' the 2 to make a vector of 2s and the 100 to make a vector of 100s. In other words, when you ask R to compute z * 2 + 100, what it really computes is this: z * c(2, 2, 2) + c(100, 100, 100).

In case we write:

```R
c(1,2,3,4)+c(0,1,0)
```
We will get:

`
Warning message: longer object length is not a multiple of shorter object length
`

However if we try con sum two vectors like this:

```R
c(1,2,3,4)+c(0,10)
```
We will get

`
[1]  1 12  3 14
`

Vectors come in two different flavors: atomic vectors and lists. 

* An Atomic Vector contains exactly one data type,
* A List may contain multiple data types. 

## Atomic vectors

Atomic vectors include numeric, logical, character, integer, and complex.

**Logical vectors** can contain the values TRUE, FALSE, and NA (for 'not available'). These values are generated as the
result of logical 'conditions'. For example:

``` R
num_vect <- c(0.5, 55, -10, 6)
```

Now a logical vector would be

``` R
tf <- num_vect < 1
```

If we have two logical expressions, A and B, we can ask whether at least one is TRUE with A | B (logical 'or' a.k.a.
 'union') or whether they are both TRUE with A & B (logical 'and' a.k.a. 'intersection'). Lastly, !A is the negation
of A and is TRUE when A is FALSE and vice versa. For example

``` R
my_char <- c("My","name","is")
```

### Joining elements from a Vector into a single String

Let's say we want to join the elements of my_char together into one continuous character string (i.e. a character vector of length 1)
We can do this using the paste(). Use paste(my_char, collapse = " ") now

``` R
paste(my_char, collapse = " ")
```

`
My name is
`
Another approach would be using paste and passing the separator argument. For example:

``` R
paste("Hello", "world!", sep = " ")
```

`
[1] "Hello world!"
`

Another example:

``` R
paste(1:3,c("X", "Y", "Z"), sep="")
```

`
[1] "1X" "2Y" "3Z"
`

To refresh vector recicling try paste(LETTERS, 1:4, sep = "-"), where LETTERS is a predefined variable in R containing a
character vector of all 26 letters in the English alphabet

``` R
paste(LETTERS, 1:4, sep = "-")
```

`
[1] "A-1" "B-2" "C-3" "D-4" "E-1" "F-2" "G-3" "H-4" "I-1" "J-2" "K-3" "L-4" "M-1" "N-2" "O-3" "P-4" "Q-1" "R-2" "S-3"
[20] "T-4" "U-1" "V-2" "W-3" "X-4" "Y-1" "Z-2"
`

Since the character vector LETTERS is longer than the numeric vector 1:4, R simply recycles, or repeats, 1:4 until
 it matches the length of LETTERS.


### Subsetting vectors

The way you tell R that you want to select some particular elements (i.e. a 'subset') from a vector is by placing an 'index vector' 
in square brackets immediately following the name of the vector. For example

``` R
x <- 1:50
x[1:10]
```

`
 [1]  1.3951681         NA         NA         NA         NA  2.1822973 -1.2372279         NA
 [9]  1.1838587  0.6482982
`
## Indexing Vectors

Index vectors come in four different flavours: 

* logical vectors
* vectors of positive integers
* vectors of negative integers
* vectors of character strings

### Logical vectors

One common scenario when working with real-world data is that we want to **extract all elements of a vector that are not NA** (i.e. missing data). Recall that **is.na(x)** yields a vector of logical values the same length as x, with TRUEs corresponding to NA values in x and FALSEs corresponding to non-NA values in x.


Let's start by indexing with logical vectors. One common scenario when working with real-world data is that we want to extract 
all elements of a vector that are not NA (i.e. missing data)

``` R
x <- 1:20
x[is.na(x)]
```

`
 [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA
`

Recall that `!` gives us the negation of a logical expression, so !is.na(x) can be read as 'is not NA'. Therefore, if we want to create
 a vector called y that contains all of the non-NA values from x

``` R
y <- x[!is.na(x)]
```

To get all of the positive elements of y, which are also the positive elements of our original vector x.

``` R
y[y > 0]
```

`
[1] 1.3951681 2.1822973 1.1838587 0.6482982 0.1217270 0.6985751 0.8156217 0.1131666 0.9101274
[10] 1.2717335 0.4134691 0.1943982 0.2456427
`

Since NA is not a value, but rather a placeholder for an unknown quantity, the expression NA > 0 evaluates to NA. Hence we get a bunch 
of NAs mixed in with our positive numbers when we do this.

``` R
x[x > 0]
```

`
 [1] 1.3951681        NA        NA        NA        NA 2.1822973        NA 1.1838587 0.6482982
[10]        NA        NA 0.1217270        NA        NA        NA 0.6985751 0.8156217        NA
[19] 0.1131666 0.9101274        NA 1.2717335 0.4134691 0.1943982        NA 0.2456427        NA
[28]        NA        NA        NA        NA        NA        NA
`

It is possible to combine logical operators with subsetting, For example

``` R
x[!is.na(x) & x > 0]
```

`
 [1] 1.3951681 2.1822973 1.1838587 0.6482982 0.1217270 0.6985751 0.8156217 0.1131666 0.9101274
[10] 1.2717335 0.4134691 0.1943982 0.2456427
`

R uses 'one-based indexing', which means the first element of a vector is considered element 1. For example:

``` R
x[0]
```

`
numeric(0)
`

In case you set an index out of the range you will get NA

``` R
x[3000]
```

`
[1] NA
`

Subset the 3rd, 5th, and 7th elements of x

``` R
x[c(3,5,7)]
```

`
[1]        NA        NA -1.237228
`

### Selecting all elements except a few indexs 

For example to get all elements except the 2 and 10

``` R
 x[c(-2, -10)] 
```

Another option would be

```R
Another option would be x[-c(2, 10)]
```

### Vector with named elements

``` R
vect <- c(foo = 11, bar = 2, norf = NA)
```

`
 foo  bar norf 
  11    2   NA 
`
### Getting the keys of a named vector 

``` R
names(vect)
```
`
[1] "foo"  "bar"  "norf"
`

It is also possible to store the names of the keys in a sequence to later assign those name to another vector. For example

``` R
vect2 <- c(11,2,NA)
names(vect2) <- c("foo", "bar", "norf")
```

### Checking if two vectors are identical

``` R
identical(vect,vect2)
```

`
[1] TRUE
`

### Geting the value of a named vector by passing the name of the key


``` R
vect["bar"]
```

`
bar 
  2 
`
`
