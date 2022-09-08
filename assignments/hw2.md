---
output:
  pdf_document: default
---


# Homework Assignment 2
## Deadline: March 6, midnight 

**Source:** Stock and Watson, 4th Edition, Exercise 4.1   

**Data description:** You can find the [data description  here](https://www.dropbox.com/s/3e24u6eymvmhldd/Growth_Description.pdf?dl=1
). 


## Questions 

**a.** Construct a scatterplot of ```growth``` and ```tradesshare``` with a regression line fit on the top. 

**b.** Look at the data set and find Malta on your graph. Why is Malta an outlier? 

**c.** Using all the observations run a regression of ```growth``` on ```tradeshare```. Interpret the intercept and the slope. Predict the growth rate for a country with a trade share of 0.5 and another with a trade share equal to 1. 

**d.** Estimate the regression without Malta and interpret the coefficients. Should Malta be excluded from the regression? Briefly comment.  


## Header for the R script

Start a new R script, copy/paste the header below and save it to ```Dropbox\EC282\Assignment2``` or a similar path that you created for this homework assignment. Run the R script and make sure that you have the data ```df1``` in your environment. Conduct the analysis below the header. 

```
###############################################################################
# list the packages we need and loads them, installs them automatically if we don't have them
# add any package that you need to the list  
need <- c('glue', 'dplyr','readxl', 'ggplot2','tidyr','AER','scales','mvtnorm', 
          'stargazer','httr', 'repmis')

have <- need %in% rownames(installed.packages()) 
if(any(!have)) install.packages(need[!have]) 
invisible(lapply(need, library, character.only=T)) 

# Save the R script to the assignment 2 folder before this
# To set up the working directory
getwd()
setwd(getwd()) #change getwd() here is you need to set a different working directory


#this clears the workspace
rm(list = ls()) 
#this sets the random number generator seed to my birthday for replication

options(scipen=999)
###############################################################################
#get the data url 
df1.url <- 'https://www.dropbox.com/s/lbk73b0amzfj8px/Growth.xlsx?dl=1'
#download the data 
GET(df1.url, write_disk(tdf <- tempfile(fileext = ".xlsx")))
#check if it worked

df1 <- read_excel(tdf) %>%
  mutate(growth = growth + rnorm(length(growth))/5)



head(df1)

#CONDUCT THE ANALYSIS BELOW

```
