# Workspace and Files

### Determine which directory your R session is using as its current working directory

```R
getwd()
```

### List all the objects in your local workspace using ls().

```R
ls()
```
`
"my_div"  "my_sqrt" "x"
`

### List all the files in your working directory using list.files() or dir()

```R
list.files()
```

### Use the args() function to determine the arguments of a function

```R
args(list.files)
```

`
function (path = ".", pattern = NULL, all.files = FALSE, full.names = FALSE, 
    recursive = FALSE, ignore.case = FALSE, include.dirs = FALSE, 
    no.. = FALSE) 
NULL
`

### Saveing your current working directory into a variable

```R
old.dir <- getwd()
```

It is often helpful to save the settings that you had before you began an analysis and then
go back to them at the end. This trick is often used within functions; you save, say, the
par() settings that you started with, mess around a bunch, and then set them back to the
original values at the end. This isn't the same as what we have done here, but it seems
similar enough to mention.

### Creating a directory in the current working directory

``` R
dir.create("testdir")
```

### Setting a new working directory

``` R
setwd("testdir")
```

### Creating a file in your working directory

```R
file.create("mytest.R")
```

## Checking if a file exists in the working directory

```R
file.exists("mytest.R")
```

`
[1] TRUE
`

### Access information a file's information

``` R
file.info("mytest.R")
```
`
         size isdir mode               mtime               ctime               atime exe
mytest.R    0 FALSE  666 2018-10-11 10:22:34 2018-10-11 10:22:34 2018-10-11 10:22:34  no
`

### Changing the name of a file

``` R
file.rename("mytest.R","mytest2.R")
```

### Making a copy of a file

``` R
file.copy("mytest2.R","mytest3.R")
```
`
[1] TRUE
`

### Provide the relative path to a file

```R
file.path("mytest3.R")
```

`
[1] "mytest3.R"
`

### Constructing paths (file + directory) independent of the Operating System

For example Pass 'folder1' and 'folder2' as arguments to file.path to make a platform-independent pathname.

```R
file.path("folder1","folder2")
```

`
[1] "folder1/folder2"
`

### Creating a directory in the current sd and a subdirectory in one command

``` R
dir.create(file.path("testdir2","testdir3"),recursive = TRUE)
```
