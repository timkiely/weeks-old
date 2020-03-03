Weeks Old
================

``` r
library(waffle)
library(ggplot2)
library(lubridate)

# What date will I turn 88 years old?
EIGHTY_EIGHT_YEARS_OLD <- ymd("1988 09 24")+years(88)

# How many weeks old am I?
WEEKS_SINCE_BORN <- floor(as.numeric(difftime(Sys.Date(), ymd("1988 09 24"), units = "weeks")))

# How many weeks does an 88 year old live?
TOTAL_WEEKS_90_YEARS <- 52*88

# How many weeks do I have left?
WEEKS_LEFT <- TOTAL_WEEKS_90_YEARS-WEEKS_SINCE_BORN


parts <- c("Weeks Left" = WEEKS_LEFT, "Weeks Lived" = WEEKS_SINCE_BORN)
w1 <- waffle(parts, rows = 52, flip = T, colors = c("darkgrey","black"))+theme(legend.position = "none")
```

``` r
w1
```

![](README_files/figure-gfm/weeks%20old-1.png)<!-- -->
