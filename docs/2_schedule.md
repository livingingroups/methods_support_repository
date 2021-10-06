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
<template id="9e61f2bc-9a8e-4671-bb73-5ffd342fd6d1"><style>
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
</style><div class="tabwid"><style>.cl-dfb484de{table-layout:auto;width:0%;}.cl-dfaead66{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 0, 0, 1.00);background-color:transparent;}.cl-dfaead7a{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-dfaead84{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-dfaebe96{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-dfaebeaa{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-dfaf0c16{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c2a{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c2b{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c34{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c35{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c3e{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c48{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-dfaf0c49{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-dfb484de'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c49"><p class="cl-dfaebe96"><span class="cl-dfaead66">Week</span></p></td><td class="cl-dfaf0c49"><p class="cl-dfaebe96"><span class="cl-dfaead7a">Week_start</span></p></td><td class="cl-dfaf0c49"><p class="cl-dfaebe96"><span class="cl-dfaead7a">Week_end</span></p></td><td class="cl-dfaf0c48"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Person</span></p></td><td class="cl-dfaf0c48"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Day_and_Time</span></p></td><td class="cl-dfaf0c48"><p class="cl-dfaebeaa"><span class="cl-dfaead66">How_to_contact</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c16"><p class="cl-dfaebe96"><span class="cl-dfaead66">40</span></p></td><td  rowspan="2"class="cl-dfaf0c16"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-02</span></p></td><td  rowspan="2"class="cl-dfaf0c16"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-08</span></p></td><td class="cl-dfaf0c2a"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Tracy (TM1)</span></p></td><td class="cl-dfaf0c2a"><p class="cl-dfaebeaa"><span class="cl-dfaead66">By appointment</span></p></td><td class="cl-dfaf0c2a"><p class="cl-dfaebeaa"><span class="cl-dfaead66">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Jake (JG1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">41</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-09</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-15</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Eli (ES1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Tues and Wed 12-2p</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">in person or over email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Shauhin (SA1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">42</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-16</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-22</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Mara (MT1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Wed 10-12</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">other times via appointment. Contact via email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Genevieve (GF1)</span></p></td><td  rowspan="2"class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td  rowspan="2"class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">43</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-23</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-29</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Urs (UK1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Wednesday, 12 - 2 pm</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">44</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-10-30</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-05</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Alie (AA1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Mondays from 2-4pm</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Roi (RH1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">45</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-06</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-12</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Tracy (TM1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">By appointment</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Jake (JG1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">46</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-13</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-19</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Eli (ES1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Tues and Wed 12-2p</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">in person or over email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Shauhin (SA1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">47</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-20</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-26</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Mara (MT1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Wed 10-12</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">other times via appointment. Contact via email</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Genevieve (GF1)</span></p></td><td  rowspan="2"class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td  rowspan="2"class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">48</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-11-27</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-03</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Urs (UK1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Wednesday, 12 - 2 pm</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">49</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-04</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-10</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Alie (AA1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Mondays from 2-4pm</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Roi (RH1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">50</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-11</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-17</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Tracy (TM1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">By appointment</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">email me and we set something up</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Jake (JG1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead66">51</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-18</span></p></td><td  rowspan="2"class="cl-dfaf0c2b"><p class="cl-dfaebe96"><span class="cl-dfaead7a">2021-12-24</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Alie (AA1)</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">Mondays from 2-4pm</span></p></td><td class="cl-dfaf0c34"><p class="cl-dfaebeaa"><span class="cl-dfaead66">contact by email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-dfaf0c3e"><p class="cl-dfaebeaa"><span class="cl-dfaead84">Roi (RH1)</span></p></td><td class="cl-dfaf0c3e"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td><td class="cl-dfaf0c3e"><p class="cl-dfaebeaa"><span class="cl-dfaead66"></span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="b252ca72-4c6d-4e47-aeba-e26d40e4cae2"></div>
<script>
var dest = document.getElementById("b252ca72-4c6d-4e47-aeba-e26d40e4cae2");
var template = document.getElementById("9e61f2bc-9a8e-4671-bb73-5ffd342fd6d1");
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


