---
lab:
    title: 'Lab 20-4-C: Exploratory Network Data Analysis in R'
    module: 'Network Data Collection via Web Surveys'
---

# Marcel's Lab - Part C - Exploratory Network Data Analysis in R with igraph


## Pre-Lab requirements

You need to have R (preferably a recent version) installed on a Linux, Windows or MacOS PC.
You should have connected to [Qualtrics via the RUG-MyUniversity access](https://rug.eu.qualtrics.com/).

   ```r
    # Check that you have iplot installed in your R

    library(igraph)
    
   ```


## What this sub-lab will teach you

- how to visually explore your network data in R and igraph
- how to use visualisations to preliminary support or reject your hypothesis

<!-- - Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph** -->
    
    

## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ ~~Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A~~
+ ~~Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B~~
+ **Task 3: Carry out exploratory network analysis in R - Lab 20-4-C**


## Estimated timing for this lab session: ~ 20 minutes

## Architecture diagram
<!-- 
![image](../media/lab02a.png)
 -->

### Instructions

## Exercise 1


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
