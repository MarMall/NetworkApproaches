---
lab:
    title: 'Lab 20-4-C: Exploratory Network Data Analysis in R'
    module: 'Network Data Collection via Web Surveys'
---

# Marcel's Lab - Part C - Exploratory Network Data Analysis in R with igraph



   ```r
    # Check that you have iplot installed in your R

    library(igraph)
    
    #otherwise, please install first via install.packages("igraph")
   ```


## What this sub-lab will teach you

- how to visually explore your network data in R and igraph


<!-- - Doing exploratory network analysis in R
    - processing and exploring the data in a network-specific R-package such as **igraph** -->
    
    

## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ ~~Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A~~
+ ~~Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B~~
+ **Task 3: Carry out exploratory network analysis in R - Lab 20-4-C**


### Instructions

## Exercise 1

Let's load our two network relations from before into R and see what we can do with them.

   ```r
   library(igraph) # load the igraph package for later 

#loading our matrices
load (paste0("~/NetworkSurvey/", "Friendship_q149", ".Rdata"))
load (paste0("~/NetworkSurvey/", "Influence_q128", ".Rdata"))
    
   ```


## Exercise 2


```r
   friendship_network <- graph_from_adjacency_matrix(QID149_mat)
influence_network <- graph_from_adjacency_matrix(QID128_mat)


# Comparing network metrics such as density
igraph::graph.density(friendship_network)
igraph::graph.density(influence_network)

## Listing all available shapes 
# shapes()

V(friendship_network)$vertex.shape <- "square"
# V(friendship_network)$name <- c("bli", "bla", "blubbi", "shrubby", "puppy", "muppy")


V(friendship_network)$name <- responses$QID169_1
V(influence_network)$name <- responses$QID169_1


plot(friendship_network) # wow, this is a mess!

# better without vertex labels?
plot(friendship_network
     ,vertex.size = 15
     ,vertex.color = "lightblue"
     ,vertex.label=NA
     )

#Interesting to see our friendship network in text form
E(friendship_network)


#Edge lists are, apart from adjacency matrices a very common way of building networks
friendship_EL <- as_edgelist(friendship_network)
influence_EL <- as_edgelist(influence_network)

```

## Exercise 3

How can we show more than one type of tie in a network without overlap?

   ```r
   
    multiplexNetwork <- graph_from_edgelist(friendship_EL)

E(multiplexNetwork)$type <- "friendship"

E(multiplexNetwork)$type
# multiplexNetwork

multiplexNetwork_V2 <- add.edges(multiplexNetwork, edges = influence_EL)

E(multiplexNetwork_V2)$type[38:56] <- "influence"
E(multiplexNetwork_V2)$type


E(multiplexNetwork_V2)$width <- 2
plot(multiplexNetwork_V2, edge.color=c("dark red", "slategrey")[(E(multiplexNetwork_V2)$type=="friendship")+1],
      vertex.color="gray40", layout=layout_in_circle, edge.curved=.3)

   ```


## Exercise 4

Self-loops are a common problem in network data. How can we get rid of them? In our case, it does not make sense to be a friend of oneself, or to influence oneself.


```r	

#getting rid of the self-loops

multiplexNetwork_V2 <- igraph::simplify(multiplexNetwork_V2, remove.loops = T, remove.multiple = F)

E(multiplexNetwork_V2)$width <- 2
plot(multiplexNetwork_V2, edge.color=c("dark red", "slategrey")[(E(multiplexNetwork_V2)$type=="friendship")+1],
      vertex.color="gray40", layout=layout_in_circle, edge.curved=.3)

```