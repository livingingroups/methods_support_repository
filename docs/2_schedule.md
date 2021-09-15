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



```r
people <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Name_table")
support_area <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Expertise_table")

people_support_area <- people %>% 
  left_join(support_area, by = "Name_ID")

schedule <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Schedule_table")

people_support_areas_concatenated <- people_support_area %>% 
  group_by(Name_ID, FirstName, Fixed_or_flexible, If_fixed_when, How_to_contact) %>% 
  summarize(Areas = paste(Support_areas, collapse = ", "))
#> `summarise()` has grouped output by 'Name_ID', 'FirstName', 'Fixed_or_flexible', 'If_fixed_when'. You can override using the `.groups` argument.

schedule_people_areas <- schedule %>% 
  left_join(people_support_areas_concatenated, by = "Name_ID") %>% 
  mutate(Start_date = as.Date(Start_date), End_date = as.Date(End_date))

schedule_people_areas %>% 
  select(Week, Start_date, FirstName, When = If_fixed_when, How_to_contact, Areas)
#> # A tibble: 24 × 6
#>     Week Start_date FirstName  When  How_to_contact Areas                       
#>    <dbl> <date>     <chr>      <lgl> <lgl>          <chr>                       
#>  1    39 2021-09-27 Alie       NA    NA             R programming (base & tidyv…
#>  2    39 2021-09-27 Roi        NA    NA             Data wrangling and visualiz…
#>  3    40 2021-10-04 Tracy      NA    NA             R programming (base & tidyv…
#>  4    40 2021-10-04 Jake       NA    NA             General experimental design…
#>  5    41 2021-10-11 Eli        NA    NA             R, git/github, Data wrangli…
#>  6    41 2021-10-11 Shauhin    NA    NA             R, QGIS, Data manipulation …
#>  7    42 2021-10-18 Mara       NA    NA             R, Python, Data wrangling, …
#>  8    42 2021-10-18 Genevieve  NA    NA             Mostly in R, unless someone…
#>  9    43 2021-10-25 Vivek Hari NA    NA             Python programming; data wr…
#> 10    43 2021-10-25 Urs        NA    NA             R programming, Data wrangli…
#> # … with 14 more rows
```


