# EFFECTS OF METAL OXIDES IN POSITANO'S TEMPERATURE 

***Author:*** Ariadna Recasens


## 1. OVERVIEW
This project explores the effect of metal oxides on the temperature of Positano to help the new mayor implement novel regulations. 


## 2. BUSINESS PROBLEM
The new mayor of Positano, a small Italian city, is worried about climate change and wants to understand whether metal oxides that are released from the city's industries impact the city's warming climate to introduce new regulations.

In this project, we will create a linear regression model to understand the effect of ten metal oxides on Positano's temperature to help the new mayor introduce new regulations to reduce climate change. 


## 3. DATA UNDERSTANDING
This project explores an [Air Quality Data Set](https://archive.ics.uci.edu/ml/datasets/Air+Quality) containing 9358 instances of hourly averaged responses from an array of 5 metal oxide chemical sensors embedded in an Air Quality Chemical Multisensor Device. 

The device was located on the field in a significantly polluted area, at road level, within an Italian city. 

Data were recorded from March 2004 to February 2005 (one year), representing the longest freely available recordings of on field-deployed air quality chemical sensor device responses. 

Missing values are tagged with -200 value.
**Attribute Information**:
1. Date (DD/MM/YYYY)
1. Time (HH.MM.SS)
1. True hourly averaged concentration CO in mg/m^3 (reference analyzer)
1. PT08.S1 (tin oxide) hourly averaged sensor response (nominally CO targeted)
1. True hourly averaged overall Non Metanic HydroCarbons concentration in microg/m^3 (reference analyzer)
1. True hourly averaged Benzene concentration in microg/m^3 (reference analyzer)
1. PT08.S2 (titania) hourly averaged sensor response (nominally NMHC targeted)
1. True hourly averaged NOx concentration in ppb (reference analyzer)
1. PT08.S3 (tungsten oxide) hourly averaged sensor response (nominally NOx targeted)
1. True hourly averaged NO2 concentration in microg/m^3 (reference analyzer)
1. PT08.S4 (tungsten oxide) hourly averaged sensor response (nominally NO2 targeted)
1. PT08.S5 (indium oxide) hourly averaged sensor response (nominally O3 targeted)
1. Temperature in Â°C
1. Relative Humidity (%)
1. AH Absolute Humidity

## 4. METHODS 
1. Data exploration: How do variables change over time?
1. Data exploration: how did the average of each variables change between 2014 and 2015?
1. Linear regression model: Iteration process to imporve the model by studying multicolinearity and interactions. The model has been validate using train and testing subset. 


## 5. RESULTS

### Change of variables over time:

![Changes of CO (mg/m^3) over time](./images/COGT.png)
![Changes of tin oxide (nominally CO targeted) over time](./images/PT08S1CO.png)
![Changes of Non Metanic HydroCarbons(mg/m^3) over time](./images/NMHCGT.png)
![Changes of Benzene (mg/m^3) over time](./images/C6H6GT.png)
![Changes of titania (nominally NMHC targeted) over time](./images/PT08S2NMHC.png)
![Changes of NOx (ppb) over time](./images/NOxGT.png)
![Changes of tungsten oxide (nominally NOx targeted) over time](./images/PT08S3NOx.png)
![Changes of NO2 (microg/m^3) over time](./images/NO2GT.png)
![Changes of tungsten oxide (nominally NO2 targeted) over time](./images/PT08S4NO2.png)
![Changes of indium oxide (nominally O3 targeted) over time](./images/PT08S5O3.png)
![Changes of Temperature (C) over time](./images/T.png)
![Changes of relative humidty (%) over time](./images/RH.png)
![Changes of absolute humidity over time](./images/AH.png)

### Comparision of averages between 2014 and 2015 
| Variable | Average 2014 | Average 2015 |
| --- | --- | --- |
| CO(GT) | 2.036723 | 2.030975 |
| Tin oxide - PT08.S1(CO) | 1061.597046 | 1041.919893 |
| Non Metanic HydroCarbons - NMHC(GT) | 29.435724 |1.500000 |
| Benzene - C6H6(GT) | 10.338383 | 7.877303 |
| Titania - PT08.S2(NMHC) | 930.068214 | 815.172230 |
| NOx - NOx(GT) | 170.898312 | 308.375834 |
| tungsten oxide - PT08.S3(NOx)| 828.916174 | 720.461949 |
| NO2 - NO2(GT) | 79.611744 | 137.482198 |
| Tungsten oxide -  PT08.S4(NO2)| 1502.120956 | 1074.207388 |
| indium oxide - PT08.S5(O3) | 980.447117 | 990.885180 |
| Temperature - (T) | 20.240605 | 9.494393 |
| Relative humidty (RH)  - PT08S5O3 | 46.753657 | 49.308055 |
| Absolute humidty (AH) | 1.151260 | 0.704977 |


### Linear regression model
R-squared = 0.951

**Variables that significantly and positively correlate with Temperature** 
| Variable | Coefficient |
| --- | --- | 
| C6H6(GT) | 11.09684 |
| NO2(GT) | 1.925704 |
| PT08.S4(NO2) | 6.673217 |


**Variables that significantly and negatively correlate with Temperature** 

| Variable | Coefficient |
| --- | --- |
| CO(GT) | -0.561600 |
| PT08.S1(CO) | -4.501010 |
| PT08.S2(NMHC)) | -5.678621 |
| NOx(GT) | -2.7477100 |
| PT08.S3(NOx) | -3.156382 |
| PT08.S5(O3) | -5.449668 |


## 6. CONCLUSIONS
* All the metal oxides studied in this model significantly affect T in Positano.
* Benzene,  NO2 and tungsten oxide (nominally NO2 targeted) positively contribute to T raise (the more concentration of these oxides, the more Temperature), being Benzene the one with the highest negative impact. 
* CO, tin oxide, Titania (PT08.S2), NOx(GT), indium oxide, and tungsten oxide (nominally 03 targeted) negatively contribute to T (the more concentration of these oxides, the less T), being Titania the one with the highest positive impact. 


## 7. BUSINESS RECOMMENDATIONS
We observe a big drop in Temperature between 2014 and 2015, with the T average in 2014 of 20.2 C vs 9.4 C in 2015. This 10C difference could be an indicator that the T sensor was damaged. We recommend checking the Tempearture Sensor and repeating the study with new collected data.

In terms of regulation, since Benzene is the one that contributes the most to Temperature increase, we recommend that the new regulations aim to reduce the emissions of Benzene. 


