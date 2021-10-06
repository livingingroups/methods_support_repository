---
output: html_document
editor_options:
  chunk_output_type: console
---
# Overview



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


Here is a list with all people interested in providing support including their areas in which they can provide support.


```r
people <- read.csv(here::here("data/Name_table.csv"))
support_area <- read.csv(here::here("data/Expertise_table.csv"))

people_support_area <- people %>% 
  left_join(support_area, by = "Name_ID")

people_support_area %>% 
  mutate(Person = paste0(FirstName, " (", Name_ID, ")")) %>% 
  select(Person, Area = Support_areas) %>% 
  flextable() %>% 
  color(j = c("Person", "Area"), color = "darkgreen", part = "all") %>% 
  merge_v() %>% 
  border_inner_h(border = officer::fp_border(color = "darkgreen", width = 1),
                 part = "body") %>% 
  border_inner_h(border = officer::fp_border(color = "black", width = 2),
                 part = "header") %>% 
  set_table_properties(layout = "autofit")
```

```{=html}
<template id="13441248-5ab4-4df9-bab4-058649cbd224"><style>
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
</style><div class="tabwid"><style>.cl-582cf2e0{table-layout:auto;width:0%;}.cl-5824deb6{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-5824f43c{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-582551ca{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-582551de{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-582551e8{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-582551f2{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-582cf2e0'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-582551f2"><p class="cl-5824f43c"><span class="cl-5824deb6">Person</span></p></td><td class="cl-582551f2"><p class="cl-5824f43c"><span class="cl-5824deb6">Area</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="4"class="cl-582551ca"><p class="cl-5824f43c"><span class="cl-5824deb6">Alie (AA1)</span></p></td><td class="cl-582551ca"><p class="cl-5824f43c"><span class="cl-5824deb6">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data visualization (including mapping) (conceptualization +/ execution in R)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Basic movement analysis (calculating home ranges, DJLs, etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="10"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Urs (UK1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R programming</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Working with spatial data (to a certain degree)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Fitting linear models from LMs to GLMMs in a frequentist and bayesian way</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Social Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Generally working with data on social behavior</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data bases</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Structuring data analysis projects</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Foundations of endocrinological work with wild animals</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Workin with long-term data sets</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Roi (RH1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Analysing acceleration data &amp; behavior inference from sensor data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data collection design and working with data-loggers / GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">working with video data (object detection &amp; tracking, Python, OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Machine Learning clustering, SVM, random forest, xgboost (R, Matlab)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">GPS\ACC\IMU dataloggers attachment\design\configuration</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="7"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Tracy (TM1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling &amp; visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Designing GLMMs &amp; otherwise structuring an analysis to test hypotheses</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Executing GLMMs (frequentist)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Long-term data, behavioral sampling design/analysis, database design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">eObs collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">endocrinology</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Eli (ES1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">git/github</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Simulations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Social network data, long-term data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Happy to try to help with movement/tag data but I’m still learning</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R package development</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Vivek Hari (VHS1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Python programming; data wrangling &amp; visualisation</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Agent-based modelling (I tend to use C++)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">General analyses and data interpretation for animal movement, social/collective behaviours</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Basic computer vision (OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Basic bayesian statistics (GLMs/GLMMs)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Machine learning (dimensionality reduction/clustering)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Jake (JG1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">General experimental design/analysis questions</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Python: data wrangling (pandas, numpy, etc.), visualisation (expert knowledge of matplotlib and seaborn APIs), code optimization (vectorized/parallel programming, JIT optimization, GPU compute), machine learning and optimization libraries (JAX, PyTorch, Tensorflow/Keras, Numpyro/Pyro, PyMC3, PyStan), package development (pip, PyPI, setuptools)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Analysis and interpretation of animal movement trajectories (incl. high-dimensional time series), social/collective behaviours, network data, audio/spectrogram data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Advanced computer vision and image processing (OpenCV, deep conv nets, object detection and tracking, pose estimation, segmentation, image/object classification)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Advanced bayesian statistics and causal inference (GLMs/GLMMs, Bayesian networks, hierarchical models, autoregressive/time series models, latent variable models, variational inference)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Machine learning and deep learning (neural nets, linear/nonlinear dimension reduction, contrastive learning, clustering &amp; unsupervised classification, sequence and time series models, supervised classification, Bayesian/probabilistic deep learning)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="15"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Shauhin (SA1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R, QGIS</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data manipulation and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Sampling design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Bio-loggers and GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Bayesian (rstan) and frequentist statistics (GLMM/GAMM, splines, nonlinear hierarchical models, autoregressive/timeseries models, spatial regression, PCA, phylogenetic models)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Geospatial statistics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Simulation, theoretical modeling, agent based modeling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Supervised and unsupervised clustering, SVM, random forest, xgboost</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Analysis of animal movement data (discrete and continuous time)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Behavioral inference from sensor data (GPS, ACC)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Remote sensing (Hyperspectral/multispectral data, satellite and aerial imagery, LiDAR, SAR, photogrammetry)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Nutritional Analyses and Geometric framework of Nutrition</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Spatial Cognition </span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Basic field endocrinology/physiology</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="9"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Mara (MT1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Python</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Supervised and unsupervised dimensionality reduction, clustering</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Bioacoustics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">ML or other classifier (SVM, random forest, NN, xgboost, LDA..)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Frequentist statistics in R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Bioinformatic analyses in R/bash/C (Illumina microarrays, NGS data, genomics…)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Genevieve (GF1)</span></p></td><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Mostly in R, unless someone wants to do connectivity stuff using UNICOR and/or CircuitScape</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Can maybe help with QGIS also, but try to avoid it</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">General data wrangling/visualisation, incl. movement and spatial data (gridded datasets etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Problem shooting code/error messages</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Running things in parallel (I’m not great but it works, more or less)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">Animal movement analysis; home range/daily distances etc (have mostly been using ctmm package recently)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551de"><p class="cl-5824f43c"><span class="cl-5824deb6">A bit of agent-based modelling (netlogo)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-582551e8"><p class="cl-5824f43c"><span class="cl-5824deb6">lm/glm/glmm/gam using frequentist approaches</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="a7cf87d9-d902-46a1-8b13-5b670bc0ca8c"></div>
<script>
var dest = document.getElementById("a7cf87d9-d902-46a1-8b13-5b670bc0ca8c");
var template = document.getElementById("13441248-5ab4-4df9-bab4-058649cbd224");
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

