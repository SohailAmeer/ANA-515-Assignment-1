# ANA-515-Assignment-1
Week 1 Activity: R Markdown


---
title: "ANA 515 Assignment 1"
author: "Mohammed Sohail Ameer"
date: "27/08/2022"
output:
  html_document:
    theme:
      bootswatch: minty
  pdf_document: default
  word_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
```{r}
#install.packages("tidyverse")
#install.packages("knitr")
#install.packages("bslib")
```
```{r}
library(tidyverse)
library(knitr)
library(bslib)
```
```{r}
mydata <- read_csv("https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv")
```
```{r}
youth<-filter(mydata, age <= 65) 
youth
summary(youth)
```
#Gun deaths by age
```{r youth-dist, echo=FALSE}
youth %>%
  ggplot(aes(x=age))+
  geom_freqpoly(binwidth=1)

```
#Gun deaths by race
```{r race-dist, echo=FALSE}
youth %>%
  ggplot(aes(x=fct_infreq(race)%>%fct_rev()))+
  geom_bar() + coord_flip() +
  labs(x="Victim race")
```

