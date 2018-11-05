# Vectors

Vectors come in two different flavors: atomic vectors and lists. 

* An atomic vector contains exactly one data type,
* A list may contain multiple data types. 

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
