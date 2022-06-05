# HOUSE PRICE ANALYSIS FOR WASHINGTON HELP PEOPLE ORGANIZATION

***Author:*** Ariadna Recasens


## Project Overview

In this project, we help the non-for-profit Washington Help People organization to find the most affordable houses. 

### Business problem
The non-for-profit Washington Help People Organization (WHPO) has recently received an anonymous donation to build the maximum number of houses for homeless people. As such, WHPO wants to get some insights to find the cheapest houses so they can buy more units to help more homeless people. In this project, we will use regression models to identify the factors that have a significant impact on house price. 

Some of the questions that we will consider are:

What are the zipcodes wehre the houses are most expensive?
What factors influecce houses price?

### The Data
This project uses the King County House Sales dataset. This dataset contains house sale prices for King County, which includes Seattle. It includes homes sold between May 2014 and May 2015.

The dataset contains 21597 entries and 21 columns. This project will focus on the following variables:
* Price
* Zipcode
* Waterfront
* Grade
* Condition
* bedroomsNumber
* sqft_livingsquare
* sqft_lotsquare
* yr_built

We will investigate how those variables influence on the price of the houses.


## METHODS 

At the core of this project, there is a filtering process that allows us to create a subset of affordable houses on which we will study the effect of several continuous variables.

First, we perform a couple of t-test analyses to study the effect of renovation and water views on house prices. This will help us select the cheapest houses (our subset of interest) to perform further studies. 

Secondly, we perform linear regression models to study the individual effect of zipcodes, grades and conditions on houses price to further narrow our subset of cheaper houses. 

Finally, we perform a linear regression model in our subset of cheap houses to understand the effect of the following continuous variables on price: 

* sqft_livingsquare
* sqft_lotsquare
* yr_built


## RESULTS

### Effects of renovation on price
**Analysis**: t-test

**Hypothesis**:
    H0 = there are no differences between renovated and non-renovated houses
    Ha = there are differences between renovated and non-renovated houses

**Results**:
    Average price in renovated houses: 759316
    Average price in non-renovated houses: 532194

**p-value**: 4.797932412475557e-18

**Meaning**: There is a significant difference between the price of renovated vs non-renovated houses

**Action**: Select only the non-renovated houses


### Effects of waterview on price
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


### Effects of zipcode on price
**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.457, which is a very low value. This means that only 45% of the price variability can be explained by zipcode.

However, in this analysis we want to focus on particular zipcodes. For example, is the zipcode 98002 significantly changing the price of the houses?

For this reason, we created two lists: 
* one with zipcodes that significantly increase the price (i.e. positive coef and p_value < 0.05) --> these zipcodes will be discarded for further analysis.
* one with zipcodes that do not signficantly change the price --> these are the zipcodes of interst

**Action**: Select only the houses that correspond to the zipcodes of interest. 

    
### Effects of condition on price
**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole model is 0.015, which is a very low value. This means that only 1.5% of the price variability can be explained by condition.

However, we observe that condition 3, 4 and 5 signifncatly and positively contribute to the price of houses

**Action**: As only 27 housess corresspond to condition below 3, we can't remove these data


### Effects of grade on price
**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole model is 0.433, which is a low value. This means that only 43.3% of the price variability can be explained by grade.

However, we observe that grade 9, 10 and 11 significantly and positively contribute to the price of houses

**Action**: Exclude houses correspoding to grade 9, 10 and 11 for further analysis

### Effects of number of bedrooms on price
**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole model is 0.132, which is a very low value. This means that only 13.2% of the price variability can be explained by the number of bedrooms.

However, we we can see that each number of bedrooms signfincantly and positively contribute to the house price and that there is an increase in the coefficient as the number of bedrooms increase. 

**Meaning**: The more number of bedrooms, the more expensive the house.

**Action**: No further action. It is up to WHPO to decide how many bedrooms they want to buy, based on homeless population. 
    

### Effects of years since built, sqft living area and sqft living lot on price
**Analysis**: regression model using OLS

**Results**:

The adjusted R-squared value for the whole mode is 0.465, which is a  low value. This means that only 46.5% of the price variability can be explained by grade.

We observe that number of bedrooms, number of bathrooms, sqft living area and sqft living lot have a significant contribution to house price. The years since the house was built does not significantly impact on the price. 

From this regression analysis, we can determine that the sqft living area is the variable that affects the most to the price, as it has the highes coeficient value (coef = 0.52) and a p_value < 0.05.


## CONCLUSIONS
We provide the following business recomendations:

* **Recomendations 1**: Look for non-renovated houses.
* **Recomendations 2**: Look for houses that have no waterview.
* **Recomendations 3**: Look for houses in the following zipcodes: 98002, 98003, 98022, 98023, 98030, 98031, 98032, 98055, 98106, 98148, 98168, 98178, 98188, 98198.
* **Recomendations 4**: Look for houses below condition 3.
* **Recomendations 5**: Look for houses below grade 9.
* **Recomendations 6**: center your search on houses with the lowest sqft living.







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
