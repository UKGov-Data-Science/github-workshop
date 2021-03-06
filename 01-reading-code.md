# R development using GitHub
Gábor Csárdi  

# Outline



## 1. Reading code
## 2. Collaboration #1
## 3. Collaboration #2
## 4. Version control & git
## 5. Best practices, CI
## 6. GitHub Pages

<p class="note">Six parts, 20 minutes each, 5 minutes for exercises.

# Goals

## 1. Understand GitHub, start using it
## 2. Understand how git works, what it can do for you
## 3. Have an R package on GitHub, with CI, code coverage
## 4. Set up a GitHub page for your package
## 5. Make you confident that you can do it again!

# 1. Reading code { .shout }

# The hardest part of coding: the *right way*

Sort a data frame? *correct* solution? Depends.

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

<img src="images/source.png" class="cover height grey">

# The GitHub UI { .fullpage .shout }

<p class="subtitle"> https://github.com/gaborcsardi/praise </p>

# { .fullpage }
<img src="images/praise.png" class="cover gh">
<p class="subtitle subtitletop">Files</p>

# { .fullpage }
<img src="images/praise-files.png" class="cover gh">
<p class="subtitle subtitletop">Files</p>

# { .fullpage }
<img src="images/praise-readme.png" class="cover gh">
<p class="subtitle subtitletop">README.md</p>

# { .fullpage }
<img src="images/praise-commits.png" class="cover gh">
<p class="subtitle subtitletop">Commits</p>

# { .fullpage }
<img src="images/praise-commit-ids.png" class="cover gh">
<p class="subtitle subtitletop">Commit ids</p>

# { .fullpage }
<img src="images/praise-browse-1.png" class="cover gh">
<p class="subtitle subtitletop">Browse files at another version</p>

# { .fullpage }
<img src="images/praise-browse-2.png" class="cover gh">
<p class="subtitle subtitletop">Browse files at another version</p>

# { .fullpage }
<img src="images/praise-diff-1.png" class="cover gh">
<p class="subtitle subtitletop">Diffs</p>

# { .fullpage }
<img src="images/praise-diff-2.png" class="cover gh">
<p class="subtitle subtitletop">Diffs</p>

# { .fullpage }
<img src="images/praise-history-1.png" class="cover gh">
<p class="subtitle subtitletop">History of files</p>

# { .fullpage }
<img src="images/praise-history-2.png" class="cover gh">
<p class="subtitle subtitletop">History of files</p>

# { .fullpage }
<img src="images/praise-blame-1.png" class="cover gh">
<p class="subtitle subtitletop">Blame</p>

# { .fullpage }
<img src="images/praise-blame-2.png" class="cover gh">
<p class="subtitle subtitletop">Blame</p>

# { .fullpage }
<img src="images/praise-star.png" class="cover gh">
<p class="subtitle subtitletop">Star</p>

# { .fullpage }
<img src="images/praise-star-2.png" class="cover gh">
<p class="subtitle subtitletop">Star</p>

# { .fullpage }
<img src="images/praise-star-3.png" class="cover gh">
<p class="subtitle subtitletop">Star</p>

# { .fullpage }
<img src="images/praise-search.png" class="cover gh">
<p class="subtitle subtitletop">Search: find users</p>

# { .fullpage }
<img src="images/praise-search-2.png" class="cover gh">
<p class="subtitle subtitletop">Search: within repository</p>

# { .fullpage }
<img src="images/praise-search-3.png" class="cover gh">
<p class="subtitle subtitletop">Search: all R code</p>

# { .fullpage }
<img src="images/praise-search-4.png" class="cover gh">
<p class="subtitle subtitletop">Search: all CRAN packages</p>

# Reading R code

## R source code, including base packages

https://github.com/wch/r-source

## CRAN packages

https://github.com/cran/*

## BioConductor packages

https://github.com/bioconductor-mirror

## R-Forge packages

https://github.com/rforge

# Installing packages from GitHub

```r
remotes::install_github("gaborcsardi/praise")
```

```
Downloading GitHub repo gaborcsardi/praise@master
Installing package into '/Users/gaborcsardi/r_pkgs'
(as 'lib' is unspecified)
* installing *source* package 'praise' ...
** R
** inst
** preparing package for lazy loading
** help
*** installing help indices
** building package indices
** testing if installed package can be loaded
* DONE (praise)
```


```r
praise::praise()
```

```
## [1] "You are pioneering!"
```

# Install remotes using itself

## https://github.com/mangothecat/remotes#readme

```r
base <- "https://raw.githubusercontent.com/"
repo <- "MangoTheCat/remotes/"
file <- "master/install-github.R"
url <- paste0(base, repo, file)
source(url)$value("mangothecat/remotes")
```

```
Downloading GitHub repo mangothecat/remotes@master
Installing package into '/Users/gaborcsardi/r_pkgs'
(as 'lib' is unspecified)
* installing *source* package 'remotes' ...
** R
** inst
** preparing package for lazy loading
** help
*** installing help indices
** building package indices
** testing if installed package can be loaded
* DONE (remotes)
```

# Dependencies to GitHub packages

## Use the `Remotes` field in `DESCRIPTION`

```
...
Suggests:
    testthat
Imports:
    description,
    rcmdcheck
Remotes:
    metacran/description,
    mangothecat/rcmdcheck
...
```

```
> remotes::install_github("mangothecat/goodPractice")
Downloading GitHub repo mangothecat/goodPractice@master
Downloading GitHub repo metacran/description@master
...
```

# Exercises

## 1. Find your favorite R developer on GitHub.

## 2. Find your favorite R package on GitHub.

## 3. Star it.

## 4. Look at the commit history.

## 5. Find out when it was last updated.

## 6. Find out who updated it.

## 7. Find out what changed.

## 8. Install your favorite R package using `remotes`.
