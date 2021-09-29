---
output: html_document
editor_options:
  chunk_output_type: console
---
# Schedule



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
library(knitr)
```



```r
people <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Name_table")

schedule <- readxl::read_excel(here::here("data/Info_on_people.xlsx"),
                   sheet = "Schedule_table")

schedule_people <- schedule %>% 
  left_join(people, by = "Name_ID") %>% 
  mutate(Start_date = as.Date(Start_date), End_date = as.Date(End_date))

schedule_people %>% 
  select(Week, Week_start = Start_date, Week_end = End_date,
         FirstName, When = If_fixed_when, How_to_contact) %>% 
  kable()
```



| Week|Week_start |Week_end   |FirstName  |When |How_to_contact |
|----:|:----------|:----------|:----------|:----|:--------------|
|   39|2021-09-27 |2021-10-01 |Alie       |NA   |NA             |
|   39|2021-09-27 |2021-10-01 |Roi        |NA   |NA             |
|   40|2021-10-04 |2021-10-08 |Tracy      |NA   |NA             |
|   40|2021-10-04 |2021-10-08 |Jake       |NA   |NA             |
|   41|2021-10-11 |2021-10-15 |Eli        |NA   |NA             |
|   41|2021-10-11 |2021-10-15 |Shauhin    |NA   |NA             |
|   42|2021-10-18 |2021-10-22 |Mara       |NA   |NA             |
|   42|2021-10-18 |2021-10-22 |Genevieve  |NA   |NA             |
|   43|2021-10-25 |2021-10-29 |Vivek Hari |NA   |NA             |
|   43|2021-10-25 |2021-10-29 |Urs        |NA   |NA             |
|   44|2021-11-01 |2021-11-05 |Alie       |NA   |NA             |
|   44|2021-11-01 |2021-11-05 |Roi        |NA   |NA             |
|   45|2021-11-08 |2021-11-12 |Tracy      |NA   |NA             |
|   45|2021-11-08 |2021-11-12 |Jake       |NA   |NA             |
|   46|2021-11-15 |2021-11-19 |Eli        |NA   |NA             |
|   46|2021-11-15 |2021-11-19 |Shauhin    |NA   |NA             |
|   47|2021-11-22 |2021-11-26 |Mara       |NA   |NA             |
|   47|2021-11-22 |2021-11-26 |Genevieve  |NA   |NA             |
|   48|2021-11-29 |2021-12-03 |Vivek Hari |NA   |NA             |
|   48|2021-11-29 |2021-12-03 |Urs        |NA   |NA             |
|   49|2021-12-06 |2021-12-10 |Alie       |NA   |NA             |
|   49|2021-12-06 |2021-12-10 |Roi        |NA   |NA             |
|   50|2021-12-13 |2021-12-17 |Tracy      |NA   |NA             |
|   50|2021-12-13 |2021-12-17 |Jake       |NA   |NA             |


