---
output: html_document
editor_options:
  chunk_output_type: console
---
# Template Script



```r
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
```


Here is a list with all people interested in providing support including their areas in which they can provide support.


```r
people <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Name_table")
support_area <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Expertise_table")

people_support_area <- people %>% 
  left_join(support_area, by = "Name_ID")

people_support_area %>% 
  select(Name = FirstName, Fixed_or_flexible, If_fixed_when, Support_areas)
#> # A tibble: 78 × 4
#>    Name  Fixed_or_flexible If_fixed_when Support_areas                          
#>    <chr> <chr>             <lgl>         <chr>                                  
#>  1 Alie  fixed             NA            R programming (base & tidyverse)       
#>  2 Alie  fixed             NA            Data wrangling                         
#>  3 Alie  fixed             NA            Data visualization (including mapping)…
#>  4 Alie  fixed             NA            Basic frequentist stats (parametric an…
#>  5 Alie  fixed             NA            General and generalized linear (mixed)…
#>  6 Alie  fixed             NA            Basic movement analysis (calculating h…
#>  7 Urs   fixed             NA            R programming                          
#>  8 Urs   fixed             NA            Data wrangling and visualizations      
#>  9 Urs   fixed             NA            Working with spatial data (to a certai…
#> 10 Urs   fixed             NA            Fitting linear models from LMs to GLMM…
#> # … with 68 more rows
```

