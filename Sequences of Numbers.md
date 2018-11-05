# Sequences of Numbers
 
### Creating a simple Sequence

By using the `:` operator we will get a sequence with every integer between (and including) the giving limits

``` R
1:20
```

`
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
`

``` R
pi:10
```

`
[1] 3.141593 4.141593 5.141593 6.141593 7.141593 8.141593 9.141593
`

Another possible approach is by using seq()


```R
seq(1,20)
```

`
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
`

### Creating a Sequence with an increment different to 1

``` R
seq(0,10, by=0.5)
```

`
 [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0  7.5  8.0  8.5
[19]  9.0  9.5 10.0
`

### Creating a sequence giving the limits and the amount of elements inthe sequence

``` R
seq(5, 10, length=30) 
```

Another option:

``` R
seq(along.with = my_seq)
```

R has a separate built-in function for this purpose called seq_along()

``` R
my_seq <- seq_along(my_seq)
```

`
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30
`


### Creating a vector that contains 40 zeros

``` R
rep(0, times = 40)
```

`
 [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
`

### Creating a vector which contains several repetitions of another sequence

If for example we want 10 repetitions of the vector (0, 1, 2), we can do

``` R
rep(c(0, 1, 2), times = 10)
```

`
 [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2
`
### Creating a vector which contains numbers repeated a specific amount of times

Let's say that rather than repeating the vector (0, 1, 2) over and over again, we want our vector to contain 10 zeros, 
then 10 ones, then 10 twos. We can do this with the  `each` argument. Try rep(c(0, 1, 2), each = 10).

``` R
rep(c(0, 1, 2), each = 10)
```

`
 [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2
`
