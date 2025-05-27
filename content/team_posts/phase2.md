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

## Wireframes

![wireframe1_img](er_diagrams-06.jpg)
![wireframe2_img](er_diagrams-07.jpg)
![wireframe3_img](er_diagrams-08.jpg)
![wireframe4_img](er_diagrams-09.jpg)
![wireframe5_img](er_diagrams-10.jpg)
![wireframe6_img](er_diagrams-11.jpg)
![wireframe7_img](er_diagrams-12.jpg)
![wireframe8_img](er_diagrams-13.jpg)
![wireframe9_img](er_diagrams-14.jpg)
![wireframe10_img](er_diagrams-15.jpg)
![wireframe11_img](er_diagrams-16.jpg)
![wireframe12_img](er_diagrams-17.jpg)
![wireframe13_img](er_diagrams-18.jpg)
![wireframe14_img](er_diagrams-19.jpg)
![wireframe15_img](er_diagrams-20.jpg)

## ER Diagrams

![erd1_img](er_diagrams-01.jpg)
This is our global ERD, which encompasses all of the entities and relationships that makeup our database.
![erd2_img](er_diagrams-02.jpg)
This is our ERD for persona 1, the student.
![erd3_img](er_diagrams-03.jpg)
This is our ERD for persona 2, the policymaker.
![erd4_img](er_diagrams-04.jpg)
This is our ERD for persona 3, the activist.
