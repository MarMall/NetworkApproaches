---
lab:
    title: 'Lab 20-3-B: Data Transfer from Qualtrics to R'
    module: 'Network Data Collection and Survey Scales'
---

# Lab 20 - M Mallow's RUG teaching lab

## What this sub-lab will teach you

We want to teach you a couple of things in this lab

- Exporting the data from Qualtrics
- Importing the data into R

<!-- - Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph** -->
    
    

## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ ~~Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A~~
+ **Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B**
+ ~~Task 3: Carry out exploratory network analysis in R - Lab 20-4-C~~

(NB: preferably you have collected your own data, but in case that was not possible, or too difficult for some reason, we also provide a sample dataset in the following)

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


    >**Note**: If you have not previously created Management Groups, select **Start using management groups**

1. Create a management group with the following settings:

    | Setting | Value |
    | --- | --- |
    | Management group ID | **az104-02-mg1** |
    | Management group display name | **az104-02-mg1** |

