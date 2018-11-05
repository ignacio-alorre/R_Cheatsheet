# Vectors

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
