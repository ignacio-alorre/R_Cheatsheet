# Looking at data

### class()

You have a file, let's start by checking it's class:

``` R
class(plants)
```

`
[1] "data.frame"
`

### dim()

Since the dataset is stored in a data frame, we know it is rectangular. That is, it has two dimensions (rows and columns) and fits 
neatly into a table or spreadsheet. We can check now its dimensions:

``` R
dim(plants)
```

`
[1] 5166   10
`

The first number you see (5166) is the number of rows (observations) and the second number (10) is the number of columns (variables).

### nrow() amd ncol()

You can use nrow(plants) to see only the number of rows.

``` R
nrow(plants)
```

`
[1] 5166
`

You can use ncol(plants) to see only the number of columns

``` R
ncol(plants)
```

`
[1] 10
`

### object.size()

If you are curious as to how much space the dataset is occupying in memory, you can use object.size(plants).

``` R
object.size(plants)
```

`
686080 bytes
`

### names()

With names(plants) will return a character vector of column (i.e. variable) names.

``` R
names(plants)
```

`
 [1] "Scientific_Name"      "Duration"             "Active_Growth_Period"
 [4] "Foliage_Color"        "pH_Min"               "pH_Max"              
 [7] "Precip_Min"           "Precip_Max"           "Shade_Tolerance"     
[10] "Temp_Min_F"  
`

### head() 

head() shows you the first six rows of the data. You can alter this behavior by passing as a second argument the number of rows 
you'd like to view. The same applies for using tail() to preview the end of the dataset

``` R
head(plants,10)
```

### summary()

Use summary(plants) to get a better feel for how each variable is distributed and how much of the dataset is missing.

summary() provides different output for each variable, depending on its class. For numeric data such as Precip_Min, 
summary() displays the minimum, 1st quartile, median, mean, 3rd quartile, and maximum. These values help us understand how 
the data are distributed. For categorical variables (called 'factor' variables in R), summary() displays the number of 
times each value (or 'level') occurs in the data. For example, each value of Scientific_Name only appears once, since it 
is unique to a specific plant. In contrast, the summary for Duration (also a factor variable) tells us that our dataset 
contains 3031 Perennial plants, 682 Annual plants, etc.


You can see that R truncated the summary for Active_Growth_Period by including a catch-all category called 'Other'. Since it is 
a categorical/factor variable, we can see how many times each value actually occurs in the data with 

``` R
table(plants$Active_Growth_Period).
```

### str()

Combines many of the features for visualization, all in a concise and readable format. At the very top, it tells us that 
the class of plants is 'data.frame' and that it has 5166 observations and 10 variables. It then gives us the name and class 
of each variable, as well as a preview of its contents.

``` R
str(plants)
```

`
'data.frame':	5166 obs. of  10 variables:
 $ Scientific_Name     : Factor w/ 5166 levels "Abelmoschus",..: 1 2 3 4 5 6 7 8 9 10 ...
 $ Duration                  : Factor w/ 8 levels "Annual","Annual, Biennial",..: NA 4 NA 7 7 NA 1 NA 7 7 ...
 $ Active_Growth_Period: Factor w/ 8 levels "Fall, Winter and Spring",..: NA NA NA 4 NA NA NA NA 4 NA ...
 $ Foliage_Color       : Factor w/ 6 levels "Dark Green","Gray-Green",..: NA NA NA 3 NA NA NA NA 3 NA ...
 $ pH_Min              : num  NA NA NA 4 NA NA NA NA 7 NA ...
 $ pH_Max              : num  NA NA NA 6 NA NA NA NA 8.5 NA ...
 $ Precip_Min          : int  NA NA NA 13 NA NA NA NA 4 NA ...
 $ Precip_Max          : int  NA NA NA 60 NA NA NA NA 20 NA ...
 $ Shade_Tolerance     : Factor w/ 3 levels "Intermediate",..: NA NA NA 3 NA NA NA NA 2 NA ...
 $ Temp_Min_F          : int  NA NA NA -43 NA NA NA NA -13 NA ...
`


### plot() 

plot(cars)

The help page for plot() highlights the different arguments that the function can take. The two most important are x and y, 
the variables that will be plotted. For the next set of questions, include the argument names in your answers. That is, do 
not type `plot(cars$speed, cars$dist)`, although that will work. Instead, use `plot(x = cars$speed, y = cars$dist)`.

In case you want to indicate the axis and the lables:

``` R
plot(x = cars$speed, y = cars$dist, xlab = "Speed", ylab = "Stopping Distance"
```

To add title and subtitle

``` R
plot(cars, main = "My Plot")
plot(cars, sub = "My Plot Subtitle")
```

Plot cars so that the plotted points are colored red.

``` R
plot(cars, col = 2)
```

Plot cars while limiting the x-axis to 10 through 15

``` R
plot(cars, xlim = c(10, 15))
```

Plot cars using triangles.

``` R
plot(cars, pch = 2)
```

boxplot(), like many R functions, also takes a "formula" argument, generally an expression with a tilde ("~") which indicates the relationship between the input variables. This allows you to enter something like mpg ~ cyl to plot the relationship between cyl (number of cylinders) on the x-axis and mpg (miles per gallon) on the y-axis.

boxplot(formula = mpg ~ cyl, data = mtcars)

When looking at a single variable, histograms are a useful tool. hist() is the associated R function. Like plot(), hist() is best used by just passing in a single vector.

hist(mtcars$mpg)

