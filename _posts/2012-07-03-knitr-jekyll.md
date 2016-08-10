---
layout: post
title: "Blog with Knitr and Jekyll"
description: ""
category: r
tags: [knitr, jekyll, tutorial]
---
{% include JB/setup %}

The [knitr](http://yihui.name/knitr/) package provides an easy way to embed
[R](http://www.r-project.org/) code in a [Jekyll-Bootstrap](http://jekyllbootstrap.com/)
blog post. The only required input is an **R Markdown** source file.
The name of the source file used to generate this post is *2012-07-03-knitr-jekyll.Rmd*, available
[here](https://github.com/jfisher-usgs/jfisher-usgs.github.com/blob/master/Rmd/2012-07-03-knitr-jekyll.Rmd).
Steps taken to build this post are as follows:

### Step 1

Create a Jekyll-Boostrap blog if you don't already have one.
A brief tutorial on building this blog is available
[here](/lessons/2012/05/30/jekyll-build-on-windows.html).

### Step 2

Open the R Console and process the source file:

{% highlight r %}
KnitPost <- function(input, base.url = "/") {
  require(knitr)
  opts_knit$set(base.url = base.url)
  fig.path <- paste0("figs/", sub(".Rmd$", "", basename(input)), "/")
  opts_chunk$set(fig.path = fig.path)
  opts_chunk$set(fig.cap = "center")
  render_jekyll()
  knit(input, envir = parent.frame())
}
KnitPost("2012-07-03-knitr-jekyll.Rmd")
{% endhighlight %}

### Step 3

Move the resulting image folder *2012-07-03-knitr-jekyll* and **Markdown** file
*2012-07-03-knitr-jekyll.md* to the local
*jfisher-usgs.github.com* [git](http://git-scm.com/) repository.
The KnitPost function assumes that the image folder will be placed in a
[figs](https://github.com/jfisher-usgs/jfisher-usgs.github.com/tree/master/figs)
folder located at the root of the repository.

### Step 4

Add the following CSS code to the
*/assets/themes/twitter-2.0/css/bootstrap.min.css* file to center images:

{% highlight r %}
[alt=center] {
  display: block;
  margin: auto;
}
{% endhighlight %}

That's it.

***

Here are a few examples of embedding R code:

{% highlight r %}
summary(cars)
{% endhighlight %}



{% highlight text %}
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
{% endhighlight %}


{% highlight r %}
par(mar = c(4, 4, 0.1, 0.1), omi = c(0, 0, 0, 0))
plot(cars)
{% endhighlight %}

![center](/figs/2012-07-03-knitr-jekyll/fig1-1.png)

##### Figure 1: Caption


{% highlight r %}
par(mar = c(2.5, 2.5, 0.5, 0.1), omi = c(0, 0, 0, 0))
filled.contour(volcano)
{% endhighlight %}

![center](/figs/2012-07-03-knitr-jekyll/fig2-1.png)

##### Figure 2: Caption

And don't forget your session information for proper reproducible research.

{% highlight r %}
sessionInfo()
{% endhighlight %}



{% highlight text %}
## R version 3.3.1 (2016-06-21)
## Platform: x86_64-w64-mingw32/x64 (64-bit)
## Running under: Windows 10 x64 (build 10586)
## 
## locale:
## [1] LC_COLLATE=English_United States.1252 
## [2] LC_CTYPE=English_United States.1252   
## [3] LC_MONETARY=English_United States.1252
## [4] LC_NUMERIC=C                          
## [5] LC_TIME=English_United States.1252    
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] knitr_1.13.1
## 
## loaded via a namespace (and not attached):
## [1] magrittr_1.5  formatR_1.4   tools_3.3.1   stringi_1.1.1 stringr_1.0.0
## [6] evaluate_0.9
{% endhighlight %}
