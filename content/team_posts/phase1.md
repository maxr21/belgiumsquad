---
title: "Project - Phase I"
date: 2025-05-20
draft: false
description: "Project Description"
slug: "phase1post"
tags: ["project", "Setup"]
authors:
  - "mayaellis"
  - "maxrobinson"
  - "aretimakropoulos"
  - "zoyasiddiqui"
showAuthorsBadges: false
---

# Project - Phase 1 Deliverable

## Project Description

A country’s quality of life provides important insight into the well-being of citizens and their satisfaction with the standards of living. Rather than simply relying on a single statistic to determine a country’s success, quality of life encapsulates a broader sense of how people feel about their experiences. This is typically based on several factors, and for our project we will be focusing on the following: Healthcare, Education, Safety, Environment, and Transportation.

Our application aims to provide information and insights about and related to the quality of life in EU countries over the past 5 years. It will assist with decision making on a personal, commercial, and governmental level. A student can use this application to assess which country to attend university in by ranking their priorities, while a government official can input their country in order to identify their most lacking factor, discover the country most similar to theirs, and gain insight from recent policy implementations. Additionally, a social organization can determine the best opportunities for expansion by identifying the countries underperforming in their target focus.

The application will utilize a combination of regression and similarity scoring in order to provide valuable insights to its users. The ultimate goal is to help users understand the factors that determine their quality of life and subsequently make informed decisions through moving, policy implementation, or providing aid.

## Persona 1

Grace Monova is an 18 year old woman who wants to move to a new country for university. Grace is outgoing, loves traveling and is dedicated to her studies. She is excited to start a life in a brand new country and wants to ensure a good fit given her priorities and concerns. She is very intelligent and values receiving a high quality education. Also, being a young woman living in a new place, she wants to find a country that is generally safe and has low crime rates. She cares about meeting people from different backgrounds and appreciates opportunities for integration in the country’s culture. The process of researching which EU country is best suited for her is grueling and time consuming, so she wishes for an easier way.

### User Stories

- As a student who values the quality of my education, I want an application to recommend a country to me based on my prioritization of education.
- As a young individual, I would like to know how each country’s quality of life scores are predicted to change over the next few years so I can make the best decision in the long run.
- As a user, I want to be able to change my priorities so that I can view different recommendations.
- As a student, I want to set my own priorities when conducting my search so that I can find the countries most tailored to me.

## Persona 2

James Gardinier is a 56 year old member of the French parliament. He recently had a discussion about the World Happiness Index with a Danish friend, and found out that France ranked 30th in 2023 while Denmark ranked 3rd globally. This made him wonder about the ways in which France could increase their ranking in the index, which requires an increase in quality of life. He is unsure about what factors are dragging France down compared to Denmark, and wants to see how other countries are working to raise their ranking. This would allow him to act appropriately as a policymaker.

### User Stories

- As a French policymaker comparing my country to those that rank higher, I want to see which factors are pulling down France’s score so that I know where to focus my attention.

- As a government worker, I want to visualize France’s ranking in QoL scores so that I know which countries are outperforming mine.
- As a member of parliament, I want to view countries that perform similarly to France so that I can gain new perspectives from outside of French culture.
- As a policymaker, I want to receive information about recent EU policy implementations that pertain to my country’s area of concern.

## Persona 3

Faye Mulligan is a 26 year old Swiss activist. She works at an organization that aims to raise awareness about environmental issues such as air pollution and reducing carbon emissions. The organization was founded several years ago in Switzerland and has had great success in increasing environmental consciousness, so it is now looking to expand into the EU. Faye has been tasked with finding three EU countries in which the organization would be most needed and would be likely to make a strong impact.

### User Stories

- As an activist focused on environmental impact, I want to identify countries where air quality and pollution is the worst so that I know where our organization is most needed.
- As an activist, I want to view trends in environmental scores over the past few years and visualize predicted scores so that I can understand and prepare for a new market.
- As a user, I want the countries that have high environmental scores to be removed from my recommendations so that I can focus my efforts.
- As an environmentalist, I want to compare potential countries on a smaller scale so that I can narrow my search.

## Datasets

For our project, we will be using datasets acquired from Eurostat. We will be using 5 datasets for Health, Education, Transport, Environment, and Safety. These datasets will be the factors that are utilized to compare countries and determine the best country for a student based on their priorities. Thee scores will also be relevant to the policymaker, as he will receive information about his country's lowest scoring factor as well as a similarity score to other EU countries based on their factor scores. The activist will also be matched to countries depending on which factor of interest they select, and they will get to view the rates of change in that factor score for each country on a gradient map.

For quality of life scores, we will be using data from World Happiness Index, which will provide the basis for the predictions in our regression. This will be used in the student persona in order to provide information about previous and future quality of life scores in the countries they are considering.

We will also be scraping data from EU Commission sites pertaining to Health, Education, Transport, Environment, and Safety. These sites will provide the most recent news articles about EU legislation in each of these factors, which will be available for the policymaker to view.

## Data collection and cleaning vision

Candidate Data Sources:

- Demonstrate you are able to successfully scrape the
  website(s)/access the API (i.e. the API is not paywalled, or an initial
  scrape attempt of the website worked)

evidence of successful scraping and api access can be found at https://github.com/mke27/life/blob/main/datasets/raw-datasets/accessingAPI.ipynb for API access

and https://github.com/mke27/life/blob/main/datasets/raw-datasets/dataAccessTest/webScraper.ipynb for successful webscraping

- Establish contents of data as appropriate for ML (# of observations,
  and types of features)

For our two models, we will need the data for our six chosen metrics (education, environment, health, infrastructure, culture and safety) over a period of at least 8 years. This is so that we can build an AR1 (autoregression model with a lag of 1 year). This model will be capable of predicting the next year's happiness index using the previous year's happiness index and our six chosen metrics.

Upon further exploration, it seems as though our autoregression model may need to be adapted into a gradient descent model. This is because we do not have enough data to make meaningful predictions for James Gardinier. We will only be capable of predicting data for the past.

- Establish utility of data in addressing personas’ use of application

This data is essential for our Student to decide which European country best fits her needs. We need these features to be available for our similarity scores so that we can compare countries. This same model will be very useful for Faye Mulligan to identify nations that require what her organization provides the most. She will be able to see which countries fit the profile of being 'in need' the most.

We also need the previous years of this data so that we may build our autoregression model and so that it may predict as much into the future as possible. This will be helpful for our French politician, James Gardinier, to evaluate the performance of his nation and policy with happiness index. Furhtermore, we are providing Gardiner a way of quickly determining the latest in EU policy combatting the 6 chosen metrics by webscraping many different news sites. We will use this data to provide Gardinier a view of the three most recent headlines concerning any one or two metrics.
