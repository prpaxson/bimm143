Class7
================
Patrick Paxson
10/22/2019

## R functions revisited

Source my functions from last day

``` r
source("http://tinyurl.com/rescale-R")
```

``` r
grade <- function(scores, print_dropped = TRUE) {
  if (any(is.na(scores)))
  {
    warning("Student is missing a homework assignment")
  }
  scores[is.na(scores)] = 0
  print(paste("Score dropped: ", scores[which.min(scores)]))
  return(mean(scores[-which.min(scores)]))
}


student1 <- c(100, 100, 100, 100, 100, 100, 100, 90)
student2 <- c(100, NA, 90, 90, 90, 90, 97, 80)

print(grade(student1))
```

    ## [1] "Score dropped:  90"
    ## [1] 100

``` r
print(grade(student2))
```

    ## Warning in grade(student2): Student is missing a homework assignment

    ## [1] "Score dropped:  0"
    ## [1] 91

``` r
url <- "https://tinyurl.com/gradeinput"
df <- read.csv(url, row.names=1)
apply(df, 1, grade)
```

    ## [1] "Score dropped:  73"
    ## [1] "Score dropped:  64"
    ## [1] "Score dropped:  69"

    ## Warning in FUN(newX[, i], ...): Student is missing a homework assignment

    ## [1] "Score dropped:  0"
    ## [1] "Score dropped:  75"
    ## [1] "Score dropped:  77"
    ## [1] "Score dropped:  74"
    ## [1] "Score dropped:  76"
    ## [1] "Score dropped:  77"

    ## Warning in FUN(newX[, i], ...): Student is missing a homework assignment

    ## [1] "Score dropped:  0"
    ## [1] "Score dropped:  66"
    ## [1] "Score dropped:  70"
    ## [1] "Score dropped:  76"
    ## [1] "Score dropped:  76"

    ## Warning in FUN(newX[, i], ...): Student is missing a homework assignment

    ## [1] "Score dropped:  0"
    ## [1] "Score dropped:  74"
    ## [1] "Score dropped:  63"

    ## Warning in FUN(newX[, i], ...): Student is missing a homework assignment

    ## [1] "Score dropped:  0"
    ## [1] "Score dropped:  68"
    ## [1] "Score dropped:  68"

    ##  student-1  student-2  student-3  student-4  student-5  student-6  student-7 
    ##      91.75      82.50      84.25      84.25      88.25      89.00      94.00 
    ##  student-8  student-9 student-10 student-11 student-12 student-13 student-14 
    ##      93.75      87.75      79.00      86.00      91.75      92.25      87.75 
    ## student-15 student-16 student-17 student-18 student-19 student-20 
    ##      78.75      89.50      88.00      94.50      82.75      82.75
