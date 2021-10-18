---
title: "Methods Support Program"
subtitle: "Webpage to organize and advertise this program"
author: "Various people"
date: "2021-10-18"
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



| Week|Start_date |End_date   |
|----:|:----------|:----------|
|   42|2021-10-16 |2021-10-22 |

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
<template id="07a88976-c7a0-4e40-a0cb-649514f13d37"><style>
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
</style><div class="tabwid"><style>.cl-e86ee168{table-layout:auto;width:0%;}.cl-e869ba1c{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-e869ba30{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-e869ca0c{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-e869faea{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-e869fafe{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-e869fb08{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-e869fb12{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-e86ee168'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-e869fb12"><p class="cl-e869ca0c"><span class="cl-e869ba1c">Person</span></p></td><td class="cl-e869fb12"><p class="cl-e869ca0c"><span class="cl-e869ba1c">Day_and_Time</span></p></td><td class="cl-e869fb12"><p class="cl-e869ca0c"><span class="cl-e869ba1c">How_to_contact</span></p></td><td class="cl-e869fb12"><p class="cl-e869ca0c"><span class="cl-e869ba30">Area</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="9"class="cl-e869faea"><p class="cl-e869ca0c"><span class="cl-e869ba1c">Mara (MT1)</span></p></td><td  rowspan="9"class="cl-e869faea"><p class="cl-e869ca0c"><span class="cl-e869ba1c">Wed 10-12</span></p></td><td  rowspan="9"class="cl-e869faea"><p class="cl-e869ca0c"><span class="cl-e869ba1c">other times via appointment. Contact via email</span></p></td><td class="cl-e869faea"><p class="cl-e869ca0c"><span class="cl-e869ba30">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Python</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Supervised and unsupervised dimensionality reduction, clustering</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Bioacoustics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">ML or other classifier (SVM, random forest, NN, xgboost, LDA..)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Frequentist statistics in R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Bioinformatic analyses in R/bash/C (Illumina microarrays, NGS data, genomics…)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba1c">Genevieve (GF1)</span></p></td><td  rowspan="8"class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba1c"></span></p></td><td  rowspan="8"class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba1c"></span></p></td><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Mostly in R, unless someone wants to do connectivity stuff using UNICOR and/or CircuitScape</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Can maybe help with QGIS also, but try to avoid it</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">General data wrangling/visualisation, incl. movement and spatial data (gridded datasets etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Problem shooting code/error messages</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Running things in parallel (I’m not great but it works, more or less)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">Animal movement analysis; home range/daily distances etc (have mostly been using ctmm package recently)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fafe"><p class="cl-e869ca0c"><span class="cl-e869ba30">A bit of agent-based modelling (netlogo)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-e869fb08"><p class="cl-e869ca0c"><span class="cl-e869ba30">lm/glm/glmm/gam using frequentist approaches</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="56ee6199-e5bf-468d-b843-41890aa3d339"></div>
<script>
var dest = document.getElementById("56ee6199-e5bf-468d-b843-41890aa3d339");
var template = document.getElementById("07a88976-c7a0-4e40-a0cb-649514f13d37");
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

