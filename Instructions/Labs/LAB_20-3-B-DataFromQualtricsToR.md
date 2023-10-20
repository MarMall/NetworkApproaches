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

#alternatively, you can use our class dataset (which I uploaded here to GitHub)
responsesFile <- "https://raw.github.com/MarMall/NetworkApproaches/main/Instructions/Labs/data/sampleNetworkSurvey.csv"

```

## Exercise 2 - Loading the data into R

```r

# #remove row(s) with question
# responses <- responses [-c (1), ] 
# head(responses)

#better way to avoid row with question recoding everything into character variables
#so we don't have to change them all back again later

#setwd("~/surveyDataImport/waves")

# readr::

responses <- read.csv (responsesFile, header = TRUE, nrows = 1)
variables <- colnames (responses)

#variables
#head(responses)

# variables[1] <- "ID"
responses <- read.csv (responsesFile, header = FALSE, skip = 2)
colnames (responses) <- variables

## Here you have your dataframe of all the responses
# have a look inside
responses 

```

## Exercise 3 - First network relation - Friendship
   
```r
   ## Now lets recode the first question results into network format

#responses to first question -- selection by question number

## exclude 99 as this is "Nobody"
QID149 <- responses %>%
  select (c (
            #"ID",
             #"recipientLastName",
             # "QID169_1",
             vars_select (names (responses),
                          starts_with ("QID149", ignore.case = TRUE),
                          -starts_with ("QID149_99", ignore.case = TRUE) #filter out NOBODY
                          )))


QID149 <- QID149[1:14] #we only have 14 responses, so we work only with those.
#QID149

```

## Exercise 4 - Second network relation - Influence
   
```r
## exclude 99 as this is "Nobody"
QID128 <- responses %>%
  select (c (
            #"ID",
             #"recipientLastName",
             # "QID169_1",
             vars_select (names (responses),
                          starts_with ("QID128", ignore.case = TRUE),
                          -starts_with ("QID128_99", ignore.case = TRUE)
                          )))


# QID128 <- QID128[2:7]

QID128 <- QID128[1:14] # again, we only had 14 responses to the survey
#QID128


QID128 <- QID128 %>%
  # Recoding NAs to 0  
  mutate (across (vars_select (names (QID128),
                               contains ("QID128", ignore.case = TRUE)),
          ~ replace (., is.na (.), 0))) %>%
  ## AND making the data binary
    mutate (across (vars_select (names (QID128),
                               contains ("QID128", ignore.case = TRUE)),
          ~ replace (., . != 0, 1))) #this ensures the data is binary



dim(QID128) # nice, this is squared 14x14

#QID128

```

## Exercise 5 - Turning the data into a matrix

```r turningIntoMatrix
# 
# QID149 # friendship relation
# QID128 # influence

QID149_mat <-  as.matrix(QID149)

#QID149_mat
is.matrix(QID149_mat)

# checking the dimensions of the matrix
#dim(QID149_mat) # should be symmetric

##same for the influence relation

QID128_mat <-  as.matrix(QID128)

# # checking the dimensions of the matrix
# dim(QID128) # should be symmetric

#QID128_mat
is.matrix(QID128_mat)

```

## Saving your network relation matrices in R

```r savingNetworkMatrices

# save the matrices as .RData files

save (QID149_mat,
        file = paste0 ("Friendship_q149"  ,".Rdata"))

save (QID128_mat,
        file = paste0 ("Influence_q128"  ,".Rdata"))

```

## Achievements

Great, you bought your first network relations into (adjacency) matrix format, so that working with them in several network analysis packages in R will be much easier.


## Moving on to sub-lab 20-4-C

Please move on to the next [sub-lab 20-4-C](LAB_20-4-C-ExploratoryAnalysisInR.md), where you will do a first exploratory analysis of your network data in R and the igraph package.
