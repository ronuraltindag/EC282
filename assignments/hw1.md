---
output:
  pdf_document: default
---


# Homework Assignment 1
## Deadline: February 20, midnight 

**Source:** Stock and Watson, 4th Edition, Exercise 3.1   

**Data description:** You can find the [data description  here](https://www.dropbox.com/s/7n79v2mjogzxv2j/CPS96_15_Description.pdf?dl=1
). 

## Questions

**a.** In 2015, the value of the Consumer Price Index (CPI) was 237.0. In 1996, the value of the CPI was 156.9. Create a new variable in your data frame that expressed all earnings in real 2015 dollars. Use this variable to answer the next questions.   

**b.** Construct a 95% confidence interval for the mean of ```ahe``` for high school graduates in 1996. 


**c.** Construct a 95% confidence interval for the mean of ```ahe``` for high school graduates in 2015. 


**d.** Construct a 95% confidence interval for the mean of ```ahe``` for college graduates in 1996. 

**e.** Construct a 95% confidence interval for the mean of ```ahe``` for college graduates in 2015.

**f.** Did the inflation adjusted wages of high school graduates increase from 1996 to 2015? Use statistical inference to answer. 

**g.** Did the inflation adjusted wages of collage graduates increase from 1996 to 2015? Use statistical inference to answer.

**h.** Did the gap between earnings of college and high school graduates increase? Use statistical inference to answer. 

## Header for the R script

Start a new R script, copy/paste the header below and save it to ```Dropbox\EC282\Assignment1``` or a similar path that you created for this homework assignment. Run the R script and make sure that you have the data ```df1``` in your environment. Conduct the analysis below the header. 

```

###############################################################################
# list the packages we need and loads them, installs them automatically if we don't have them
# add any package that you need to the list  
need <- c('glue', 'dplyr','readxl',  'ggplot2','tidyr','AER','scales','mvtnorm', 
          'stargazer','httr', 'repmis')

have <- need %in% rownames(installed.packages()) 
if(any(!have)) install.packages(need[!have]) 
invisible(lapply(need, library, character.only=T)) 

# Save the R script to the assignment 1 folder before this
# To set up the working directory
getwd()
setwd(getwd()) #change getwd() here is you need to set a different working directory


#this clears the workspace
rm(list = ls()) 
#this sets the random number generator seed to my birthday for replication


options(scipen=999)
###############################################################################
#get the data url 
df1.url <- 'https://www.dropbox.com/s/hbi82scuz9q4k11/CPS96_15.xlsx?dl=1'
#download the data 
GET(df1.url, write_disk(tdf <- tempfile(fileext = ".xlsx")))
#check if it worked
df1 <- read_excel(tdf) %>%
  mutate(ahe = ahe + rnorm(length(ahe)))



head(df1)

# CONDUCT THE ANALYSIS BELOW

```
