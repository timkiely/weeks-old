Weeks Old
================

Last updated: 2020-03-03

``` r
lifespan_plot <- function(BIRTHDAY = NULL, lifespan = 88, extra_motivation = FALSE){
  
  suppressPackageStartupMessages({
    require(waffle)
    require(ggplot2)
    require(lubridate)
  })
  
  if(!is.Date(BIRTHDAY)) stop("Must supply a valid date")
  if(BIRTHDAY>Sys.Date()) stop("Birthdate supplied is after today")
  
  
  
  # What date will you reach your lifespan?
  LIFESPAN_DATE <- BIRTHDAY+years(lifespan)
  
  # How many weeks old are you?
  WEEKS_SINCE_BORN <- floor(as.numeric(difftime(Sys.Date(), BIRTHDAY, units = "weeks")))
  
  # How many weeks does an 88 year old live?
  TOTAL_WEEKS_LIFESPAN <- 52*lifespan
  
  # How many weeks do I have left?
  WEEKS_LEFT <- TOTAL_WEEKS_LIFESPAN-WEEKS_SINCE_BORN
  
  
  parts <- c("Weeks Left" = WEEKS_LEFT, "Weeks Lived" = WEEKS_SINCE_BORN)
  lifespan_plot <- waffle(parts, rows = 52, flip = T, colors = c("darkgrey","black"))+theme(legend.position = "none")
  
  if(extra_motivation) {
    
    if(lifespan%/%10==8){
      motivation_text <- 
        paste0("You are "
               , scales::percent(WEEKS_SINCE_BORN/TOTAL_WEEKS_LIFESPAN)
               ," through an ",lifespan
               , " year life")
    } else {
      
      motivation_text <- 
        paste0("You are "
               , scales::percent(WEEKS_SINCE_BORN/TOTAL_WEEKS_LIFESPAN)
               ," through a ",lifespan
               , " year life")
    }
    
    lifespan_plot <- lifespan_plot+labs(title = motivation_text)
  }
  lifespan_plot
}
```

``` r
BIRTHDAY <- lubridate::ymd("1988 09 24")

lifespan_plot(BIRTHDAY)
```

![](README_files/figure-gfm/weeks%20old-1.png)<!-- -->

``` r
BIRTHDAY <- lubridate::ymd("1988 09 24")

lifespan_plot(BIRTHDAY, lifespan = 88, extra_motivation = TRUE)
```

![](README_files/figure-gfm/extra%20motivation-1.png)<!-- -->
