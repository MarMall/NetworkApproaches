---
lab:
    title: 'Lab 20-2-A: Implementing Research Idea in Qualtrics'
    module: 'Network Data Collection and Survey Scales'
---

# Lab 20 - M Mallow's RUG teaching lab
# Student lab manual

## Pre-Lab requirements

You need to have R (preferably a recent version) installed on a Linux, Windows or MacOS PC.
You should have connected to [Qualtrics via the RUG-MyUniversity access](https://rug.eu.qualtrics.com/).

## What this sub-lab will teach you

We want to teach you a couple of things in this lab

- How to think about integrated data collection
    - i.e. network-specific data (relations)
    - with individual-specific data (attributes)

- How to implement this in a streamlined Qualtrics and R workflow
    - by first designing a survey in Qualtrics
    - collecting the data
    - importing the data into R

- Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph**
    
    

## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ **Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A**
+ Task 2: Import the collected data into R - Lab 20-2-B
+ Task 3: Carry out exploratory network analysis in R - Lab 20-2-C

(NB: Task 1 should be carried out as preparatory work before the lab session, and Task 2 and 3 are carried out during the lab session)

## Estimated timing for this lab session: ~ 45 minutes

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


## Task 1: Implement Management Groups

In this task, you will create and configure management groups. 

1. Sign in to the [**Azure portal**](http://portal.azure.com).

1. Search for and select **Management groups** to navigate to the **Management groups** blade.

1. Review the messages at the top of the **Management groups** blade. If you are seeing the message stating **You are registered as a directory admin but do not have the necessary permissions to access the root management group**, perfom the following sequence of steps:

    1. In the Azure portal, search for and select **Azure Active Directory**.
    
    1.  On the blade displaying properties of your Azure Active Directory tenant, in the vertical menu on the left side, in the **Manage** section, select **Properties**.
    
    1.  On the **Properties** blade of your your Azure Active Directory tenant, in the **Access management for Azure resources** section, select **Yes** and then select **Save**.
    
    1.  Navigate back to the **Management groups** blade, and select **Refresh**.

1. On the **Management groups** blade, click **+ Create**.

    >**Note**: If you have not previously created Management Groups, select **Start using management groups**

1. Create a management group with the following settings:

    | Setting | Value |
    | --- | --- |
    | Management group ID | **az104-02-mg1** |
    | Management group display name | **az104-02-mg1** |

