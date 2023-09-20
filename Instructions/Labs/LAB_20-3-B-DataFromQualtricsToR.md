---
lab:
    title: 'Lab 20-3-B: Data Transfer from Qualtrics to R'
    module: 'Network Data Collection and Survey Scales'
---

# Marcel's Lab - Part B - Data Transfer from Qualtrics to R

## What this sub-lab will teach you

We want to teach you a couple of things in this lab

- Exporting network data from Qualtrics
- Importing the data into R

<!-- - Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph** -->
    
    
## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ ~~Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A~~
+ **Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B**

(NB: preferably you have collected your own data, but in case that was not possible, or too difficult for some reason, we will also provide a sample dataset before the lecture / lab )

## Estimated timing for this lab session: ~ 20 minutes

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





   ```r 
    # otherwise load / import the packages you will need for the data import and cleaning / wrangling in this session

    library (tidyverse)
    library (tidyselect)
    library (stringr)
    library (dplyr)
 
   ```



## Exercise 1

1. 

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
