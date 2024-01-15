R and RStudio

## Install R

1. [Click here to go to R homepage](https://cran.r-project.org/)
2. Choose your operating system.

### For Windows

1. Click on `install R for the first time`.
2. Click on `Download R-4.3.2 for Windows` and install.

### For Mac

1. Choose the framework corresponding to your macOS version and install.

## Install RStudio

1. [Click here to go to the RStudio download page](https://www.rstudio.com/products/rstudio/download/#download).
2. Download RStudio Desktop Recommended for your system.
3. Once installed, run RStudio. In the top left corner, click on `File -> New File -> R Script`.

4. Copy and paste the following code header into the new script. Select all (Ctrl+A) and run the script. If it executes successfully and you see an object `wage2` in the Environment tab, you're ready to start.

```{r setup, include=FALSE}
# Minimal R setup for empirical analysis
need <- c('dplyr', 'ggplot2', 'wooldridge')
have <- need %in% rownames(installed.packages())
if(any(!have)) install.packages(need[!have])
invisible(lapply(need, library, character.only = TRUE))

# Clear the workspace
rm(list = ls())

# Set random number generator seed for reproducibility
set.seed(12345)

# Set options
options(scipen = 999)

# Load 'wage2' data from the 'wooldridge' package
data("wage2", package = "wooldridge")
View(wage2)