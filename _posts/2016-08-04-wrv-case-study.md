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
The package repository can be found on the **G**elogical Survey **R** **A**rchive **N**etwork ([GRAN](https://github.com/USGS-R/wrv)).
Commands for installing the package are as follows:

```r
repos <- c("https://owi.usgs.gov/R", "https://cloud.r-project.org/")
install.packages("wrv", repos = repos, dependencies = TRUE)  # about 100 MB, so be patient
```

Report documentation was included in the **wrv** package as vignettes; these files are also available from the
[USGS Publications Warehouse](http://dx.doi.org/10.3133/sir20165080).
For a general overview of the project, I'll recommend my
[useR! 2016 talk](https://channel9.msdn.com/Events/useR-international-R-User-conference/useR2016/A-Case-Study-in-Reproducible-Model-Building-Simulating-Groundwater-Flow-in-the-Wood-River-Valley-Aqu):

<div style="text-align:center;padding: 1% 0%;">
<iframe src="https://channel9.msdn.com/Events/useR-international-R-User-conference/useR2016/A-Case-Study-in-Reproducible-Model-Building-Simulating-Groundwater-Flow-in-the-Wood-River-Valley-Aqu/player" width="560" height="315" allowFullScreen frameBorder="0"></iframe>
</div>
