# Dates

Dates are represented by the 'Date' class and times are represented by the 'POSIXct' and 'POSIXlt' classes. 
Internally, dates are stored as the number of days since 1970-01-01 and times are stored as either the number of seconds 
since 1970-01-01 (for 'POSIXct') or a list of seconds, minutes, hours, etc. (for 'POSIXlt').

``` R
d1 <- Sys.Date()
class(d1)
```

`
[1] "Date"
`

Use the **unclass()** function to see what d1 looks like internally.

``` R
unclass(d1)
```

`
[1] 17819
`

That's the exact number of days since 1970-01-01!

If you print d1 to the console, you'll get today's date.

``` R
d1
```

`
[1] "2018-10-15"
`

What if we need to reference a date prior to 1970-01-01?

``` R
d2 <- as.Date("1969-01-01")
unclass(d2)
```

`
[1] -365
`

### Sys.time()

To **access the current date and time**  

``` R
t1 <- Sys.time()
t1
```

`
[1] "2018-10-15 16:10:17 +03"
`

``` R
class(t1)
```

`
[1] "POSIXct" "POSIXt" 
`

By default, Sys.time() returns an object of class POSIXct, but we can coerce the result to POSIXlt with as.POSIXlt(Sys.time())

``` R
t2 <- as.POSIXlt(Sys.time()
```

A POSIXlt objects  is just a list of values that make up the date and time. Use str(unclass(t2)) to have a more compact view.

``` R
str(unclass(t2))
```

`
List of 11
 $ sec   : num 35.5
 $ min   : int 12
 $ hour  : int 16
 $ mday  : int 15
 $ mon   : int 9
 $ year  : int 118
 $ wday  : int 1
 $ yday  : int 287
 $ isdst : int 0
 $ zone  : chr "+03"
 $ gmtoff: int 10800
 - attr(*, "tzone")= chr [1:3] "" "+03" "   "
`

If we want just the minutes from the time stored in t2, we can access them with:

``` R
t2$min
```

`
[1] 12
`

### weekdays(), months(), and quarters()

Functions that extract useful information from any of these objects: weekdays(), months(), and quarters()
The weekdays() function will return the day of week from any date or time object

``` R
weekdays(t1)
```

`
[1] "Monday"
`

strptime() converts character vectors to POSIXlt. In that sense, it is similar to as.POSIXlt(), except that the input 
doesn't have to be in a particular format (YYYY-MM-DD). For example:

``` R
t3 <- "October 17, 1986 08:24"
t4 <- strptime(t3, "%B %d, %Y %H:%M")
```

`
[1] "1986-10-17 08:24:00 +03"
`

``` R
class(t4)
```

`
[1] "POSIXlt" "POSIXt" 
`

Some arithmetic operations on Time variables:

``` R
Sys.time() - t1
```

Time difference of 18.96835 mins

### difftime()

To find the amount of time in DAYS that has passed since you created t1 you can use:

``` R
difftime(Sys.time(), t1, units = 'days')
```

`
[1] 0.01403285
`
