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
<template id="a1507d22-2824-4dee-8a6d-65a183853b6b"><style>
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
</style><div class="tabwid"><style>.cl-9e56493a{table-layout:auto;width:0%;}.cl-9e5028b6{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 0, 0, 1.00);background-color:transparent;}.cl-9e5028ca{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-9e5028d4{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(139, 0, 0, 1.00);background-color:transparent;}.cl-9e5038a6{margin:0;text-align:right;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-9e5038ba{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-9e50f8c2{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8e0{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8e1{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8ea{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8eb{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8f4{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8f5{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-9e50f8fe{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-9e56493a'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8f5"><p class="cl-9e5038a6"><span class="cl-9e5028b6">Week</span></p></td><td class="cl-9e50f8f5"><p class="cl-9e5038a6"><span class="cl-9e5028ca">Week_start</span></p></td><td class="cl-9e50f8f5"><p class="cl-9e5038a6"><span class="cl-9e5028ca">Week_end</span></p></td><td class="cl-9e50f8fe"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Person</span></p></td><td class="cl-9e50f8f5"><p class="cl-9e5038a6"><span class="cl-9e5028b6">Day_and_Time</span></p></td><td class="cl-9e50f8f5"><p class="cl-9e5038a6"><span class="cl-9e5028b6">How_to_contact</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8c2"><p class="cl-9e5038a6"><span class="cl-9e5028b6">39</span></p></td><td  rowspan="2"class="cl-9e50f8c2"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-09-27</span></p></td><td  rowspan="2"class="cl-9e50f8c2"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-01</span></p></td><td class="cl-9e50f8e0"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Alie (AA1)</span></p></td><td  rowspan="24"class="cl-9e50f8c2"><p class="cl-9e5038a6"><span class="cl-9e5028b6"></span></p></td><td  rowspan="24"class="cl-9e50f8c2"><p class="cl-9e5038a6"><span class="cl-9e5028b6"></span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Roi (RH1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">40</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-04</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-08</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Tracy (TM1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Jake (JG1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">41</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-11</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-15</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Eli (ES1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Shauhin (SA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">42</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-18</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-22</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Mara (MT1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Genevieve (GF1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">43</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-25</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-10-29</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Urs (UK1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">44</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-01</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-05</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Alie (AA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Roi (RH1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">45</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-08</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-12</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Tracy (TM1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Jake (JG1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">46</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-15</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-19</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Eli (ES1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Shauhin (SA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">47</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-22</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-26</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Mara (MT1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Genevieve (GF1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">48</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-11-29</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-12-03</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Vivek Hari (VHS1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Urs (UK1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">49</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-12-06</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-12-10</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Alie (AA1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Roi (RH1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028b6">50</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-12-13</span></p></td><td  rowspan="2"class="cl-9e50f8e1"><p class="cl-9e5038a6"><span class="cl-9e5028ca">2021-12-17</span></p></td><td class="cl-9e50f8ea"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Tracy (TM1)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-9e50f8f4"><p class="cl-9e5038ba"><span class="cl-9e5028d4">Jake (JG1)</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="d7a347e4-6264-4693-9037-56e39cc30847"></div>
<script>
var dest = document.getElementById("d7a347e4-6264-4693-9037-56e39cc30847");
var template = document.getElementById("a1507d22-2824-4dee-8a6d-65a183853b6b");
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


