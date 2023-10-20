---
lab:
    title: 'Lab 20-3-B: Data Transfer from Qualtrics to R'
    module: 'Network Data Collection via Web Surveys'
---

# Marcel's Lab - Part B - Data Transfer from Qualtrics to R

## What this sub-lab will teach you

We want to teach you a couple of things in this lab

- Exporting network data from Qualtrics
- Importing the data into R
- Clearning the data in R
- Getting the data into network format

<!-- - Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph** -->
    
    
## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ ~~Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A~~
+ **Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B**

(NB: preferably you have collected your own data, but in case that was not possible, or too difficult for some reason, we will also provide a sample dataset before the lecture / lab )

<!-- 
![image](../media/lab02a.png)
 -->




### Instructions

## Exercise 1 - Getting your R/R-Studio environment ready

We will be working with with the tidyverse (especially dplyr) in this DataImport and Data Wrangling Sub-Session. These packages need to be installed / loaded in R first.

   ```r 
     # if you are pretty sure you did not install any of the below packages to your R / RStudio environment before, then please run the install-commands
    # otherwise just go to the next code block

    install.packages("tidyverse")
    install.packages("dplyr")
    install.packages("tidyselect")
    install.packages("stringr")  
 
   ```
Loading important packages into R.
   ```r 
    # otherwise load / import the packages you will need for the data import and cleaning / wrangling in this session

    library (tidyverse)
    library (tidyselect)
    library (stringr)
    library (dplyr)
 
   ```

Check what your working directory is, and either put the survey data / network .csv-file in there, or set your working directory to where our .csv file resides on your PC.

```r 
    # otherwise load / import the packages you will need for the data import and cleaning / wrangling in this session

    getwd() #tell you what your working dir is

    setwd() #lets you set a new working directory
```

```r 
# set this to your working directory
setwd("~/yourRProjectName/yourWorkingDir")

responsesFile <- "xyzxWave3raw.csv" #set this to the filename of your downloaded Qualtrics .csv file 

```


## Exercise 2 - Loading the data into R


```r

# #remove row with question
# responses <- responses [-c (1), ] 
# head(responses)

# better way to avoid row with question making everything into character variables
# so we don't have to change them all back again later

responses <- read.csv (responsesFile, header = TRUE, nrows = 1)
variables <- colnames (responses)

#variables
#head(responses)

variables[1] <- "ID"
responses <- read.csv (responsesFile, header = FALSE, skip = 2)
colnames (responses) <- variables

#responses

#rm(QID149)
```

 ## Exercise 3 - Cleaning the data
   ```r
   
    library(igraph)
    library(ggraph)

    relations <- data.frame(from=c("Bob", "Cecil", "Cecil", "David", "David", "Esmeralda"),
                        to=c("Alice", "Bob", "Alice", "Alice", "Bob", "Alice"),
                        weight=c(4,5,5,2,1,1))

    # Load (DIRECTED) graph from data frame 
    g <- graph.data.frame(relations, directed=TRUE)

    # Plot graph
    plot(g, edge.width=E(g)$weight)
   ```


## Exercise 3 - Cleaning the data
   ```r
   
    library(igraph)
    library(ggraph)

    relations <- data.frame(from=c("Bob", "Cecil", "Cecil", "David", "David", "Esmeralda"),
                        to=c("Alice", "Bob", "Alice", "Alice", "Bob", "Alice"),
                        weight=c(4,5,5,2,1,1))

    # Load (DIRECTED) graph from data frame 
    g <- graph.data.frame(relations, directed=TRUE)

    # Plot graph
    plot(g, edge.width=E(g)$weight)
   ```


## Moving on to sub-lab 20-4-C

Please move on to the next [sub-lab 20-4-C](LAB_20-4-C-ExploratoryAnalysisInR.md), where you will do a first exploratory analysis of your network data in R and the igraph package.
