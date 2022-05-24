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
library(flextable)
#> Warning: package 'flextable' was built under R version 4.0.5
```



```r

people <- read.csv(here::here("data/Name_table.csv"))
schedule <- read.csv(here::here("data/Schedule_table.csv"))

schedule_people <- schedule %>% 
  left_join(people, by = "Name_ID") %>% 
  mutate(Start_date = as.Date(Start_date, format = c("%d.%m.%y")),
         End_date = as.Date(End_date, format = c("%d.%m.%y")))

schedule_people %>% 
  mutate(Person = paste0(FirstName, " (", Name_ID, ")")) %>% 
  select(Week, Week_start = Start_date, Week_end = End_date,
         Person, Day_and_Time = If_fixed_when, How_to_contact) %>% 
  flextable() %>% 
  color(j = c("Week_start", "Week_end"), color = "darkgreen", part = "all") %>%
  color(j = c("Person"), color = "darkred", part = "all") %>%
  merge_v() %>% 
  border_inner_h(border = officer::fp_border(color = "darkgreen", width = 1),
                 part = "body") %>%
  border_inner_h(border = officer::fp_border(color = "black", width = 2),
                 part = "header") %>%
  set_table_properties(layout = "autofit")
```

```{=html}
<template id="96b57642-e91c-4285-8f31-c90665e4bcc9"><style>
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
</style><div class="tabwid"><style>.cl-5667bbde{table-layout:auto;width:0%;}.cl-5661c940{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 0, 0, 1.00);background-color:transparent;}.cl-5661c95e{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-5661c968{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-5661da20{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-5661da2a{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-56622660{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5662266a{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5662266b{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-5662266c{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-56622674{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-56622675{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-56622676{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-56622677{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-5667bbde'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-56622677"><p class="cl-5661da20"><span class="cl-5661c940">Week</span></p></td><td class="cl-56622677"><p class="cl-5661da20"><span class="cl-5661c95e">Week_start</span></p></td><td class="cl-56622677"><p class="cl-5661da20"><span class="cl-5661c95e">Week_end</span></p></td><td class="cl-56622676"><p class="cl-5661da2a"><span class="cl-5661c968">Person</span></p></td><td class="cl-56622676"><p class="cl-5661da2a"><span class="cl-5661c940">Day_and_Time</span></p></td><td class="cl-56622676"><p class="cl-5661da2a"><span class="cl-5661c940">How_to_contact</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-56622660"><p class="cl-5661da20"><span class="cl-5661c940">40</span></p></td><td  rowspan="2"class="cl-56622660"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-02</span></p></td><td  rowspan="2"class="cl-56622660"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-08</span></p></td><td class="cl-5662266a"><p class="cl-5661da2a"><span class="cl-5661c968">Tracy (TM1)</span></p></td><td class="cl-5662266a"><p class="cl-5661da2a"><span class="cl-5661c940">By appointment</span></p></td><td class="cl-5662266a"><p class="cl-5661da2a"><span class="cl-5661c940">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Jake (JG1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Tues and Thurs 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Email (jgraving@ab.mpg.de) or Slack</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">41</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-09</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-15</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Eli (ES1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Tues and Wed 12-2p</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">in person or over email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Shauhin (SA1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">42</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-16</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-22</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Mara (MT1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wed 10-12</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">other times via appointment. Contact via email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Genevieve (GF1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wed 12-2</span></p></td><td  rowspan="2"class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">43</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-23</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-29</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Vivek Hari (VHS1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Urs (UK1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wednesday, 12 - 2 pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">44</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-10-30</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-05</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Alie (AA1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Mondays from 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Roi (RH1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">45</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-06</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-12</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Tracy (TM1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">By appointment</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Jake (JG1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Tues and Thurs 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Email (jgraving@ab.mpg.de) or Slack</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">46</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-13</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-19</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Eli (ES1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Tues and Wed 12-2p</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">in person or over email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Shauhin (SA1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">47</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-20</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-26</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Mara (MT1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wed 10-12</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">other times via appointment. Contact via email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Genevieve (GF1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wed 12-2</span></p></td><td  rowspan="2"class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">48</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-11-27</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-03</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Vivek Hari (VHS1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Urs (UK1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Wednesday, 12 - 2 pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">49</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-04</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-10</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Alie (AA1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Mondays from 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Roi (RH1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">50</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-11</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-17</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Tracy (TM1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">By appointment</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Jake (JG1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Tues and Thurs 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Email (jgraving@ab.mpg.de) or Slack</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">51</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-18</span></p></td><td  rowspan="2"class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2021-12-24</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Alie (AA1)</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">Mondays from 2-4pm</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">Roi (RH1)</span></p></td><td  rowspan="3"class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td><td  rowspan="3"class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c940"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c940">1</span></p></td><td class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2022-01-03</span></p></td><td class="cl-5662266c"><p class="cl-5661da20"><span class="cl-5661c95e">2022-01-09</span></p></td><td class="cl-5662266b"><p class="cl-5661da2a"><span class="cl-5661c968">NA ()</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-56622675"><p class="cl-5661da20"><span class="cl-5661c940">2</span></p></td><td class="cl-56622675"><p class="cl-5661da20"><span class="cl-5661c95e">2022-01-10</span></p></td><td class="cl-56622675"><p class="cl-5661da20"><span class="cl-5661c95e">2022-01-16</span></p></td><td class="cl-56622674"><p class="cl-5661da2a"><span class="cl-5661c968">Vlad (VD1)</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="c306a883-795d-49a0-8058-56974882864c"></div>
<script>
var dest = document.getElementById("c306a883-795d-49a0-8058-56974882864c");
var template = document.getElementById("96b57642-e91c-4285-8f31-c90665e4bcc9");
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


