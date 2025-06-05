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

For our data visualization, we generated nine plots using Plotly. The first four are scatter plots illustrate the relationship between quality of life and each of our factors, displaying graphs for quality of life versus healthcare, quality of life versus education, quality of life versus safety, and quality of life versus environment. The last five are line plots that visualize health, education, environment, safety, and quality of life over time.

These visualizations help illustrate any immediately obvious relationships between our chosen factors and quality of life, which will prove integral to our regression model that will use these factors to predict future quality of life. Using these graphs, we can see weak, positive relationships between quality of life and all of our factors, though safety is not as clear in their relationships with quality of life. After seeing these relationships visually, we will be able to better predict how our quality of life regressor model will be impacted by each of these factors, as these visuals can help guide the development of our regressor. 

### Visualizations
Factors vs. Quality of Life
{{< iframe src="health_qol.html" width="100%" height="600" >}}
{{< iframe src="edu_qol.html" width="100%" height="600" >}}
{{< iframe src="env_qol.html" width="100%" height="600" >}}
{{< iframe src="safety_qol.html" width="100%" height="600" >}}

Factors over Time
{{< iframe src="health_time.html" width="100%" height="600" >}}
{{< iframe src="edu_time.html" width="100%" height="600" >}}
{{< iframe src="env_time.html" width="100%" height="600" >}}
{{< iframe src="safety_time.html" width="100%" height="600" >}}
{{< iframe src="qol_time.html" width="100%" height="600" >}}

## Model explanations and plans

We are planning on making two models, a supervised autoregression model with a lag of 1 year (AR1) and a cosine similarity score model. Our AR1 model will be used to predict future values of the happiness index. The current difficulties with this model are that it is very easy to have more features than data points, forcing us to use a gradient descent model instead. We would prefer to avoid this and keep our time lag low so that we can perform linear regression. We have 10 years of data, meaning 10 data points, and 5 features. We are considering adding a sixth feature representing pre, post and during covid. However, this may be collinear with other features because I expect many of the metrics used to vary with covid.

The cosine similarity score model is already implemented and will be used to compare what the student wants (they will input this using sliders) and a country that best matches their input. We have used an inverse-sigmoid function to translate the bounded data from the sliders to the unbounded but standardised data from the APIs. After test running this model it looks like it works pretty well.

This model can be found at https://github.com/mke27/life/blob/main/ml-src/cos_similarity.py

## Wireframes

![wireframe1_img](er_diagrams-06.jpg)
Title page.
![wireframe2_img](er_diagrams-07.jpg)
Welcome/Home page for Persona 1, Grace.
![wireframe3_img](er_diagrams-08.jpg)
This page shows a gradient map for which Grace can change her priorities. It will display the countries that are most appealing to her.
![wireframe4_img](er_diagrams-09.jpg)
This page allows Grace to select which prior priority sets she wants to compare in the form of the top recommended country.
![wireframe5_img](er_diagrams-10.jpg)
This page will display the top 3 universities in Grace's top recommended country. She will be able to click on each one and contact an admissions officer.
![wireframe6_img](er_diagrams-11.jpg)
This is Persona 2's (James) landing page.
![wireframe7_img](er_diagrams-12.jpg)
By selecting a factor, he can view recent news from the EU Commission and click links to the articles.
![wireframe8_img](er_diagrams-13.jpg)
James can view his country's most similar country and also the country score stats. 
![wireframe9_img](er_diagrams-14.jpg)
Landing page for Persona 3, Faye.
![wireframe10_img](er_diagrams-15.jpg)
This is a map of the EU which will show which country has the lowest score in the chosen factor.
![wireframe11_img](er_diagrams-16.jpg)
TBD chart
![wireframe12_img](er_diagrams-17.jpg)
Faye can view existing organizations given the country and factor she chooses.

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
