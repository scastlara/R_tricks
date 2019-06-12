Condition on multiple columns
================

Load libraries
--------------

``` r
library(dplyr)
```

Apply condition
---------------

This will apply a given condition `< 0.3` on the columns `2,3,4` of `iris` and, if **any** column (`> 0`) passes the condition, `has_below_val` will be set to `TRUE`, otherwise it will be `FALSE`. Customize as needed.

``` r
iris <- as_tibble(iris)
iris %>% mutate(
  has_below_val = ifelse(
    rowSums(iris[2:4] < 0.3) > 0, 
    T, 
    F
  )
)
```

    ## # A tibble: 150 x 6
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species has_below_val
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>   <lgl>        
    ##  1          5.1         3.5          1.4         0.2 setosa  TRUE         
    ##  2          4.9         3            1.4         0.2 setosa  TRUE         
    ##  3          4.7         3.2          1.3         0.2 setosa  TRUE         
    ##  4          4.6         3.1          1.5         0.2 setosa  TRUE         
    ##  5          5           3.6          1.4         0.2 setosa  TRUE         
    ##  6          5.4         3.9          1.7         0.4 setosa  FALSE        
    ##  7          4.6         3.4          1.4         0.3 setosa  FALSE        
    ##  8          5           3.4          1.5         0.2 setosa  TRUE         
    ##  9          4.4         2.9          1.4         0.2 setosa  TRUE         
    ## 10          4.9         3.1          1.5         0.1 setosa  TRUE         
    ## # ... with 140 more rows
