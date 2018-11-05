Sequences of Numbers
 

The simplest way to create a sequence of numbers in R is by using the `:` operator. Type
1:20 to see how it works.
> 1:20
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20

That gave us every integer between (and including) 1 and 20. We could also use it to create
a sequence of real numbers. For example, try pi:10.  The result is a vector of real numbers starting 
with pi (3.142...) and increasing in increments of 1. The upper limit of 10 is never reached, since the
next number in our sequence would be greater than 10.
> pi:10
[1] 3.141593 4.141593 5.141593 6.141593 7.141593 8.141593 9.141593

The most basic use of seq() does exactly the same thing as the `:` operator. Try seq(1, 20) to see this.
seq(1,20)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20

 Let's say that instead we want a vector of numbers ranging from 0 to 10, incremented by 0.5.

seq(0,10, by=0.5)
 [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0  7.5  8.0  8.5
[19]  9.0  9.5 10.0

If we don't care what the increment is and we just want a sequence of 30 numbers
between 5 and 10. seq(5, 10, length=30) does the trick. Give it a shot now and store the
result in a new variable called my_seq.
> my_seq <- seq(5,10, length=30)

Another option:

seq(along.with = my_seq)

R has a separate built-in function for this purpose called seq_along()

seq_along(my_seq)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

If we're interested in creating a vector that contains 40 zeros, we can use rep(0, times =
40). Try it out.
> rep(0, times = 40)
 [1] 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0


If instead we want our vector to contain 10 repetitions of the vector (0, 1, 2), we can do
rep(c(0, 1, 2), times = 10). Go ahead.
> rep(c(0, 1, 2), times = 10)
 [1] 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2 0 1 2

Let's say that rather than repeating the vector (0, 1, 2) over and over again, we want our vector to contain 10 zeros, 
then 10 ones, then 10 twos. We can do this with the  `each` argument. Try rep(c(0, 1, 2), each = 10).
> rep(c(0, 1, 2), each = 10)
 [1] 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 2 2 2 2 2
