
<!-- README.md is generated from README.Rmd. Please edit that file -->

# regexcite

<!-- badges: start -->

<!-- badges: end -->

The goal of regexcite is to …

## Installation

You can install the development version of regexcite from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("pmanoharan-hr/regexcite")
```

## Example

An example when you can use `regexcite::str_split_one()`

``` r
library(regexcite)
## basic example code

x <- "alpha,bravo,charlie,delta"
strsplit(x, split = ",")
#> [[1]]
#> [1] "alpha"   "bravo"   "charlie" "delta"
stringr::str_split(x, pattern = ",")
#> [[1]]
#> [1] "alpha"   "bravo"   "charlie" "delta"
```

Notice how the return value is a **list** of length one, and the first
element has the character vector. This is inconvenient, i.e. we want the
un-listed version which should be just the character vector.

That’s exactly what `regexcite::str_split_one()` does.

``` r
library(regexcite)

str_split_one(x, pattern = ",")
#> [1] "alpha"   "bravo"   "charlie" "delta"
```

Use `str_split_one()` when the input is known to be a single string. For
safety, it will error if its input has length greater than one.

`str_split_one()` is built on `stringr::str_split()`, so you can use its
`n` argument and stringr’s general interface for describing the
`pattern` to be matched.

``` r
str_split_one(x, pattern = ",", n=2)
#> [1] "alpha"               "bravo,charlie,delta"

y <- "192.168.0.1"
str_split_one(y, pattern = stringr::fixed("."))
#> [1] "192" "168" "0"   "1"
```
