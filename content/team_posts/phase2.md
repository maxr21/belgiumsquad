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
![healthcare](/healthcare_qol.html)
![education](/edu_qol.html)
![safety](/safety_qol.html)
![environment](/env_qol.html)
![transportation](/inf_qol.html)

## Wireframes

![wireframe1_img](er diagrams-06.jpg "Wireframe1")
![wireframe2_img](er diagrams-07.jpg "Wireframe2")
![wireframe3_img](er diagrams-08.jpg "Wireframe3")
![wireframe4_img](er diagrams-09.jpg "Wireframe4")
![wireframe5_img](er diagrams-10.jpg "Wireframe5")
![wireframe6_img](er diagrams-11.jpg "Wireframe6")
![wireframe7_img](er diagrams-12.jpg "Wireframe7")
![wireframe8_img](er diagrams-13.jpg "Wireframe8")
![wireframe9_img](er diagrams-14.jpg "Wireframe9")
![wireframe10_img](er diagrams-15.jpg "Wireframe10")
![wireframe11_img](er diagrams-16.jpg "Wireframe10")
![wireframe12_img](er diagrams-17.jpg "Wireframe10")
![wireframe13_img](er diagrams-18.jpg "Wireframe10")
![wireframe14_img](er diagrams-19.jpg "Wireframe10")
![wireframe15_img](er diagrams-20.jpg "Wireframe10")

## ER Diagrams

![erd1_img](er diagrams-01.jpg "ERD1")
This is our global ERD, which encompasses all of the entities and relationships that makeup our database.
![erd2_img](er diagrams-02.jpg "ERD2")
This is our ERD for persona 1, the student.
![erd3_img](er diagrams-03.jpg "ERD3")
This is our ERD for persona 2, the policymaker.
![erd4_img](er diagrams-04.jpg "ERD4")
This is our ERD for persona 3, the activist.

