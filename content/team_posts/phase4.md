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

Create new team and individual blog posts which

- demonstrate fundamental understanding of ML models and their
  implementation in the software architecture
- Incl. verifying checking of all model assumptions and predictive
  checks (things not included in the web app)
- describe software architecture and final version of database model

# Project: Phase 4 Deliverable

## ML Models

Our **time-series autoregressive** model uses quality of life scores taken from the World Happiness Index for years 2011-2022 with a five-year lag to predict quality of life scores for a specific country five years into the future (or really, five years past the end of our data, so up to 2027) with relative accuracy. The features of this model included 26 dummy columns of country indicators for each EU country, and then our five lag columns for our quality of life data. On the front-end, this model displays as a graph of quality of life scores over time with a line for either one country, or two countries to compare them. There is a line of demarcation between historical and predicted scores.

The weights produced by this model were stored in the database, and these are accessed in the _autoregressor_all_ function that produces a list of dicts of historical and predicted scores for a given country up to 2027. This function can be called using the _get_model_scores_ route, which is the input for the _plot_qol_ function that exists on any page that requires a graph of quality of life over time.

This model was used for all our user personas.

- The _university student_ can see a graph comparing historical and predicted quality of life over time ffor two countries from their saved preferences (created using the cosine similarity model based on their inputted preferences) on the "Past_Prefs" page.
- The _policymaker_ can see a graph comparing historical and predicted quality of life over time time for their inputted country and the country most similar to theirs on the "Similar_Countries" page.
- The _activist_ can see a graph comparing historical and predicted quality of life over time for two inputted countries on the "QoL_Change" page.

The cosine similarities score model uses the health, education, environment and safety scores taken from Eurostat for a given year. We gather this data for each EU member state so that our model can compare the input scores to the standardised scores of each country. The output of this model is a dataframe containing the name of each EU member state and a value between -1 and 1 called the similarity score. This score represents the cosine of the angle between the input vector and the EU member state vector. A value of 1 means an angle of 0, therefore very similar vectors. A value of -1 means opposite direction vectors meaning completely different.

This model is used by the prospective university student user and the policymaker user.

- The prospective university student can input her priorities using four sliders. The page then translates these scores from 0-100 into an unbounded inverse sigmoided score that stays generally between -3 and 3 (this stretches across most of our standardised values). The result is a chloropleth map showing the most similar countries to her input
- The policymaker can directly compare countries to eachother. He can select his country and look at another chloropleth map of Europe with similar EU member states shaded darker.

### Checking of All Model Assumptions & Predictive Checks

Before performing cross-validation, our **time-series autoregressor** had an R^2 of 0.99 and a mean-squared error of 0.006. After performing cross-validation, these values went to an R^2 of 0.62 and an MSE of 0.12. So, 62% of variance in quality of life scores can be explained by time, and the model comes pretty close to going through all points exactly. Using the residuals and x-values from our cross-validation, we then created _x feature vs. e plots_ to assess linearity and homoscedasticity, an _ordered e plot_ to assess autocorrelation, and a _histogram of e_ to assess normality of residuals.

**X-Features vs. Residual Plots**
There are five of these to assess for each of our five lag columns.
![xve1](/rvx_1.png)
![xve2](/rvx_2.png)
![xve3](/rvx_3.png)
![xve4](/rvx_4.png)
![xve5](/rvx_5.png)
_Discussion_: These plots are supposed to be a random line of points across zero - if there is anything else, either linearity or homoscedasticity is violated. This is relatively true in our above plots, but for all lags, there seems to be outlier residuals that are particularly negative around lower QoL values and particularly positive ones around higher QoL values. This means that the relationship may not be perfectly linear, or the residuals do not have constant variance.

**Ordered Residual Plot**
![orderede](/rvo.png)
_Discussion_: This plot is supposed to have no patterns - if there are, autocorrelation is violated. Once again, this seems to be generally true, but there seem to be outliers at particular points in the indices. There may be some autocorrelation, but as this is an autoregressive model, that is to be expected.

**Historgram of Residuals**
![histogram](/histogram.png)
_Discussion_: The residuals should be generally symmetric about zero. This is not true here. There are more negative residuals, and there is not a normal distribution of residuals.

Ultimately, it seems that our residual plots are not the best, so some assumptions of linearity may not be met. Heteroscedasticity seems to be an issue, which could be fixed by transforming either the x or y feature. A linear model also may not necessarily be the best option here. We could tackle some of these issues by making more models for quality of life over time and comparing their cross-validated R^2 and MSE.

## Software Architecture

## Database Model
