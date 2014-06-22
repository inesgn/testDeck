---
title       : Data Products Course Project
subtitle    : Reproducible Presentation in Slidify
author      : Ines Garmendia
job         : Scholarship holder - Research in official statistics
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Purpose of the App

1. To design a dashboard to explore a bunch of items from a questionnaire: the Living Conditions Survey, Basque Government (north of Spain), year 2009.
2. Living condition items (such as health status or number of languages spoken by the person) are visualized as a function of the labour market segmentation, according to which people are classified as occupied, unemployed, occupied in unpaid activities (studying or housekeeping), or retired.
3. Aim is to facilitate exploration of data, in order to find patterns. For example: occupied people speak more languages than the retired. Some  will be obvious, others unexpected.

---

## About the data

Data is coming from two sources of information from the same institution, Eustat - Basque Government Institute for Official Statistics:

1. *The Living Conditions Survey* 2009, in which people where interviewed and gave details about many individual and family dimentions of life  such as health status, working conditions, type of household, social relations, level of instruction, and income.
2. *The Population in Relation to Activity Panel*, 4th quarter of 2009, from which the labour market classification was derived for the same population.

---

## An example
Let's derive one of the tables, i.e. crossing one living conditions item vs labour force segment.


```r
data <- get(load('data.Rda'))
addmargins(prop.table(xtabs( weigths ~ LFS + IncomeLevel, data = data ),1)*100)
```

```
##                           IncomeLevel
## LFS                            Low  Medium    High No response     Sum
##   Occupied                   7.372  49.205  29.249      14.174 100.000
##   Unemployed (unpaid work)  34.873  36.928   9.500      18.699 100.000
##   Unemployed (strict)       21.096  51.783  16.747      10.374 100.000
##   Non-active (unpaid work)  23.429  43.980  14.819      17.771 100.000
##   Retired                   20.792  51.443  13.800      13.966 100.000
##   Sum                      107.562 233.338  84.115      74.985 500.000
```


---

## Visualization method
The chosen visualization method is the *balloon plot*, where the value of each pairs of categories (in this case, % of people in each segment, having each condition) is mapped to the area or radius of a balloon. 

In this way, differences in patterns between distinct segments are highlighted.

---


## Thanks

I hope you enjoy this interactive visualization.
Thanks!

---



