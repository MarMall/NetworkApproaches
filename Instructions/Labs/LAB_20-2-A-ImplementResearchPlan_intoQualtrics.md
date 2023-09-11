---
lab:
    title: 'Lab 20-2-A: Implementing Research Idea in Qualtrics'
    module: 'Network Data Collection and Survey Scales'
---

# Lab 20 - M Mallow's RUG teaching lab

## Pre-Lab requirements

You need to have R (preferably a recent version) installed on a Linux, Windows or MacOS PC.
You should have connected to [Qualtrics via the RUG-MyUniversity access](https://rug.eu.qualtrics.com/).

## What this sub-lab will teach you

- How to create a quick network-roster type survey for network-specific data collection...
    - capturing **network-specific relational data** between individuals of a defined population (within boundary
    - adding **non-network specific data** to the network data collection
        - demographic information
        - depending on research ideas specifically designed question scales

- Kick-Off Data Collection
    - How to distribute the survey to your population of interest
    - How to monitor the data collection process
    

## Sub-Lab's Objective

This lab is divided into three sub-sections (for better orientability), and in the separate sub-modules you will:

+ **Task 1: Implement your research plan (and hypothesis into a Qualtrics survey) - Lab 20-2-A**
+ ~~Task 2: Network Data - Export from Qualtrics and Import into R - Lab 20-3-B~~
+ ~~Task 3: Carry out exploratory network analysis in R - Lab 20-4-C~~

(NB: preferably you have collected your own data, but in case that was not possible, or too difficult for some reason, we also provide a sample dataset in the following)

## Estimated timing for this lab session: ~ 45 minutes

<!-- 
![image](../media/lab02a.png)
 -->

### Instructions

## Exercise 1 - (Conceptual) Survey Framework

- Make a nice layout of your data bits and pieces.
    - i.e. the network relations you want to capture,
    - the directionality of those relations
    - the non-network information you want to capture

<!-- 
![image](../media/lab02a.png)
 -->


## Task 1: Go ahead in Qualtrics

In this task, you will create and configure your survey. There are many different ways of collection network type data (see slides), but one of the most common is the **roster type survey**. In this type of survey, you first define the population of interest, and then you ask respondents to indicate their relations to other members of the population.

1. Sign in to the [**RUG - Qualtrics account**](https://rug.eu.qualtrics.com/).

1. Then go to [Create a project](https://rug.eu.qualtrics.com/app/catalog/projects) or [Create your first survey] (https://rug.eu.qualtrics.com/app/catalog/projects/results?search=survey) **and** then create a survey **from scratch** (as shown in the following screenshot).

    ![image](../media/lab20-2a-01-fromScratch.png)

    1. then give your survey project a name (e.g. **Lab 20-2-A**), and click **Create Survey**.
    
    1. From here you will have two options...

        
        1. either, you can build on a template that we have created for you (which is the recommended way forward for this lab)
        1. or, you can create your very own little network survey from scratch (based on examples you find in the SNA literature)

        You see both options shown in the following screenshot. Please choose accordingly.
        
        ![image](../media/lab20-2a-02-chooseTemplateOrNot.png)

        >**Note**: If you have not previously worked with Qualtrics or other online survey tools, you might want to look at the following link on [Survey component basics](https://www.qualtrics.com/support/survey-platform/survey-module/survey-module-overview/)


## Task 2: Importing the .qsf file for survey import

1. The recommended way forward is to use our pre-built **network roster-type** questions, which you can load via this [.qsf file](https://unishare.nl/index.php/s/JdwMseKp6oTEbWJ) that we have made available on UniShare (link: https://unishare.nl/index.php/s/JdwMseKp6oTEbWJ). In case you want to build your very own network survey without any help, please skip this task.

>**Note**: please look up the official Qualtrics documentation for more help on [Importing and Exporting surveys] (https://www.qualtrics.com/support/survey-platform/survey-module/survey-tools/import-and-export-surveys/#ExportingaSurveyasaQSF)


## Task 3: Modify the survey questions to match your research ideas

1. modify the survey items, as well as structure and logic to match your **(Conceptual) Survey Framework** (see above)
1. test your survey via the "Preview" button on the top right

## Task 4: Test your online-survey

1. (pre-)test your survey via the "Preview" button on the top right

## Task 5: Collect your data

1. when you are fairly certain that the survey is running flawless and collects the your network data as desired, click on the "Publish" button to go from testing to data collection mode.

## Task 6: Export the data for Data Analysis and Exploration

1. ...
1. ...
