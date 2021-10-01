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
<template id="057687e5-46e2-4541-951a-bac6c01ad2a1"><style>
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
</style><div class="tabwid"><style>.cl-c624adac{table-layout:auto;width:0%;}.cl-c61ea0f6{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-c61eb1d6{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-c61ef7b8{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-c61ef7cc{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-c61ef7cd{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-c61ef7d6{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-c624adac'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7d6"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Person</span></p></td><td class="cl-c61ef7d6"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Area</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="4"class="cl-c61ef7b8"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Alie (AA1)</span></p></td><td class="cl-c61ef7b8"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data visualization (including mapping) (conceptualization +/ execution in R)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Basic movement analysis (calculating home ranges, DJLs, etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="10"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Urs (UK1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R programming</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Working with spatial data (to a certain degree)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Fitting linear models from LMs to GLMMs in a frequentist and bayesian way</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Social Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Generally working with data on social behavior</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data bases</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Structuring data analysis projects</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Foundations of endocrinological work with wild animals</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Workin with long-term data sets</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="5"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Roi (RH1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Analysing acceleration data &amp; behavior inference from sensor data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data collection design and working with data-loggers / GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">working with video data (object detection &amp; tracking, Python, OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Machine Learning clustering, SVM, random forest, xgboost (R, Matlab)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="5"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Tracy (TM1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling &amp; visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Designing GLMMs &amp; otherwise structuring an analysis to test hypotheses</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Executing GLMMs (frequentist)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Long-term data, behavioral sampling design/analysis, database design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Eli (ES1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">git/github</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Simulations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Social network data, long-term data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Happy to try to help with movement/tag data but I’m still learning</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R package development</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Vivek Hari (VHS1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Python programming; data wrangling &amp; visualisation</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Agent-based modelling (I tend to use C++)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">General analyses and data interpretation for animal movement, social/collective behaviours</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Basic computer vision (OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Basic bayesian statistics (GLMs/GLMMs)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Machine learning (dimensionality reduction/clustering)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Jake (JG1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">General experimental design/analysis questions</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Python: data wrangling (pandas, numpy, etc.), visualisation (expert knowledge of matplotlib and seaborn APIs), code optimization (vectorized/parallel programming, JIT optimization, GPU compute), machine learning and optimization libraries (JAX, PyTorch, Tensorflow/Keras, Numpyro/Pyro, PyMC3, PyStan), package development (pip, PyPI, setuptools)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Analysis and interpretation of animal movement trajectories (incl. high-dimensional time series), social/collective behaviours, network data, audio/spectrogram data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Advanced computer vision and image processing (OpenCV, deep conv nets, object detection and tracking, pose estimation, segmentation, image/object classification)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Advanced bayesian statistics and causal inference (GLMs/GLMMs, Bayesian networks, hierarchical models, autoregressive/time series models, latent variable models, variational inference)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Machine learning and deep learning (neural nets, linear/nonlinear dimension reduction, contrastive learning, clustering &amp; unsupervised classification, sequence and time series models, supervised classification, Bayesian/probabilistic deep learning)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="15"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Shauhin (SA1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R, QGIS</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data manipulation and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Sampling design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Bio-loggers and GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Bayesian (rstan) and frequentist statistics (GLMM/GAMM, splines, nonlinear hierarchical models, autoregressive/timeseries models, spatial regression, PCA, phylogenetic models)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Geospatial statistics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Simulation, theoretical modeling, agent based modeling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Supervised and unsupervised clustering, SVM, random forest, xgboost</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Analysis of animal movement data (discrete and continuous time)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Behavioral inference from sensor data (GPS, ACC)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Remote sensing (Hyperspectral/multispectral data, satellite and aerial imagery, LiDAR, SAR, photogrammetry)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Nutritional Analyses and Geometric framework of Nutrition</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Spatial Cognition </span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Basic field endocrinology/physiology</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="9"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Mara (MT1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Python</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Supervised and unsupervised dimensionality reduction, clustering</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Bioacoustics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">ML or other classifier (SVM, random forest, NN, xgboost, LDA..)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Frequentist statistics in R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Bioinformatic analyses in R/bash/C (Illumina microarrays, NGS data, genomics…)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Genevieve (GF1)</span></p></td><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Mostly in R, unless someone wants to do connectivity stuff using UNICOR and/or CircuitScape</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Can maybe help with QGIS also, but try to avoid it</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">General data wrangling/visualisation, incl. movement and spatial data (gridded datasets etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Problem shooting code/error messages</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Running things in parallel (I’m not great but it works, more or less)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">Animal movement analysis; home range/daily distances etc (have mostly been using ctmm package recently)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cc"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">A bit of agent-based modelling (netlogo)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-c61ef7cd"><p class="cl-c61eb1d6"><span class="cl-c61ea0f6">lm/glm/glmm/gam using frequentist approaches</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="ceee4472-4876-484d-a50c-ab2ff32fcb2d"></div>
<script>
var dest = document.getElementById("ceee4472-4876-484d-a50c-ab2ff32fcb2d");
var template = document.getElementById("057687e5-46e2-4541-951a-bac6c01ad2a1");
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

