---
title: "Methods Support Program"
subtitle: "Webpage to organize and advertise this program"
author: "Various people"
date: "2022-05-24"
documentclass: book
bibliography: [book.bib]
biblio-style: apalike
link-citations: yes
github-repo: livingingroups/methods_support_repository
description: "Webpage to organize and advertise the Methods Support Program at the EAS department/MPI-AB"
editor_options: 
  chunk_output_type: console
---






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
library(flextable)
#> Warning: package 'flextable' was built under R version 4.0.5
```


```r
people <- read.csv(here::here("data/Name_table.csv"))
support_area <- read.csv(here::here("data/Expertise_table.csv"))
schedule <- read.csv(here::here("data/Schedule_table.csv"))

today <- as.Date(Sys.time())
current_week_people_support_area <- schedule %>% 
  left_join(people, by = "Name_ID") %>% 
  left_join(support_area, by = "Name_ID") %>% 
  mutate(Start_date = as.Date(Start_date, format = c("%d.%m.%y")),
         End_date = as.Date(End_date, format = c("%d.%m.%y"))) %>% 
  filter(today > Start_date & today < End_date)
```

# Introduction

The goal of the “Methods Support Program” is to connect students in need of methodological assistance with more experienced researchers who can help. 

By posting the skillsets and availability of more-senior people in the department who are keen to provide support, students can select and reach out to a potential helper. Ideally, this makes it easier for students to get the support they need, and also distributes helping responsibilities across experience department members. While the focus of this program is on data wrangling and analysis, it can extend to other aspects of methodology – such as experimental design, choosing and using GPS collars and audio recorders, etc.

If you are looking for methods help, consult the [overview of people in the department who are offering their support][Overview]. Choose somebody whose area(s) of expertise align with your needs, and then [check their availability and contact info][Schedule]. The program is organized similar to office hours, and each week 2-3 people are available to provide help. Some people have office hours on a fixed day and time, whereas others can be contacted to setup a meeting at an agreed-upon day and time. **The current week is listed below.**

**To get the most of these meetings, think prior to the meeting what exactly is needed and come with the thoughts/materials ready** (or even send them before the meeting). For example, for help with coding a specific model, it would be very helpful to send the following material before the meeting so that the supporter can already prepare for the questions:

(1) The questions that should be addressed with the model
(2) The data and
(3) The current code

**Current week** (if not up-to-date, the webpage has to re-created)  


```r
current_week_people_support_area %>% 
  distinct(Week, Start_date, End_date) %>% 
  kable()
```



| Week|Start_date |End_date |
|----:|:----------|:--------|

**People available this week:**  


```r
current_week_people_support_area %>% 
  mutate(Person = paste0(FirstName, " (", Name_ID, ")")) %>% 
  select(Person, Day_and_Time = If_fixed_when, How_to_contact, Area = Support_areas) %>% 
  flextable() %>% 
  color(j = c("Person", "Day_and_Time", "How_to_contact"), color = "darkgreen", part = "all") %>%
  color(j = c("Area"), color = "darkred", part = "all") %>%
  merge_v() %>% 
  border_inner_h(border = officer::fp_border(color = "darkgreen", width = 1),
                 part = "body") %>%
  border_inner_h(border = officer::fp_border(color = "black", width = 2),
                 part = "header") %>%
  set_table_properties(layout = "autofit")
```

```{=html}
<template id="77ffee7d-22c5-4249-bf26-a1dd3001bd60"><style>
.tabwid table{
  border-spacing:0px !important;
  border-collapse:collapse;
  line-height:1;
  margin-left:auto;
  margin-right:auto;
  border-width: 0;
  display: table;
  margin-top: 1.275em;
  margin-bottom: 1.275em;
  border-color: transparent;
}
.tabwid_left table{
  margin-left:0;
}
.tabwid_right table{
  margin-right:0;
}
.tabwid td {
    padding: 0;
}
.tabwid a {
  text-decoration: none;
}
.tabwid thead {
    background-color: transparent;
}
.tabwid tfoot {
    background-color: transparent;
}
.tabwid table tr {
background-color: transparent;
}
</style><div class="tabwid"><style>.cl-551da6bc{table-layout:auto;width:0%;}.cl-551908a0{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-551908be{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-551917be{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-551937f8{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-551da6bc'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-551937f8"><p class="cl-551917be"><span class="cl-551908a0">Person</span></p></td><td class="cl-551937f8"><p class="cl-551917be"><span class="cl-551908a0">Day_and_Time</span></p></td><td class="cl-551937f8"><p class="cl-551917be"><span class="cl-551908a0">How_to_contact</span></p></td><td class="cl-551937f8"><p class="cl-551917be"><span class="cl-551908be">Area</span></p></td></tr></thead></table></div></template>
<div class="flextable-shadow-host" id="8628032a-dafb-434e-a08d-ce818e2c328f"></div>
<script>
var dest = document.getElementById("8628032a-dafb-434e-a08d-ce818e2c328f");
var template = document.getElementById("77ffee7d-22c5-4249-bf26-a1dd3001bd60");
var caption = template.content.querySelector("caption");
if(caption) {
  caption.style.cssText = "display:block;text-align:center;";
  var newcapt = document.createElement("p");
  newcapt.appendChild(caption)
  dest.parentNode.insertBefore(newcapt, dest.previousSibling);
}
var fantome = dest.attachShadow({mode: 'open'});
var templateContent = template.content;
fantome.appendChild(templateContent);
</script>

```
 
 




If you are interested in being added to the list of helpers, contact Urs.

