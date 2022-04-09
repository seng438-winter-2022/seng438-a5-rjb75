# Assignment 5

**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #5 – Software Reliability Assessment**

| Group \#: 14   |   |
|----------------|---|
| Student Names: | Robert Brown (10180520) |
|                | Brooke Kindleman (30090660) |
|                | Risat Haque (30094174) |
|                | Amnah Hussain (30095907) | 

# Introduction

In this lab, we analyzed the reliability of software with the data provided in the lab using Reliability Growth Testing and Reliability Demonstration charts. Unlike previous labs, we examined the effectiveness of testing and software through 2 methods with data provided within the lab. We use the Reliability Growth Testing with the C-SFRAT tool in the first part. Here, we plot the failure and reliability of the SUT based on the failure data provided. Our report will discuss the effectiveness of the tool and the outcomes based on the dataset provided. The second section dives into the Reliability Demonstration Chart, which again uses a dataset provided. We examine trends in the system's reliability and MTTF-min to determine the reliability of the software. 

# ****Assessment Using Reliability Growth Testing****

**Result of model comparison (selecting top two models)**

The top two models were selected through comparing the log-likelihood’s of all the combinations of covariates and models, as the value of log-likelihood interprets the best fit of the data set, it is used to rank the models according to the log-likelihood (the higher the log-likelihood, the better the fit). With the given values of log-likelihood, it can be seen that the models DW3 and IFRGSB have the highest values. 

![Untitled](Assignment%20f1db6/Untitled.png)

Therefore the chosen top two models were DW3 and IFRGSB, and the top combinations include DW3(F, C), DW3(F), IFRGSB(E, F,C), IFRGSB(E,F), IFRGSB(F,C), IFRGSB(F).

![Untitled](Assignment%20f1db6/Untitled%201.png)

**Result of range analysis (an explanation of which part of data is good for proceeding with the analysis)**

In terms of the subset failure data used the original amount was set at 31 but that provided a limited amount of combination results compared to the 56 we were supposed to get, therefore we set it to 29 as it provided the most combinations of covariates and models to work with, allowing for more accurate ranking of the different models. Additionally, in the case of the Log-Likelihood the values between and including -52.865 and -55.582 are used in the proceeding analysis as it follows values calculated in the model ranking.

**Plots for failure rate and reliability of the SUT for the test data provided**

Time-between-failures graph:

![Untitled](Assignment%20f1db6/Untitled%202.png)

Failure Intensity Graph:

![Untitled](Assignment%20f1db6/Untitled%203.png)

Reliability Graph:

![Untitled](Assignment%20f1db6/Untitled%204.png)

**A discussion on decision making given a target failure rate**

With the use of the C-SFRAT tool, as seen in the reliability graph, the target failure rate was set to be 0.4 as this allowed each of the combination of covariates and models chosen to have the ability to predict the number of additional intervals to achieve that set failure rate. For each combination it can be seen that the additional intervals require for each of them are,

- DW3(F, C) has 59 additional failure intervals
- DW3(F) has 42 additional failure intervals
- IFRGSB(E, F,C) has 16 additional failure intervals
- IFRGSB(E,F) has 15 additional failure intervals
- IFRGSB(F,C) has 14 additional failure intervals
- IFRGSB(F) has 12 additional failure intervals

As the most failure intervals was from DW3(F, C) and was at a total of 88 (59+29), the MTTF would be 0.4/88, which is 0.0045.

**A discussion on the advantages and disadvantages of reliability growth analysis**

**Advantages:**

- Provides quantitative results for the reliability of the system. This can help in the decision making process on whether a product is ready for release or not.
- Estimating failure intensity for large programs.
- Flexibility allowed based on the data used.

**Disadvantages:**

- The results are estimates and may not be the most accurate.
- Outdated tools may not reflect changes in development from past year. Some of these tools are dated as back as 1993, and since then, software has changed. These tools may not support new functionalities.
- May not be accurate with smaller programs with less lines of code. Can result in inaccurate data.

# ****Assessment Using Reliability Demonstration Chart****

The following charts utilize the dataset provided in the lab. The excel sheet was used to generate this graph. Note that the excel sheet was modified to accommodate this lab's number of data points. 

## MTTFMin

![Untitled](Assignment%20f1db6/Untitled%205.png)

The above graph shows the plot for MTTFmin for the provided input data which we determined to be 100/230,000 = 0.000435.

## 1/2 x MTTFmin

![Untitled](Assignment%20f1db6/Untitled%206.png)

The above graph shows the plot for 1/2 x MTTFmin for the provided input data which we took as 50/230,000 = 0.000217.

## 2 x MTTFmin

![Untitled](Assignment%20f1db6/Untitled%207.png)

The above graph shows the plot for 2 x MTTFmin for the provided input data which we took as 200/230,000 = 0.000870. By doubling the MTTF, we see an increased number of failures in the accept region of the graph.

**Evaluation and Justification of MTTFmin**

Based on the original graph of **MTTFmin** , the selected value is when the FIO is 100 failures per 230,000 calls. This value was chosen through trial and error to have the graph ending in the acceptable range (1 point barely entering the good range). By dividing the acceptable number of failures by the per number of input events, we approach the `0.000435` mark for the **MTTFmin**. When decreasing the value of the call to 100,000, we notice that the plot graph has a substantial section in the acceptable range, resulting in an incorrect chart. Alternatively, having the value increased to 500,000, the plot graph falls in the reject region. We hover around the 220,000 - 240,000 range through trial and error to get the plots to end after the acceptable and continue-to-test boundary. 

Note that throughout this part of the lab, we maintained the original value of the Discrimination Ratio, Developer's Risk, and User's Risk parameters at 2.0, 0.1, and 0.1, respectively. 

**Advantages of RDC**

- Time and cost-efficient method to analyze reliability in a system. This can assist in the decision-making process to accept or reject a SUT. Furthermore, this can help estimate how much testing remains in the project if the SUT is not accepted.
- Visually recognize the evolution of errors and reliability over time and changes within the internal system. This allows for a closer analysis of the error rate and how the SUT grows with time.

**Disadvantages of RDC**

- A Tedious process when experimenting with **MTTFmin** to meet the criteria of the RDC. A lot of trial and error was used to create a graph that makes sense.
- A visual approach can be less accurate than a mathematical approach. Mathematical approaches tend to be more precise.
- Inability to determine quantitative numbers for reliability. This includes how trends change and how they affect reliability.

# ****Comparison of Results****

When comparing the different results that were generated using the test data we were able to better understand the overall reliability of the system. In part 1, we determine an MTTF is  `0.0045` while in part 2, the **MTTFmin** is `0.000435`. The values are separated by a factor of 10 which indicates that they are quite different quantitatively. This can be due to the fact that part 2 calculates the MIN value, and part 1 maybe an average value, which can be much higher. We imagine that part 1 is more accurate since part 2 was calculated visually with a trial and error approach while part 1 was calculated mathematically. 

# ****Discussion on Similarity and Differences of the Two Techniques****

A similarity between both techniques is that they can assess data based on their failure times and failure intensity. This was evident when determining the **MTTFmin** in part 2 of the lab. Based on reliability, both techniques can help determine whether the SUT is ready for release. This supports the decision-making process in software.   

Alternatively, part 1 provides quantitative values for the system's availability and reliability. While part 2 (RDC) only indicates whether a system falls in the acceptable (or other) ranges based on the data set. In addition, RDC allows for experimentation based on hypothetical scenarios when “playing around” with the **MTTFmin** and the system's confidence levels.  

# How the teamwork/effort was divided and managed

As a result of some of the challenges presented by operating system incompatibilities our team split the different methods in pairs to ensure that we all had access to a windows machine to run the software. Before starting the core components of the lab, we each attempted to run software in both parts. With unprecedented difficulties in running various tools, we selected sub-teams based on tools that ran in our respective machines. Amnah and Brooke mainly worked with the Reliability Growth Testing. Risat and Robert primarily worked with the Reliability Demonstration Chart. We tried to work as an entire group where possible. Otherwise, we would present any findings to the larger team when worked on individually. After completing each section, we formally discussed our results to understand the entirety of the lab and asked questions to each other about our findings. Then, we split up the report evenly among us and reviewed each section individually. After reviewing each document independently, we further discussed the answers to questions in the laboratory rubric and submitted the final assignment. 

# Difficulties encountered, challenges overcome, and lessons learned.

One of the most significant challenges was the initial setup of the software on various machines. In part 1, we installed both applications but struggled to get them to work successfully in our respective operating systems. Through trial and error and with TA support, we could get it working on select systems. In addition, the software would occasionally freeze and cause delays in completing the section. In part 2, we struggled to understand how the excel sheet worked. We had to familiarize ourselves with the terminologies and understand how different components in the excel sheet worked with one another. We also struggled to realize that we needed to expand the number of data points the graph took. The provided excel sheet supported approximately 16 data points, while our data set required over 100. Understanding how to do this became challenging and made this laboratory significantly harder. We would need a better understanding of how the tools work and work with given resources (such as TAs).  

# Comments/feedback on the lab itself

This lab was quite challenging since not enough information was provided on how the tools work. Each tool came with its challenges with minimal instructions and time to execute. Furthermore, we are only offered one lab session to get TA support. This was also the same day the lab was released, which does not provide enough time to generate questions for TAs. It would have made sense to allocate an additional lab to ask questions and learn from the technical challenges proposed by the lab.
