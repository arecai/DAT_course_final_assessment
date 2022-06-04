# HOUSE PRICE ANALYSIS FOR WASHINGTON HELP PEOPLE ORGANIZATION

***Author:*** Ariadna Recasens


## Project Overview

In this project, we help the non-for-profit Washinton Help People organization to find the most afforadable houses. 


### Business problem
The non-for-profit Washinton Help People organization (WHPO)has recently received an anonymous donation to build the most number of houses for homeless people. Herein,WHOW wants to get some insights to find the cheapest houses so they can buy more houses to help more homelesses. In this project, we will use regression models to identify the factors that has a signficant impact in the house price. 

Some of the questions that we will consider are:

What are the zipcodes wehre the houses are most expensive?
What factors influece the houses price?



### The Data

This project uses the King County House Sales dataset. This dataset contains house sale prices for King County, which includes Seattle. It includes homes sold between May 2014 and May 2015.

The dataset contains 21597 entries and 21 columns. This project will focus on the following variables:
* Price
* Zipcode
* Waterfront
* Grade
* Condition
* bedroomsNumber
* bathroomsNumber
* sqft_livingsquare
* sqft_lotsquare
* yr_built
* floorsTotal

We will investigate how those variables influence in the price of the houses



## METHODS 

We first investigate whether renovating a house signficantly impact the house prices. Running a t-test, we observed that renovating houses have a signifcant effect in price salary (t-test, pvalue: 4.797932412475557e-18). 
The average price for renovated is 759316.8022151899, which represents 1.4-fold increase compared to non-renovated houses (average price = 532194.4358991687)

As such, we decided to select only the houses that were not renovated, as we want to buy the major number of houses with a budget. 

Similarly, we run a t-test to investigate whether water views affected the price of the houses. We observed a statistical signifcance increases between the price of houses with water view (1725217.97752809 average price) compared to houses with no water views (524975.2969812347)

Therefore, we filtered the houses that have no water views for furhter analysis. 

Next step was to investigate which zipcodes have the most expensive house. For this reaso, we perfom a regression model to investigate the effect of zipcodes in price. From this analysis, we discarded the suburs that have a signifncant postive correlation with houses prices, and continue with the analysis of the other suburbs.

One selected the suburbs of interest, we run a linear regression model to investigate the effect of grade and conditions. From this analysis, we descarded the houses whose grade signficnatly and positively increase the salary price. 

Once we have performed the filters to select the houses with lowest price, we run a linear regression model to investigate the effect of the variales:

* bedroomsNumber
* bathroomsNumber
* sqft_livingsquare
* sqft_lotsquare
* yr_built
* floorsTotal



## RESULTS

### Effects of renovation in price
**Analysis**: t-test

**Hypothesis**:
    H0 = there are no differences between renovated and non-renovated houses
    H1 = there are differences between renovated and non-renovated houses

**Results**:
    Average price in renovated houses: 759316
    Average price in non-renovated houses: 532194

**p-value**: 4.797932412475557e-18

**Meaning**: There is a significant difference between the price of renovated vs non-renovated houses

**Action**: Select only the non-renovated houses


### Effects of waterview in price

**Analysis**: t-test

**Hypothesis**:
    H0 = there are no differences between houses with or without waterviews 
    H1 = there are differences between houses with or without waterviews 

**Results**:
    Average price in renovated houses: 1725217 
    Average price in non-renovated houses: 524975

p-value: 5.1010178385823954e-17

**Meaning**: There is a significant difference between the price of houses with vs without waterview

**Action**: Select only the houses without waterview


### Effects of zipcode in price

**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.457, which is a very low value. This means that only 45% of the price variability can be explained by zipcode.

However, in this analysis we want to focus on particular zipcodes. For example, is the zipcode 98002 significantly changing the price of the houses?

For this reason, we created two lists: 
* one with zipcodes that significantly increase the price (i.e. positive coef and p_value < 0.05) --> these zipcodes will be discarded for further analysis.
* one with zipcodes that do not signficantly change the price --> these are the zipcodes of interst

**Action**: Select only the houses that correspond to the zipcodes of interest. 

    
### Effects of condition in price

**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.015, which is a very low value. This means that only 1.5% of the price variability can be explained by condition.

However, we observe that condition 3, 4 and 5 signifncatly and positively contribute to the price of houses

**Action**: As only 25 housess corresspond to condition 1, we can't remove these data


### Effects of grade in price

**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.433, which is a very low value. This means that only 43.3% of the price variability can be explained by grade.

However, we observe that grade 9, 10 and 11 signifncatly and positively contribute to the price of houses

**Action**: Exclude houses correspoding to grade 9, 10 and 11 for further analysis
    

### Effects of number of bedrooms, number of bathrooms, number of floors, years since built, sqft living area and sqft living lot in price

**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.465, which is a very low value. This means that only 46.5% of the price variability can be explained by grade.

We observe that number of bedrooms, number of bathrooms, number of floors, sqft living area and sqft living lot have a significant contribution to house price. The years since the hougses was built do not significantly impact on the price. 

From all these factors, the sqft living area is the variable that affects the most to the price, with a coeficient value of 0..52


## CONCLUSIONS
We provide the following business recomendations:

* **Insights 1** Look for non-renovated houses
* **Insights 2** Look for houses that have no waterview
* **Insights 3** Look for houses in the following zipcodes: 98002, 98003, 98022, 98023, 98030, 98031, 98032, 98055, 98106, 98148, 98168, 98178, 98188, 98198.
* **Insights 4** : look for houses corresponding to condition 2
* **Insights 5** : look for houses below grade 9
* **Insights 6** : focus your search on houses with the lowest sqft living







### Key Points

* **Your deliverables should explicitly address each step of the data science process.** Refer to [the Data Science Process lesson](https://github.com/learn-co-curriculum/dsc-data-science-processes) from Topic 19 for more information about process models you can use.

* **Your Jupyter Notebook should demonstrate an iterative approach to modeling.** This means that you begin with a basic model, evaluate it, and then provide justification for and proceed to a new model. After you finish refining your models, you should provide 1-3 paragraphs discussing your final model - this should include interpreting at least 3 important parameter estimates or statistics.

* **Based on the results of your models, your notebook and presentation should discuss at least two features that have strong relationships with housing prices.**

## Getting Started

Start on this project by forking and cloning [this project repository](https://github.com/learn-co-curriculum/dsc-phase-2-project) to get a local copy of the dataset.

We recommend structuring your project repository similar to the structure in [the Phase 1 Project Template](https://github.com/learn-co-curriculum/dsc-project-template). You can do this either by creating a new fork of that repository to work in or by building a new repository from scratch that mimics that structure.

## Project Submission and Review

Review the "Project Submission & Review" page in the "Milestones Instructions" topic to learn how to submit your project and how it will be reviewed. Your project must pass review for you to progress to the next Phase.

## Summary

This project will give you a valuable opportunity to develop your data science skills using real-world data. The end-of-phase projects are a critical part of the program because they give you a chance to bring together all the skills you've learned, apply them to realistic projects for a business stakeholder, practice communication skills, and get feedback to help you improve. You've got this!
