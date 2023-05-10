---
layout: default
---

# Welcome to My Portfolio!
Below you will find projects that I have done in Rstudio, Tableu, SQL and Excel.


---
# Rstudio Projects

## _Insurance Analysis_ Project
### Description

In this personal project I analyzed the data set _insurance.csv_ which I found on Kaggle from the user Alexis Cook. The purpose of this analysis was to discover if the following claims were correct or incorrect: baby boomers pay more for health insurance compared to millenials and gen x, baby boomers have a higher BMI(Body Mass Index) causing their health insurance to be more, and on average the number of baby boomers that smoke is greater than the other two groups, millenials and gen x.

### Process

The first thing we will do is download ```tidyverse()``` which is the package we will use for this analysis, the data set we will be working with ```insurance.csv```, and the ```head()``` function. Then, we will use the ``head`` function to preview the data.

```r
# R code with syntax highlighting
install.packages(tidyverse)
library(tidyverse)
insurance <- read.csv("insurance.csv")
install.packages(head)
library(head)
head(insurance)
```
```r
# head() output
1. age    sex    bmi children smoker    region   charges
2. 19 female 27.900        0    yes southwest 16884.924
3. 18   male 33.770        1     no southeast  1725.552
4. 28   male 33.000        3     no southeast  4449.462
5. 33   male 22.705        0     no northwest 21984.471
6. 32   male 28.880        0     no northwest  3866.855
7. 31 female 25.740        0     no southeast  3756.622
```

