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
  mean(pull(first_df, random_sample)) #mean of random sample
```

    ## [1] -0.08440639

``` r
  mean(pull(first_df, vec_logical)) #mean of logical variable
```

    ## [1] 0.375

``` r
  mean(pull(first_df, vec_char))  #mean of char variable
```

    ## Warning in mean.default(pull(first_df, vec_char)): argument is not numeric
    ## or logical: returning NA

    ## [1] NA

``` r
  mean(pull(first_df, vec_factor)) #mean of factor variable
```

    ## Warning in mean.default(pull(first_df, vec_factor)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

As can be seen from the results, taking the mean of the random sample or
the logical vector works, but taking the mean of the character vector or
the factor vector doesn’t work.

Now let us try explicitly convert variables from one type to another.

``` r
  as.numeric(pull(first_df, vec_logical)) #convert to numeric
  as.numeric(pull(first_df, vec_char))    
  as.numeric(pull(first_df, vec_factor))  
```

Converting the logical variable to numeric type, we get 0s and 1s. The
reason is that logical variables only two type of values: TRUE or FALSE.
0s and 1s are enough to represent the values.

Converting the character variable to numeric type does not work and we
get NAs which stand for missing values. The reason is that character
vector stores character values whose encodings are fundamentally
different from those of numeric values.

Converting the factor variable to numeric type, we get 1s, 2s and 3. The
reason is that factor variables give numeric encodings to non-numeric
variables and represent them by countable levels which can be rendered
by numbers. The factor variable we created contain three dinstinct
levels, which is why we get 1s, 2s and 3s.

This helps explain what happened when I tried to take the mean. If a
variable cannot be or has not been converted into numeric type, it
cannot have a mean as mean in essence is a numeric value.

Since a character vector cannot be converted to numeric type, taking its
mean does not make sense.

Since the factor variable was not converted before taking its mean,
missing values were returned.

However, logical values are always binary which means they can always be
represented by 0s and 1s. Therefore, its mean can be calculated
numerically without conversions.
