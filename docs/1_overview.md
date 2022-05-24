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
#> Warning: package 'flextable' was built under R version 4.0.5
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
<template id="b68ba775-4a05-4703-9e4f-21da76300fe7"><style>
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
</style><div class="tabwid"><style>.cl-55c0b3ac{table-layout:auto;width:0%;}.cl-55baddce{font-family:'Helvetica';font-size:11pt;font-weight:normal;font-style:normal;text-decoration:none;color:rgba(0, 100, 0, 1.00);background-color:transparent;}.cl-55baeec2{margin:0;text-align:left;border-bottom: 0 solid rgba(0, 0, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);padding-bottom:5pt;padding-top:5pt;padding-left:5pt;padding-right:5pt;line-height: 1;background-color:transparent;}.cl-55bb3756{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 0 solid rgba(0, 0, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-55bb3760{background-color:transparent;vertical-align: middle;border-bottom: 1pt solid rgba(0, 100, 0, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-55bb3761{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 1pt solid rgba(0, 100, 0, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}.cl-55bb3762{background-color:transparent;vertical-align: middle;border-bottom: 2pt solid rgba(102, 102, 102, 1.00);border-top: 2pt solid rgba(102, 102, 102, 1.00);border-left: 0 solid rgba(0, 0, 0, 1.00);border-right: 0 solid rgba(0, 0, 0, 1.00);margin-bottom:0;margin-top:0;margin-left:0;margin-right:0;}</style><table class='cl-55c0b3ac'>
```

```{=html}
<thead><tr style="overflow-wrap:break-word;"><td class="cl-55bb3762"><p class="cl-55baeec2"><span class="cl-55baddce">Person</span></p></td><td class="cl-55bb3762"><p class="cl-55baeec2"><span class="cl-55baddce">Area</span></p></td></tr></thead><tbody><tr style="overflow-wrap:break-word;"><td  rowspan="4"class="cl-55bb3756"><p class="cl-55baeec2"><span class="cl-55baddce">Alie (AA1)</span></p></td><td class="cl-55bb3756"><p class="cl-55baeec2"><span class="cl-55baddce">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data visualization (including mapping) (conceptualization +/ execution in R)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Basic movement analysis (calculating home ranges, DJLs, etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="10"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Urs (UK1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R programming</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Working with spatial data (to a certain degree)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Fitting linear models from LMs to GLMMs in a frequentist and bayesian way</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Social Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Generally working with data on social behavior</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data bases</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Structuring data analysis projects</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Foundations of endocrinological work with wild animals</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Workin with long-term data sets</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Roi (RH1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Analysing acceleration data &amp; behavior inference from sensor data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data collection design and working with data-loggers / GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">working with video data (object detection &amp; tracking, Python, OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Machine Learning clustering, SVM, random forest, xgboost (R, Matlab)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">GPS\ACC\IMU dataloggers attachment\design\configuration</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="7"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Tracy (TM1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R programming (base &amp; tidyverse)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling &amp; visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Designing GLMMs &amp; otherwise structuring an analysis to test hypotheses</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Executing GLMMs (frequentist)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Long-term data, behavioral sampling design/analysis, database design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">eObs collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">endocrinology</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Eli (ES1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">git/github</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Simulations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Social network data, long-term data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Happy to try to help with movement/tag data but I’m still learning</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R package development</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Vivek Hari (VHS1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Python programming; data wrangling &amp; visualisation</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Agent-based modelling (I tend to use C++)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">General analyses and data interpretation for animal movement, social/collective behaviours</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Basic computer vision (OpenCV)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Basic bayesian statistics (GLMs/GLMMs)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Machine learning (dimensionality reduction/clustering)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="6"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Jake (JG1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">General experimental design/analysis questions</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Python: data wrangling (pandas, numpy, etc.), visualisation (expert knowledge of matplotlib and seaborn APIs), code optimization (vectorized/parallel programming, JIT optimization, GPU compute), machine learning and optimization libraries (JAX, PyTorch, Tensorflow/Keras, Numpyro/Pyro, PyMC3, PyStan), package development (pip, PyPI, setuptools)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Analysis and interpretation of animal movement trajectories (incl. high-dimensional time series), social/collective behaviours, network data, audio/spectrogram data</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Advanced computer vision and image processing (OpenCV, deep conv nets, object detection and tracking, pose estimation, segmentation, image/object classification)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Advanced bayesian statistics and causal inference (GLMs/GLMMs, Bayesian networks, hierarchical models, autoregressive/time series models, latent variable models, variational inference)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Machine learning and deep learning (neural nets, linear/nonlinear dimension reduction, contrastive learning, clustering &amp; unsupervised classification, sequence and time series models, supervised classification, Bayesian/probabilistic deep learning)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="15"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Shauhin (SA1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R, QGIS</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data manipulation and visualizations</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Sampling design</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Bio-loggers and GPS collars</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Bayesian (rstan) and frequentist statistics (GLMM/GAMM, splines, nonlinear hierarchical models, autoregressive/timeseries models, spatial regression, PCA, phylogenetic models)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Geospatial statistics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Network Analysis</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Simulation, theoretical modeling, agent based modeling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Supervised and unsupervised clustering, SVM, random forest, xgboost</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Analysis of animal movement data (discrete and continuous time)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Behavioral inference from sensor data (GPS, ACC)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Remote sensing (Hyperspectral/multispectral data, satellite and aerial imagery, LiDAR, SAR, photogrammetry)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Nutritional Analyses and Geometric framework of Nutrition</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Spatial Cognition </span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Basic field endocrinology/physiology</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="9"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Mara (MT1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Python</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data wrangling</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Data visualization</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Supervised and unsupervised dimensionality reduction, clustering</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Bioacoustics</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">ML or other classifier (SVM, random forest, NN, xgboost, LDA..)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Frequentist statistics in R</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Bioinformatic analyses in R/bash/C (Illumina microarrays, NGS data, genomics…)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td  rowspan="8"class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Genevieve (GF1)</span></p></td><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Mostly in R, unless someone wants to do connectivity stuff using UNICOR and/or CircuitScape</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Can maybe help with QGIS also, but try to avoid it</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">General data wrangling/visualisation, incl. movement and spatial data (gridded datasets etc)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Problem shooting code/error messages</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Running things in parallel (I’m not great but it works, more or less)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">Animal movement analysis; home range/daily distances etc (have mostly been using ctmm package recently)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">A bit of agent-based modelling (netlogo)</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3760"><p class="cl-55baeec2"><span class="cl-55baddce">lm/glm/glmm/gam using frequentist approaches</span></p></td></tr><tr style="overflow-wrap:break-word;"><td class="cl-55bb3761"><p class="cl-55baeec2"><span class="cl-55baddce">Vlad (VD1)</span></p></td><td class="cl-55bb3761"><p class="cl-55baeec2"><span class="cl-55baddce">field audio recording; tag based audio recorders (deployment, setup and troubleshooting); audio data processing, acoustic analysis in R, Avisoft, Raven and more; playback experiment planning, playback tracks design, playback equipment advice; operation of FLIR thermal cameras,  processing and decoding FLIR file formats, basic thermal analysis using ImageJ and/or Thermimage</span></p></td></tr></tbody></table></div></template>
<div class="flextable-shadow-host" id="0fca106a-05cb-470d-95d4-5130e46ac8ad"></div>
<script>
var dest = document.getElementById("0fca106a-05cb-470d-95d4-5130e46ac8ad");
var template = document.getElementById("b68ba775-4a05-4703-9e4f-21da76300fe7");
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

