# Matrices and Dataframes

Matrices and data frames represent 'rectangular' data types, meaning that they are used to store tabular data, with rows and columns.

* **matrices can only contain a single class of data**
* **data frames can consist of many different classes of data**

### Finding the length of a vector 

``` R
length(my_vector)
```

### Giving a flat vector the `dim` attribute 

``` R
dim(my_vector) <- c(4,5)
```

### Displaying the attributes of a vector

``` R
attributes(my_vector)   
dim(my_vector)
```

`
$`dim`
[1] 4 5
`

Print out the vector

``` R
my_vector
```

`
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    5    9   13   17
[2,]    2    6   10   14   18
[3,]    3    7   11   15   19
[4,]    4    8   12   16   20
`

We can see it is now a matrix

``` R
class(my_vector)
```

`
[1] "matrix"
`

The example that we've used so far was meant to illustrate the point that a matrix is simply an atomic vector with a 
dimension attribute. A more direct method of creating the same matrix uses the matrix() function.

### Creating a Matrix

Create a matrix containing the same numbers (1-20) and dimensions (4 rows, 5 columns)

``` R
my_matrix2 <- matrix(1:20,4,5)
```

### Creating a Vector of names

``` R
patients <- c("Bill", "Gina", "Kelly", "Sean")
```

### Combining a vector and a matrix 

With cbind() the vector will become a new column of the matrix

``` R
cbind(patients,my_matrix)
```

`
     patients                       
[1,] "Bill"   "1" "5" "9"  "13" "17"
[2,] "Gina"   "2" "6" "10" "14" "18"
[3,] "Kelly"  "3" "7" "11" "15" "19"
[4,] "Sean"   "4" "8" "12" "16" "20"
`

**Note:**
Combining the character vector with our matrix of numbers caused everything to be enclosed in double quotes. This means we're left
with a matrix of character strings. This is because matrices can only contain ONE class of data. Therefore, **when we tried to combine a 
character vector with a numeric matrix, R was forced to 'coerce' the numbers to characters**, hence the double quotes.
This is called **'implicit coercion'**, because we didn't ask for it. 

To avoid it what we need is to create a dataframe for 


### Creating a Dataframe

``` R
my_data <- data.frame(patients, my_matrix)
```

Behind the scenes, the data.frame() function takes any number of arguments and returns a single object of class `data.frame` that is 
composed of the original objects.

```R
class(my_data)
```

`
[1] "data.frame"
`

### Assigning names to infividual rows and columns in a dataframe

Since we have six columns (including patient names), we'll need to first create a vector containing one element for each column. 
Create a character vector called cnames that contains the following values (in order): "patient", "age", "weight", "bp", "rating", 
"test".

``` R
cnames <- c("patient", "age", "weight", "bp", "rating","test")
colnames(my_data) <- cnames
```
