---
layout: default
---

# Welcome to My Portfolio!
#### This site is always growing;)

On this page you will find projects that I have done in Rstudio. 

Below are links to other pages that contain projects that I have done using Tableau, SQL, and Excel.

[Tableau Projects](./another-page.html)

[SQL Projects](./another-page2.html):construction:

[Excel Projects](./another-page3.html):construction:


---
# Rstudio Projects

## _Insurance Analysis_ Project
### Description

In this personal project I analyzed the data set _insurance.csv_ which I found on Kaggle from the user Alexis Cook. The purpose of this analysis was to discover if the following claims were correct or incorrect: older people pay more for health insurance compared to younger individuals, older people have a higher BMI(Body Mass Index) causing their health insurance to be more, and on average the number of older individuals that smoke is greater than younger people. 

#### DISCLAIMER

While this is a personal project, the sample size amongst the ages represented in the data set _insurance.csv_ is not consistent amongst each group. The findings below are accurate pertaining to this data but do not represent the population as a whole.

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

Focusing on the first claim that older people pay more for health insurance compared to young people, we will use the ```max()``` and ```min()``` functions in order to gain insight about the ages we are working with. We will use the ```$``` sign to select the specific variable ```age```.

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
Now that we know the maximum and minimum ages, we can divide the ages into three subsets using the ```subset()``` function. These three subsets will be ```millenials(18-34), gen_x(35-50), and baby_booomers(51-64)```. 

```r
# R code with syntax highlighting
millenials = subset(insurance, age <=34)
gen_x = subset(insurance, age >34 & age < 50)
baby_boomers = subset(insurance, age >51)
```
```r
# R output
```
![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/main/assets/subsets.png)


Now that we have the three subsets setup, we will begin to analyze them. The first analysis we will make involves using the ```mean()``` function to find the average price each group pays. We will use the ```$``` sign to select the specific variable ```charges```.

```r
# R code with syntax highlighting 
mean(millenials$charges)
mean(gen_x$charges)
mean(baby_boomers$charges)
```

```r
# R output
 mean(millenials$charges)
[1] 9673.317
 mean(gen_x$charges)
[1] 13744.29
 mean(baby_boomers$charges)
[1] 18298.07
```

From this function, we can see that on average ```baby_boomers``` pay 18,298.07 for health insurance which means they pay the most compared to the other groups. This discovery makes the first claim that _older people pay more for health insurance compared to younger individuals_ correct.

Let's create a data visualization to show us how age affects the price of health insurance. To do this, we will use ```ggplot()``` which is apart of the ```tidyverse``` package we downloaded at the beginning. We also will use the function ```labs()``` to give the visualization a title and a caption that will contain the data source.

```r
# R code with syntax highlighting 
ggplot(insurance, aes(x=age, y= charges,color=age)) +
  geom_line(stat = "identity") + theme_minimal() +
  labs(title = "Comparing Age to Health Insurance Price",
       caption = "Data source: insurance.csv from Kaggle User Alexis Cook")
```

```r
# R ouput
```
![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/main/assets/datavis.png)

We will move onto answering the second claim now that _older people have a higher BMI(Body Mass Index) causing their health insurance to be more_. To begin answering this claim we will use the ```mean()``` function to find the average BMI of each subset. The ```$``` sign will be used again to select the specific variable ```bmi```.

```r
# R code with syntax highlighting 
mean(millenials$bmi)
mean(gen_x$bmi)
mean(baby_boomers$bmi)
```

```r
# R output
mean(millenials$bmi)
[1] 30.05137
 mean(gen_x$bmi)
[1] 30.5453
 mean(baby_boomers$bmi)
[1] 31.70093
```
Above, we can see that ```baby_boomers``` on average have the higher BMI compared to the other groups. This makes the claim _older people have a higher BMI(Body Mass Index) causing their health insurance to be more_ true.

Lastly, let's answer the last claim that _on average the number of older individuals that smoke is greater than younger people_. To do this we will use the ```count()``` function to see which subset has the most smokers. 

```r
# R code with syntax highlighting 
count(millenials,smoker, sort = TRUE)
count(gen_x,smoker,sort = TRUE)
count(baby_boomers,smoker,sort = TRUE)
```

```r
# R code with syntax highlighting
count(millenials,smoker, sort = TRUE)
  smoker   n
1     no 433
2    yes 116
count(gen_x,smoker,sort = TRUE)
  smoker   n
1     no 314
2    yes  90
count(baby_boomers,smoker,sort = TRUE)
  smoker   n
1     no 269
2    yes  58
```

Looking at the ```yes``` we see that millenials have the most smokers making the claim _on average the number of older individuals that smoke is greater than younger people_ untrue. 

### Conclusion
During this project, we discovered that older people pay more for health insurance compared to younger individuals, older people have a higher BMI(Body Mass Index) causing their health insurance to be more, and that millenials smoke more than the other two groups baby boomers and gen x. Although this was a personal project, these findings have some real world use. Becuase of this analysis people could get an idea for when to expect their health insurance price to increase and how an unhealthy lifestyle could cost them more.


---
## _Prices of Packaging Materials_ Analysis
### Description

In this project, which I did for a Pack Form Distributor, I retreived data from the FRED (Federal Reserve Economic Data) API (Application Programming Interface). The reason I chose to retreive the data from this data base is because most if not all of the data is up to date and clean. The purpose of this analysis was to analyse the three most popular materials(foil, plastic, paper) that this Pack Form Distributor gets requested to see how the prices have flucated in the past five years. The main goal was to create a visualization for the distributor so that he was able to see patterns in the prices of the materials. 

### Process

We will first request a FRED API key which can be found following the link https://fredaccount.stlouisfed.org/apikeys. For security purposes, I will not disclose the key which I was given.

Next, we will install the package ```fredr()``` which provides a complete set of R bindings to the Federal Reserve of Economic Data, the ```ggplot2``` package to create the visualization, and load the packages.

```r
# R code with syntax highlighting
install.packages("fredr")
install.packages("ggplot2")
library(ggplot2)
library(fredr)
library(dplyr)
```

Then we will run the ```fredr_set_key()``` which sets the FRED API key as an environment variable for use with the service.

```r
# R code with syntax highlighting
fredr_set_key("insert FRED API key here")
```

Now we will make three specific requests to the API which will be requests for plastic, paper, and foil data using the ```fredr()``` function and the ```series_id()``` function to specify what data we want using the ids associated with the data. We will also select the specific time frames that we want using the ```observation_start()``` and the ```observation_end()``` functions.

```r
# R code with syntax highlighting
dirty_plastic <- fredr(
series_id = "WPU072A0101",
  observation_start = as.Date("2018-04-15"),
  observation_end = as.Date("2023-04-15")
)


dirty_paper <- fredr(
  series_id = "WPU091303",
  observation_start = as.Date("2018-04-15"),
  observation_end = as.Date("2023-04-15")
)

dirty_foil <- fredr(
  series_id = "PCU3313153313150",
  observation_start = as.Date("2018-04-15"),
  observation_end = as.Date("2023-04-15")
)
```

```r
# R output
```
![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/main/assets/Screenshot%202023-05-15%20at%204.02.09%20PM.png)

Let's now look preview the data sets using the ```head()``` function to see what we are working with

```r
# R code with syntax highlighting
  date       series_id     value realtime…¹ realtime…²
  <date>     <chr>         <dbl> <date>     <date>    
1 2018-04-01 PCU331315331…  209. 2023-05-15 2023-05-15
2 2018-05-01 PCU331315331…  220. 2023-05-15 2023-05-15
3 2018-06-01 PCU331315331…  224. 2023-05-15 2023-05-15
4 2018-07-01 PCU331315331…  215. 2023-05-15 2023-05-15
5 2018-08-01 PCU331315331…  215. 2023-05-15 2023-05-15
6 2018-09-01 PCU331315331…  213. 2023-05-15 2023-05-15
# … with abbreviated variable names ¹​realtime_start,
#   ²​realtime_end
> head(dirty_paper)
# A tibble: 6 × 5
  date       series_id value realtime_start realtime…¹
  <date>     <chr>     <dbl> <date>         <date>    
1 2018-04-01 WPU091303  258. 2023-05-15     2023-05-15
2 2018-05-01 WPU091303  258. 2023-05-15     2023-05-15
3 2018-06-01 WPU091303  257. 2023-05-15     2023-05-15
4 2018-07-01 WPU091303  258. 2023-05-15     2023-05-15
5 2018-08-01 WPU091303  259. 2023-05-15     2023-05-15
6 2018-09-01 WPU091303  258. 2023-05-15     2023-05-15
# … with abbreviated variable name ¹​realtime_end
> head(dirty_plastic)
# A tibble: 6 × 5
  date       series_id   value realtime_s…¹ realtime…²
  <date>     <chr>       <dbl> <date>       <date>    
1 2018-04-01 WPU072A0101  116. 2023-05-15   2023-05-15
2 2018-05-01 WPU072A0101  117. 2023-05-15   2023-05-15
3 2018-06-01 WPU072A0101  117. 2023-05-15   2023-05-15
4 2018-07-01 WPU072A0101  116. 2023-05-15   2023-05-15
5 2018-08-01 WPU072A0101  117. 2023-05-15   2023-05-15
6 2018-09-01 WPU072A0101  118. 2023-05-15   2023-05-15
# … with abbreviated variable names ¹​realtime_start,
#   ²​realtime_end
```

We will now change the data within the ```series_id``` column so it reflects each type of material. To do this, we will use the mutate() function.

```r
# R code with syntax highlighting
cleaner_foil <- dirty_foil%>% 
  mutate(series_id = recode(series_id, PCU3313153313150
= "foil"))

cleaner_paper <- dirty_paper %>% 
  mutate(series_id = recode(series_id, WPU091303
= "paper"))

cleaner_plastic <- dirty_plastic %>% 
  mutate(series_id = recode(series_id, WPU072A0101
= "plastic"))
```

```r
# R output
```
![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/main/assets/Screenshot%202023-05-15%20at%204.09.44%20PM.png)

Now we will combine the data sets into one set called ```materials``` using the ```rbind()``` function

```r
# R code with syntax highlighting
materials <- rbind(cleaner_foil,cleaner_paper,cleaner_plastic)
```

```r
# R output
```
![R Output](https://github.com/Marshall-Kesti/marshallkesti.github.io/blob/main/assets/Screenshot%202023-05-15%20at%204.14.29%20PM.png)

Since we changed the data within the column ```series_id``` in all three of the data sets, we will change the name of the column to ```type``` instead of ```series_id```. Using the ```head()``` function we can see that change.

```r
# R code with syntax highlighting
colnames(materials)[colnames(materials) == "series_id"] <- "type"
head(materials)
```

```r
# R output
 date       type  value realtime_start realtime_end
   <date>     <chr> <dbl> <date>         <date>      
 1 2018-04-01 foil   209. 2023-05-15     2023-05-15  
 2 2018-05-01 foil   220. 2023-05-15     2023-05-15  
 3 2018-06-01 foil   224. 2023-05-15     2023-05-15  
 4 2018-07-01 foil   215. 2023-05-15     2023-05-15  
 5 2018-08-01 foil   215. 2023-05-15     2023-05-15  
 6 2018-09-01 foil   213. 2023-05-15     2023-05-15  
 7 2018-10-01 foil   213. 2023-05-15     2023-05-15  
 8 2018-11-01 foil   209. 2023-05-15     2023-05-15  
 9 2018-12-01 foil   209. 2023-05-15     2023-05-15  
10 2019-01-01 foil   208. 2023-05-15     2023-05-15 
 ```
 
 Finally, we will make a line chart using the ```ggplot()``` function  to show how each type of materials price has changed over the last five year, add the title _Materials Price and Date_, and cite the source of the data by adding a caption.
 
 ```r
 # R code with syntax highlighting
 materials %>% 
ggplot(aes(date, value, colour = type)) +
  geom_line(size = 1) +
  theme_minimal() +
  labs(title = "Materials Price and Date", caption = "Source: U.S. Bureau of Labor Statistics")
  ```
  
  ```r
  ``` # R output
  ```
  ![R Output](https://raw.githubusercontent.com/Marshall-Kesti/marshallkesti.github.io/main/assets/dataviz23.png)
  
### Conclusion
Becuase of this analysis, I was able to find trends in the material pricing that will help the distributor make informed pricing descisions going forward.
