# Phase 3 Diabetes Screening

Welcome scientists, politians, conservationists, concerned citizens, and beyond! For my fourthl phase project in the Flatiron Data Science program, I have made a model that can help screen patients for diabetes. 

In this project description, we will cover:

* [***Project Overview:***](#project-overview) The project goal, audience, and dataset
* [***Basic Walkthrough:***](#Walkthrough) The basics of what I did during the project
* [***Final Model***](#final_model) Final model chosen based on RSME and AIC
* [***Findings:***](#findings) Projected findings using said models
* [***Business Recommendations:***](#busrec) Recommendations based on model findings
* [***What's Next:***](#next) What I'd like to do to improve further


## Project Overview<a id='project-overview'></a>

For this project, I used exploratory data analysis, data preparation, and modeling to generate insights for a business stakeholder.

### Business Problem

#### Stake Holders:
* Medical facilities such as primary care physician offices, or even other medical care facilities such as convenient care facilities, urgent care facilities, and hospitals. While these are my primary stake holders, it would be within the rhealm of possibility that this model could be used by insurance companies.

#### Busniess Problem/Solution:
* Declining bee populations have been a problem worldwide, but especially in Ireland, where about 1/3 of the bee species face threat of extinction. Declining populations have a real impact on local ecosystems, as well as local and national economies, so monitoring and implementation of bee-friendly practices are needed.

* We want to take older data to get an idea of what we can expect to find for the current population of various species of bees, and make a plan based on those findings to increase bee populations.

### The Dataset

The [data]("https://www.gbif.org/dataset/6eed5110-c7b8-11de-b279-d063ea754e15") we are using today is the dataset on the distribution of bees in Ireland from both published and unpublished sources spanning from 1884 to 2022, initially compiled as part of a Trinity College Dublin/Queen's University Belfast HEA funded research project on the conservation of Irish bees (2003-2006; Úna Fitzpatrick & Tomás Murray). It was used for conservation purposes, including the development of a Red List, which evaluates species on their extinction risk. It is now deposited with the National Biodiversity Data Centre and is managed by Úna Fitzpatrick.

#### Features Used:
* **eventDate:** Object, date of sighting
* **genus:** Object, genus of bee spotted
* **species:** Object, species of bee spotted

## Basic Walkthrough<a id='Walkthrough'></a>

* **Exploring the data**: Sizing up the data, planning what needs to be done
* **Cleaning/Preprocesing the data**: No cleaning needed, so we made a subset of all entries between 2013-2015, 
* **Data Prep/Feature Engineering**: I checked for normality and homoscedasticity, implementing various ways to ready the data for time series modeling.
* **Models**: I tried out a couple different models (ARIMA*, SARIMAX*, and Phrophet) after establishing a baseline naive model, adding in analysis for each one and trying out different ways to improve their results.
* **Final Model Selection**: Review the model I selected and explain why I chose it. 
* **Business Recommendations** - Implimentation and greater uses. 
* **Beyond**: Relfections on how I would improve my process or do something differently in the future. 

Note:

 "*"= Model was optimized with GridSearchCV after baseline established
 
## Final Model<a id='final_model'></a>

After running a few models mentioned above, I chose XGBoost after I enhanced it via GridSearchCV. 

<img src="images/Final_model_results.png" alt="XGBoost Model Results" />

For this project I actually made three models, one for each bee species I decided to follow. 

For Bombus Moscurom, I chose a SARIMAX model with orders as follows:______________. 

## Findings <a id='findings'></a>

The top factors that correlated with having diabetes were (poor) general health, high blood pressure, BMI, high cholestoral, Age, difficulty walking. I also found the correlation between mental health and diabetes to be compelling. 

### Age vs. Diabetes Status
Here we can plainly see a gradual incline of the prevelence of diabetes as patients get older. There ia slight decline at the end, which might be explained by the lower life expectancy of those with diabetes (77 for men, 81 for women).

<img src="images/Age_Diabetes.png" alt="Age versus Diabetes" />


## Business Recommendations <a id='busrec'></a>

**Basic Use Function**
When receiving a new patient or even reviewing updated information for a current patient, doctors and nurses would be able to input the basic data points needed for the model to see if a patient might have diabetes (diagnosed or not). This can be implimented into their workflow via an add-on to software they currently use, or as a standalone application.

**Recommendation**

You will want to keep an eye out for **high blood pressure, high cholesterol, poor general health, elevated BMI, and difficulty walking, especially in older and female patients.**

While this model can be useful for inputting data on new and existing patients, it shows that the most influental parameters could be examined to utilize in an action plan to improve the patients health.

For example, while someone cannot make themselves younger or erase a stroke from their medical history, they could work to:
* lower their blood pressure
* lower their cholesterol
* get their BMI to a healthy level
* take steps to improve their general physical health
* refer to mental health services such as counseling, therapy, etc. as needed

## What's Next<a id='next'></a>
I would like to explore the original data from the original dataset (rather than this subset) and do a bit more exploratory analysis on that. This dataset explored pretty broad topics, but I'd like to see if going into more detail in each topic made more of a difference rather than the broad topic on it's own.

In addition, I would like to explore more data derived not from the patients opinion, but from a measurable quantity outside of that to see if we can get away from possible personal bias.

On a more data-centric note, I think next time I will change the column titles after OHE-ing, as continually refering back to my legend got pretty old, pretty fast. 

Thank you for taking the time to read through this, and I hope it helped inform and awaken your curiosity!

