writing_function
================
Tianyou He

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(rvest)
```

    ## 
    ## Attaching package: 'rvest'
    ## 
    ## The following object is masked from 'package:readr':
    ## 
    ##     guess_encoding

``` r
set.seed(1)
```

### Z score function

Z scores subtract the mean and divide by the sd.

``` r
x_vec = rnorm(20, mean = 5, sd = .3)
```

Compute Z scores for `x_vec`

``` r
(x_vec - mean(x_vec))/ sd(x_vec)
```

    ##  [1] -0.894579096 -0.007534108 -1.123622566  1.538189109  0.152185414
    ##  [6] -1.107022329  0.325106999  0.599834216  0.421851526 -0.543016965
    ## [11]  1.446758183  0.218251901 -0.888870682 -2.633686248  1.023162590
    ## [16] -0.257822640 -0.226349080  0.824866429  0.690604708  0.441692638

write a function to do this

``` r
z_score = function(x){
  
  if(!is.numeric(x)){
    stop("Argument should be numbers")
  } else if(length(x)<2){
    stop("You need at least 2 numbers to get z scores")
  }
  
  z = (x - mean(x))/ sd(x)
  z
}
```

check that this works.

``` r
z_score(x = x_vec)
```

    ##  [1] -0.894579096 -0.007534108 -1.123622566  1.538189109  0.152185414
    ##  [6] -1.107022329  0.325106999  0.599834216  0.421851526 -0.543016965
    ## [11]  1.446758183  0.218251901 -0.888870682 -2.633686248  1.023162590
    ## [16] -0.257822640 -0.226349080  0.824866429  0.690604708  0.441692638

keep checking

``` r
z_score(x = 3)
```

    ## Error in z_score(x = 3): You need at least 2 numbers to get z scores

``` r
z_score(c("my", "name","is","jeff"))
```

    ## Error in z_score(c("my", "name", "is", "jeff")): Argument should be numbers

``` r
z_score(c(TRUE,TRUE,FALSE,TRUE))
```

    ## Error in z_score(c(TRUE, TRUE, FALSE, TRUE)): Argument should be numbers

``` r
z_score(iris)
```

    ## Error in z_score(iris): Argument should be numbers
