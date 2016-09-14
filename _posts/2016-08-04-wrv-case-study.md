---
layout: post
title: "A Case Study in Reproducible Model Building"
description: ""
category: r
tags: [reproducibility, package, knitr, model]
---
{% include JB/setup %}

![center](/figs/2016-08-04-wrv-case-study/fig1.png)

The U.S. Geological Survey ([USGS](https://www.usgs.gov/)) recently published a report describing a groundwater-flow model of the Wood River Valley (WRV) aquifer system.
What makes this report unique (at least in my opinion) was the authors' desire to make their work as reproducible as possible under budgetary constraints.
The collection of raw data, source code, and processing instructions used to build and analyze the model was placed in an non-general-use R package named **wrv**.
The package repository can be found on [GitHub](https://github.com/USGS-R/wrv).
Commands for installing the package are as follows:

```r
repos <- c("http://owi.usgs.gov/R", getOption("repos"))
install.packages("wrv", repos = repos, dependencies = TRUE)  # about 100 MB, so be patient
```

While many of the functions are intended for non-general use, there are a few functions that the larger R community might find of interest.
For example, the `PlotMap`, `PlotGraph`, and `PlotCrossSection` functions have been designed for general use.
Report documentation was included in the **wrv** package as vignettes; these files are also available from the
[USGS Publications Warehouse](http://dx.doi.org/10.3133/sir20165080).
For a general overview of the project, I'll recommend my
[useR! 2016 talk](https://channel9.msdn.com/Events/useR-international-R-User-conference/useR2016/A-Case-Study-in-Reproducible-Model-Building-Simulating-Groundwater-Flow-in-the-Wood-River-Valley-Aqu):

<div style="text-align:center;padding: 1% 0%;">
<iframe src="https://channel9.msdn.com/Events/useR-international-R-User-conference/useR2016/A-Case-Study-in-Reproducible-Model-Building-Simulating-Groundwater-Flow-in-the-Wood-River-Valley-Aqu/player" width="560" height="315" allowFullScreen frameBorder="0"></iframe>
</div>

Any comments or suggestions regarding our approach to reproducible model building can be left below.
Please realize that your opinions go a long way in determining whether this type of approach will be used in future projects.
