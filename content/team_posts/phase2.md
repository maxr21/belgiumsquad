---
title: "Project - Phase II"
date: 2025-05-27
draft: false
description: "Project Description"
slug: "phase2post"
tags: ["project", "Setup"]
authors:
  - "mayaellis"
  - "maxrobinson"
  - "aretimakropoulos"
  - "zoyasiddiqui"
showAuthorsBadges: false
---

# Project - Phase 2 Deliverable

## Updates

While working with Phase 2 deliverables and considering Phase 1 feedback, we decided to update some of our user stories to be more differentiable and created corresponding pages in our wireframes. We also made some changes to our data, as we are no longer considering culture as a factor in quality of life because of the insufficient number of years included in the dataset. For our regression, we are now utilizing 11 years of data in order to predict farther into the future. We have switched our quality of life dataset from a Eurostat API to a CSV of scores from the World Happiness Index. We made this decision because the Eurostat API for quality of life only had data for four non-concurrent years, and the World Happiness Index CSV had much more extensive data.

## Data Visualizations

For our data visualization, we generated five scatter plots using Plotly. These scatter plots illustrate the relationship between quality of life and each of our factors, displaying graphs for quality of life versus healthcare, quality of life versus education, quality of life versus safety, quality of life versus environment, and quality of life versus transportation.

These visualizations help illustrate any immediately obvious relationships between our chosen factors and quality of life, which will prove integral to our regression model that will use these factors to predict future quality of life. Using these graphs, we can see weak, positive relationships between quality of life and all of our factors, though safety and transit are not as clear in their relationships with quality of life. After seeing these relationships visually, we will be able to better predict how our quality of life regressor model will be impacted by each of these factors.

### Visualizations

![healthcare](/health_qol.jpg)
![education](/edu_qol.jpg)
![safety](/safety_qol.jpg)
![environment](/env_qol.jpg)
![transportation](/inf_qol.jpg)

## Model explanations and plans

We are planning on making two models, a supervised autoregression model with a lag of 1 year (AR1) and a cosine similarity score model. Our AR1 model will be used to predict future values of the happiness index. The current difficulties with this model are that it is very easy to have more features than data points, forcing us to use a gradient descent model instead. We would prefer to avoid this and keep our time lag low so that we can perform linear regression. We have 10 years of data, meaning 10 data points, and 5 features. We are considering adding a sixth feature representing pre, post and during covid. However, this may be collinear with other features because I expect many of the metrics used to vary with covid.

The cosine similarity score model is already implemented and will be used to compare what the student wants (they will input this using sliders) and a country that best matches their input. We have used an inverse-sigmoid function to translate the bounded data from the sliders to the unbounded but standardised data from the APIs. After test running this model it looks like it works pretty well.

This model can be found at https://github.com/mke27/life/blob/main/ml-src/cos_similarity.py

## Wireframes

![wireframe1_img](er_diagrams-06.jpg)
Title page.
![wireframe2_img](er_diagrams-07.jpg)
Welcome/Home page for Persona 2, Grace.
![wireframe3_img](er_diagrams-08.jpg)
This page shows a gradient map for which Grace can change her priorities. It will display the countries that are most appealing to her and will allow her to navigate to a universities page, a QoL trends page, and a history page.
![wireframe4_img](er_diagrams-09.jpg)
This page allows Grace to select which prior priority sets she wants to compare in the form of the top recommended country.
![wireframe5_img](er_diagrams-10.jpg)
The priority sets that she chooses will show up side by side with each country's past QoL score and predicted scores.
![wireframe6_img](er_diagrams-11.jpg)
This page will display the top 3 universities in Grace's top recommended country. She will be able to click on each one and contact an admissions officer.
![wireframe7_img](er_diagrams-12.jpg)
This page hows the QoL overtime and predicted for one country that Grace clicks on the map.
![wireframe8_img](er_diagrams-13.jpg)
This is Persona 2's (James) landing page.
![wireframe9_img](er_diagrams-14.jpg)
James can view his country's most similar country and also his country's lowest scoring factor. By selecting a factor, he can view recent news from the EU Commission and click links to the articles.
![wireframe10_img](er_diagrams-15.jpg)
James can click on his most similar country in order to view a chart showing that country's similarity score compared to other countries.
![wireframe11_img](er_diagrams-16.jpg)
Landing page for Persona 3, Faye.
![wireframe12_img](er_diagrams-17.jpg)
Faye can select her organization's area of interest and will view a map showing each country's rate of change in that factor. She can click on each country to learn more on the next page.
![wireframe13_img](er_diagrams-18.jpg)
This chart shows the country's factor score over time and the predicted score. The scores of each factor in thi country will also be displayed.
![wireframe14_img](er_diagrams-19.jpg)
This is an opportunity for Faye to post on an external social media site. She can upload a photo and text.
![wireframe15_img](er_diagrams-20.jpg)
Faye can view her recent posts here.

## ER Diagrams

![erd1_img](er_diagrams-01.jpg)
This is our global ERD, which encompasses all of the entities and relationships that makeup our database.
![erd2_img](er_diagrams-02.jpg)
This is our ERD for persona 1, the student.
![erd3_img](er_diagrams-03.jpg)
This is our ERD for persona 2, the policymaker.
![erd4_img](er_diagrams-04.jpg)
This is our ERD for persona 3, the activist.

## Relational Mapping

<div style="width: 640px; height: 480px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://lucid.app/documents/embedded/6399ce45-7fe8-4d5b-b456-1b6e986de67d" id="jSzj-C2TrnaZ"></iframe></div>

## SQL DDL for Global Data Model

[SQL File](https://raw.githubusercontent.com/mke27/life/refs/heads/main/database-files/global_db.sql)
