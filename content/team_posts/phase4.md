---
title: "Project - Phase IV"
date: 2025-06-12
draft: false
description: "Project Description"
slug: "phase4post"
tags: ["project", "Setup"]
authors:
  - "mayaellis"
  - "maxrobinson"
  - "aretimakropoulos"
  - "zoyasiddiqui"
showAuthorsBadges: false
---

# Project: Phase 4 Deliverable

## ML Models

Our **time-series autoregressive** model uses quality of life scores taken from the World Happiness Index for years 2011-2022 with a five-year lag to predict quality of life scores for a specific country five years into the future (or really, five years past the end of our data, so up to 2027) with relative accuracy. The features of this model included 26 dummy columns of country indicators for each EU country, and then our five lag columns for our quality of life data. On the front-end, this model displays as a graph of quality of life scores over time with a line for either one country, or two countries to compare them. There is a line of demarcation between historical and predicted scores.

The weights produced by this model were stored in the database, and these are accessed in the *autoregressor_all* function that produces a list of dicts of historical and predicted scores for a given country up to 2027. This function can be called using the *get_model_scores* route, which is the input for the *plot_qol* function that exists on any page that requires a graph of quality of life over time.

This model was used for all our user personas. 
- The *university student* can see a graph comparing historical and predicted quality of life over time ffor two countries from their saved preferences (created using the cosine similarity model based on their inputted preferences) on the "Past_Prefs" page. 
- The *policymaker* can see a graph comparing historical and predicted quality of life over time time for their inputted country and the country most similar to theirs on the "Similar_Countries" page.
- The *activist* can see a graph comparing historical and predicted quality of life over time for two inputted countries on the "QoL_Change" page. 

### Checking of All Model Assumptions & Predictive Checks
Before performing cross-validation, our **time-series autoregressor** had an R^2 of 0.99 and a mean-squared error of 0.006. After performing cross-validation, these values went to an R^2 of 0.62 and an MSE of 0.12. So, 62% of variance in quality of life scores can be explained by time, and the model comes pretty close to going through all points exactly. Using the residuals and x-values from our cross-validation, we then created *x feature vs. e plots* to assess linearity and homoscedasticity, an *ordered e plot* to assess autocorrelation, and a *histogram of e* to assess normality of residuals.

**X-Features vs. Residual Plots**
There are five of these to assess for each of our five lag columns.
![xve1](/rvx_1.png)
![xve2](/rvx_2.png)
![xve3](/rvx_3.png)
![xve4](/rvx_4.png)
![xve5](/rvx_5.png)
*Discussion*: These plots are supposed to be a random line of points across zero - if there is anything else, either linearity or homoscedasticity is violated. This is relatively true in our above plots, but for all lags, there seems to be outlier residuals that are particularly negative around lower QoL values and particularly positive ones around higher QoL values. This means that the relationship may not be perfectly linear, or the residuals do not have constant variance.

**Ordered Residual Plot**
![orderede](/rvo.png)
*Discussion*: This plot is supposed to have no patterns - if there are, autocorrelation is violated. Once again, this seems to be generally true, but there seem to be outliers at particular points in the indices. There may be some autocorrelation, but as this is an autoregressive model, that is to be expected.

**Historgram of Residuals**
![histogram](/histogram.png)
*Discussion*: The residuals should be generally symmetric about zero. This is not true here. There are more negative residuals, and there is not a normal distribution of residuals. 

Ultimately, it seems that our residual plots are not the best, so some assumptions of linearity may not be met. Heteroscedasticity seems to be an issue, which could be fixed by transforming either the x or y feature. A linear model also may not necessarily be the best option here. We could tackle some of these issues by making more models for quality of life over time and comparing their cross-validated R^2 and MSE.

## Software Architecture


## Database Model

The final database model is best displayed in our updated entity relationship diagram and relational mapping. Here is the global relational mapping.

<div style="width: 640px; height: 480px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://lucid.app/documents/embedded/6399ce45-7fe8-4d5b-b456-1b6e986de67d" id="XoqoXAboBGN4"></iframe></div>

In our database model we have 12 entities which structure and organize our data for our Best Life application. 

**ML_Score_US**, **ML_Score**, and **Predicted_Score** store the data used by our machine learning models. **ML_Score_US** contains the unstandardized scores of each country by year for our factors of health, education, safety, and environment as well as the quality of life score. **ML_Score** stores the standardized version of the same attributes, used for the cosine similary ML model.**Predicted_Score** holds the the weights and lags produced by our times series autoregressive model, allowing for prediction.

**User** and **User_Role** support user login with role based experiences. **User** stores the specific information about the user and **User_Role** allows for each **User** to have a role, ensuring the features and pages accessible to the user. 

**Country** plays a crucial role with many relationships as much of our data being stored is country specific, this table is referenced by many entities. Additionally, **Factor** contains the names of the four key areas which is health, education, safety, or environment, allowing for consistent referencing.

**University** stores information on top universities within each country which assists the prospective university student persona in evaluating academic opportunities. **Preference** stores the user's selections regarding how much they weigh the value of each factor (health, education, safety, environment) enabling personalized country recommendation.

For the policymaker persona, **Similarity** provides data on countries similar to another country derived from cosine similarity calculations which enables them to explore comparative insights. **Policy_News** stores web-scraped recent policy artices for each country allowing policymakers to stay informed and make well informed decisions. 

**Organization** contains information about organizations in specific countries addressing certain factors, so activists can find causes aligned with their interests. 
