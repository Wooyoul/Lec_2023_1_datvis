---
title: "수업 보충자료용 github"
subtitle: "2023-1학기: 데이터시각화"
abstract: "수업 보충자료용 github입니다."
author:
- name: "Wooyoul Na"
  affiliation: "Konkuk University"  
date: "2023-03-01"
output: 
  html_document:
    theme: flatly
    keep_md: true
    toc: yes
    toc_depth: '4'
    toc_float: yes
    df_print: default
    highlight: zenburn
    code_folding: show
  latex_engine: pdflatax
  pdf_document:
    toc: yes
    toc_depth: '4'
  word_document:
    toc: yes
    toc_depth: 4
mainfont: NanumSquare
---




[example_code.r](https://github.com/Wooyoul/Lec_2023_1_datvis/blob/0545de63930c6ca645629610ba3294180d6f7ae1/R/example_code.r)

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Including Plots

You can also embed plots, for example:

![](README_files/figure-html/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
