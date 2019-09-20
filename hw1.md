p8105\_hw1\_ml4420
================
Mengjia Lyu
2019-09-13

## Data Science Homework 1

``` r
library(formattable)
library(tidyverse) #loading libraries
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   0.8.3     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
first_df = tibble(   #first data frame
  random_sample = rnorm(n = 8),
  vec_logical   = random_sample > 0,
  vec_char      = c("this", "is", "a", "character", "vector", "of", "length", "eight"),
  vec_factor    = factor(c("small", "medium", "large", "small", "medium", "large", "small", "medium")),
 )
```

Now let us try to take the mean of each variable in the data
    frame.

``` r
  mean(pull(first_df, random_sample)) #take the mean
```

    ## [1] -0.06138473

``` r
  mean(pull(first_df, vec_logical))
```

    ## [1] 0.25

``` r
  mean(pull(first_df, vec_char))
```

    ## Warning in mean.default(pull(first_df, vec_char)): argument is not numeric
    ## or logical: returning NA

    ## [1] NA

``` r
  mean(pull(first_df, vec_factor))
```

    ## Warning in mean.default(pull(first_df, vec_factor)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

As can be seen from the results, taking the mean of the random sample or
the logical vector works, but taking the mean of the character vector or
the factor vector doesn’t work.
