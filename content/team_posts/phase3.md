---
title: "Project - Phase III"
date: 2025-05-27
draft: false
description: "Project Description"
slug: "phase3post"
tags: ["project", "Setup"]
authors:
  - "mayaellis"
  - "maxrobinson"
  - "aretimakropoulos"
  - "zoyasiddiqui"
showAuthorsBadges: false
---

# Project: Phase 3 Deliverable

Has your team made any updates to your project plan since the
submission of Phase II? Examples include:

- detail any updates/modifications to data model
- give a bulleted list of all tables and if the data will be sourced or
  generated
- detail the features being used for ML and provide reasonable explanation
  why those features are the chosen ones
- discuss any major/surprising issues found during ML model exploration
- provide a REST API Matrix in table format indicating your proposed routes.
  Be sure to tie back to either wireframes and/or User Stories.
- provide screenshots of the mocked up app and results of the implemented
  functionality, including calling the ML model

## Changes to the model since Phase 2

### Data issues

Upon revisiting our EDA and attempting to write our PCA, we noticed significant gaps in the data we had for
features such as Happiness index and Infrastructure scores. Many countries completely lacked the needed infrastructure score data, this meant our Cosine similarity model and our planned PCA and Autoregression model needed to be changed. Our Cosine model was inaccurate because it was missing certain countries entirely because they had no data for infrastructure.

To resolve this immediate issue, we decided to drop the infrastructure feature because we valued having more nations to be compared than having more features to compare.

This decision has implications for our supervised model as well. Because of the many random missing datapoints across all features, years and countries, we must find a way to plug the gaps.

We can solve the above by averaging the data from the previous and next year and inputting it as dummy data in the years that are missing some. We would definitely lose accuracy by doing this but otherwise we would have insufficient data. Alternatively, we could build another ML model to predict the most likely values for those missing years by using the previous and next years for that country. However, I don't think we have the time to implement such a model on such short notice.

Our PCA aims to reduce the number of features from 20 to at most 4, after which we will add a covid column.

### List of Data sources

- Health, Environment, Education, Safety scores and happiness per country per year. (missing datapoints as explained above)
-
