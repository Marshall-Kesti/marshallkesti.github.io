---
layout: default
---

# Welcome to My Portfolio!
Below you will find projects that I have done in Rstudio, Tableu, SQL and Excel.


---
# Rstudio Projects

## _Insurance Analysis_

In this personal project I analyzed the data set _insurance.csv_ which I found on Kaggle from the user Alexis Cook. The purpose of this analysis was to discover if the following claims were correct or incorrect: baby boomers pay more for health insurance compared to millenials and gen x, baby boomers have a higher BMI(Body Mass Index) causing their health insurance to be more, and on average the number of baby boomers that smoke is greater than the other two groups, millenials and gen x.

### The first thing we will do is download ```tidyverse()``` which is the package we will use for this analysis, the data set we will be working with ```insurance.csv```, and the ```head()``` function so that we can preview what the data set. 

```r
# R code with syntax highlighting
install.packages(tidyverse)
library(tidyverse)
insurance <- read.csv("insurance.csv")
install.packages(head)
library(head)
head(insurance)
```
