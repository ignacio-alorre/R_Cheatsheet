# Simulation

### sample

Randomly select a subsample from a vector. It is possible to make a Sampling with replacement, which simply means that each 
number is "replaced" after it is selected, so that the same number can show up more than once. For example:

``` R
sample(1:6, 4, replace = TRUE)
```

`
[1] 4 3 3 6
`

When the 'size' argument to sample() is not specified, R takes a sample equal in size to the vector from which you are sampling.

Now, suppose we want to simulate 100 flips of an unfair two-sided coin. This particular coin has a 0.3 probability of landing 'tails' 
and a 0.7 probability of landing 'heads'.

``` R
flips <- sample(c(0,1), 100, replace = TRUE, prob = c(0.3, 0.7))
```

### binomial random variable rbinom()

A binomial random variable represents the number of 'successes' (heads) in a given number of independent 'trials' 
(coin flips) We can generate a single random variable that represents the number of heads in 100 flips of our unfair coin 
using:


``` R
rbinom(1, size = 100, prob = 0.7)
```

`
[1] 62
`

**Note** that you only specify the probability of 'success' (heads) and NOT the probability of 'failure' (tails)

### random standar normal distribution rnorm

The standard normal distribution has mean 0 and standard deviation 1. As you can see under the 'Usage' section in the documentation, 
the default values for the 'mean' and 'sd' arguments to rnorm() are 0 and 1, respectively.

``` R
rnorm(10) 
```

will generate 10 random numbers from a standard normal distribution. If you want to use instead a mean of 100 and a standard 
deviation of 25.

``` R
rnorm(10, mean = 100, sd = 25)
```

### random poissons distribution

If we want to simulate 100 *groups* of random numbers, each containing 5 values generated from a Poisson distribution with mean 10:

``` R
my_pois <- replicate(100, rpois(5, 10))
```

replicate() created a matrix, each column of which contains 5 random numbers generated from a Poisson distribution with mean 10. 
Now we can find the mean of each column in my_pois using the colMeans() function.

``` R
colMeans(my_pois)
```
