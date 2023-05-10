---
layout: default
---

# Welcome to My Portfolio!
Below you will find projects that I have done in Rstudio, Tableu, SQL and Excel.


---
# Rstudio Projects

## _Insurance Analysis_ Project
### Description

In this personal project I analyzed the data set _insurance.csv_ which I found on Kaggle from the user Alexis Cook. The purpose of this analysis was to discover if the following claims were correct or incorrect: older people pay more for health insurance compared to younger individuals, older people have a higher BMI(Body Mass Index) causing their health insurance to be more, and on average the number of older individuals that smoke is greater than younger people.

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
# R output
1. age    sex    bmi children smoker    region   charges
2. 19 female 27.900        0    yes southwest 16884.924
3. 18   male 33.770        1     no southeast  1725.552
4. 28   male 33.000        3     no southeast  4449.462
5. 33   male 22.705        0     no northwest 21984.471
6. 32   male 28.880        0     no northwest  3866.855
7. 31 female 25.740        0     no southeast  3756.622
```
![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/9b475f2349fd175a6b29f14ddf5f41a0dbaa754e/assets/Outpu1.png)

Focusing on the first claim that older people pay more for health insurance compared to young people, we will use the ```max()``` and ```min()``` functions in order to gain insight about the ages we are working with.

```r
# R code with syntax highlighting
max(insurance$age)
min(insurance$age)
```
```r
# R output
 max(insurance$age)
[1] 64
 min(insurance$age)
[1] 18
```
Now that we know the maximum and minimum ages, we can divide the ages into three subsets using the ```subset()``` function. These three subsets will be ```millenials(18-34), gen x(35-50), and baby booomers(51-64)```. 

```r
# R code with syntax highlighting
Millenials = subset(insurance, age <=34)
Gen_X = subset(insurance, age >34 & age < 50)
Baby_Boomers = subset(insurance, age >51)
```
```r
#R output
```
![R Output]([https://marshall-kesti.github.io/assets/Outpu2.png](https://viewscreen.githubusercontent.com/added/img?color_mode=auto&commit=9b475f2349fd175a6b29f14ddf5f41a0dbaa754e&enc_url=68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f4d61727368616c6c2d4b657374692f6d61727368616c6c6b657374692e6769746875622e696f2f396234373566323334396664313735613662323966313464646635663431613064626161373534652f6173736574732f4f75747075322e706e67&path=assets%2FOutpu2.png&repository_id=638533525#32dcf0c7-77ed-4398-a9ee-6b1a637be831))
