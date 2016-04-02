# R development using GitHub
Gábor Csárdi  

# Outline

<style>
  .inverse h1 { color: white; background-color: black; padding: 30px; opacity: 0.7; }
  .grey { opacity: 0.4; }
  h1 emph { color: blue; }
</style>



## 1. Reading code
## 2. Collaboration #1
## 3. Version control & git
## 4. Collaboration #2
## 5. Best practices

<p class="note">Five parts, 30 minutes each, 5 minutes for exercises.

# Goals

## 1. Understand GitHub, start using it
## 2. Understand how git works, what it can do for you
## 3. Have an R package on GitHub, with CI, code coverage, linting
## 4. Make you confident that you can do it again!

# 1. Reading code { .shout }

# The hardest part of programming:<br> Doing things the *right way*

Example: how do you update elements of a named list based on another list?


```r
old <- list(foo = 1, bar = 2)
new <- list(bar = 3, foobar = 10)
```

Want:


```r
list(foo = 1, bar = 3, foobar = 10)
```

How about


```r
old[ names(new) ] <- new
```

# Updating a list

But hey, what if `new` has no names?


```r
old <- list(foo = 1, bar = 2)
new <- list(bar = 3, NULL, foobar = 10)
old[ names(new) ] <- new
old
```

```
## $foo
## [1] 1
## 
## $bar
## [1] 3
## 
## [[3]]
## NULL
## 
## $foobar
## [1] 10
```

# Updating a list

Not good. Need to drop unnamed elements from `new`:


```r
old <- list(foo = 1, bar = 2)
new <- list(bar = 3, NULL, foobar = 10)
good <- names(new) != ""
old[ names(new)[good] ] <- new[good]
old
```

```
## $foo
## [1] 1
## 
## $bar
## [1] 3
## 
## $foobar
## [1] 10
```

# Updating a list

But what if `new` is empty:


```r
old <- list(foo = 1, bar = 2)
new <- list()
good <- names(new) != ""
old[ names(new)[good] ] <- new[good]
old
```

```
## $foo
## [1] 1
## 
## $bar
## [1] 2
```

# Updating a list

> * What if we want to remove when `new` is `NULL`?
> * What if we want it to be recursive?
> * It is not trivial to get it right.

```r
❯ modifyList
function (x, val, keep.null = FALSE)
{
    stopifnot(is.list(x), is.list(val))
    xnames <- names(x)
    vnames <- names(val)
    vnames <- vnames[nzchar(vnames)]
    if (keep.null) {
        for (v in vnames) {
            x[v] <- if (v %in% xnames && is.list(x[[v]]) && ...
                list(modifyList(x[[v]], val[[v]], keep.null ...
...
```

# Sort a data frame? The *correct* solution?

Depends.

```r
dd[with(dd, order(-z, b)), ]
```

```r
library(plyr)
arrange(dd, desc(z), b)
```

```r
library(data.table)
data.table(dd)[order(-z, b)]
```

```r
library(taRifx)
sort(dd, f= ~-z+b)
```

```r
doBy::orderBy(~ - z + b, data = dd)
```

http://stackoverflow.com/questions/1296646

# Reading code

> Programs must be written for people to read, and only incidentally for
> machines to execute.

**Harold Abelson, Structure and Interpretation of Computer Programs**

# Open <emph>Source</emph> { .fullpage .shout }

<img src="source.png" class="cover height grey">

# Reading R code

## R source code, including base packages

https://github.com/wch/r-source

## CRAN packages

https://github.com/cran/*

## BioConductor packages

https://github.com/bioconductor-mirror

## R-Forge packages

https://github.com/rforge


# GitHub UI Parts gaborcsardi/praise

## Files

## README.md

## Commits

## Commit ids

## Browse files at another version

## Diffs

## History of files

## Blaming

## Star

## Watch

# Finding people on GitHub

## Search

# Finding R packages on GitHub

## Base R code wch/r-source

## URLs in CRAN packages

## Search

## CRAN @ GitHub

## Bioc @ GitHub

## Installing packages from GitHub

## Install remotes using itself

## Install repos using remotes

## Dependencies to GitHub packages
