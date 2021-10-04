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
<template id="dbc805bc-9593-45de-a24c-8846b80bfc17"><style>
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
</style><div class="tabwid"><style>.cl-3e818418{table-layout:auto;width:0%;}.cl-3e7b9d5a{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 0, 0, 1.00);background-color:transparent;}.cl-3e7b9d6e{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-3e7b9d78{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-3e7bad72{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-3e7bad86{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-3e7bf8a4{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8b8{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8b9{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8c2{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8cc{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8cd{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8d6{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-3e7bf8d7{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-3e818418'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8d7"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">Week</span></p></td><td class="cl-3e7bf8d7"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">Week_start</span></p></td><td class="cl-3e7bf8d7"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">Week_end</span></p></td><td class="cl-3e7bf8d6"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Person</span></p></td><td class="cl-3e7bf8d6"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">Day_and_Time</span></p></td><td class="cl-3e7bf8d6"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">How_to_contact</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8a4"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">40</span></p></td><td  rowspan="2"class="cl-3e7bf8a4"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-02</span></p></td><td  rowspan="2"class="cl-3e7bf8a4"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-08</span></p></td><td class="cl-3e7bf8b8"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Tracy (TM1)</span></p></td><td  rowspan="7"class="cl-3e7bf8b8"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td><td  rowspan="7"class="cl-3e7bf8b8"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Jake (JG1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">41</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-09</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-15</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Eli (ES1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Shauhin (SA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">42</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-16</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-22</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Mara (MT1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Genevieve (GF1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">43</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-23</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-29</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Urs (UK1)</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">Wednesday, 12 - 2 pm</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">44</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-10-30</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-05</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Alie (AA1)</span></p></td><td  rowspan="9"class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td><td  rowspan="9"class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Roi (RH1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">45</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-06</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-12</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Tracy (TM1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Jake (JG1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">46</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-13</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-19</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Eli (ES1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Shauhin (SA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">47</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-20</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-26</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Mara (MT1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Genevieve (GF1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">48</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-11-27</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-03</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Urs (UK1)</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">Wednesday, 12 - 2 pm</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a">Email or in person</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">49</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-04</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-10</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Alie (AA1)</span></p></td><td  rowspan="6"class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td><td  rowspan="6"class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d5a"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Roi (RH1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">50</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-11</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-17</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Tracy (TM1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Jake (JG1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d5a">51</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-18</span></p></td><td  rowspan="2"class="cl-3e7bf8b9"><p class="cl-3e7bad72"><span class="cl-3e7b9d6e">2021-12-24</span></p></td><td class="cl-3e7bf8c2"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Alie (AA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-3e7bf8cd"><p class="cl-3e7bad86"><span class="cl-3e7b9d78">Roi (RH1)</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="8ba9149e-f160-4875-8964-ad7d568f2904"></div>
<script>
var dest = document.getElementById("8ba9149e-f160-4875-8964-ad7d568f2904");
var template = document.getElementById("dbc805bc-9593-45de-a24c-8846b80bfc17");
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


