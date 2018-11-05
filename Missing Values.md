# Missing Values

Lets create a vector containing 1000 draws from a standard normal distribution

``` R
y <- rnorm(1000)
```

Now we create a vector containing 1000 NAs with

``` R
z <- rep(NA, 1000)
```

Next step is to select 100 elements at random from these 2000 values (combining y and z). This means that initially we don't know how many
 NAs we'll wind up with or what positions they'll occupy in our final vector

``` R
my_data <- sample(c(y,z),100)
```

Now we want to know where our NAs are located in our data. The is.na() function tells us whether each element of a vector is NA. 

``` R
my_na <- is.na(my_data)
```

If you print the result, everywhere you see a TRUE, you know the corresponding element of my_data is NA. Likewise,
 everywhere you see a FALSE, you know the corresponding element of my_data is one of our random draws from the standard normal distribution.

### Calculating the number of nulls

``` R
sum(my_na)
````

`
[1] 52
`

NaN stands for 'not a number'. To generate NaN, try dividing  0/0
