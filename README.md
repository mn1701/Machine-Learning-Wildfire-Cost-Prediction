# Wildfires: Predicting the Cost

### Authors:
- Reilly Dunn
- Mateo Escobar
- Owen Hoover
- Minh Nguyen

**Date**: March 14, 2024  

[GitHub Repository](https://github.com/ReillyDunn-UCDavis/ECS-171-Wildfire-Project)  

[Demo Video](https://drive.google.com/file/d/1uX1qRkTAR2GRR7SsL_c1m3eFLZ3clsvc/view?usp=sharing)

## Table of Contents
- [Project Overview](#project-overview)
- [Introduction](#introduction)
- [Dataset Description](#dataset-description)
- [Proposed Solutions & Experimental Results](#proposed-solutions--experimental-results)
  - [Fire Duration Prediction](#fire-duration-prediction)
  - [Fire Size Prediction](#fire-size-prediction)
  - [Cause of Fire Prediction](#cause-of-fire-prediction)
  - [Financial Cost Prediction](#financial-cost-prediction)
- [Conclusion and Discussion](#conclusion-and-discussion)
- [References](#references)

## Project Overview
This project focuses on wildfires and predicting the damage they will cause using machine learning models. Specifically, it addresses:
- **Fire Size** (Classification and Regression)
- **Duration of Fires** (Regression)
- **Cause of Fires** (Classification)
- **Dollar Damage** (Classification)

We gathered data from several sources, including the National Interagency Fire Center (NIFC), National Oceanic and Atmospheric Administration (NOAA), and California Department of Forestry and Fire Protection’s “Redbooks.”

## Introduction
Wildfires are destructive and difficult to predict, with increasing frequency due to climate change. California, in particular, faces a high number of wildfires every year, impacting the local economy, environment, and human health. This project aims to leverage machine learning techniques to predict various wildfire-related factors, assisting emergency responders and policymakers in resource allocation and decision-making.

The models we developed cover:
1. **Fire Size**: Classification of the fire size into classes based on the number of acres burned.
2. **Fire Duration**: Estimation of how long the wildfire will last.
3. **Cause of Fire**: Determining whether the fire was human-caused or due to natural factors.
4. **Financial Impact**: Predicting the dollar damage a wildfire will cause based on its size and location.

## Dataset Description
The primary dataset used comes from [Kaggle's US Wildfire Records (6th Edition)](https://www.kaggle.com/datasets/behroozsohrabi/us-wildfire-records-6th-edition). This dataset contains over 2.3 million records of wildfires from 1992 to 2020 in the continental U.S. It includes fire size, discovery date, and location (latitude and longitude). 

In addition to this dataset, we appended environmental data (temperature and precipitation) from NOAA and used fire cost data from the California Department of Forestry and Fire Protection’s "Redbooks" for dollar damage predictions.

## Proposed Solutions & Experimental Results

### Fire Duration Prediction
We used a **Linear Regression model** to predict how long a fire will burn based on environmental conditions and the location of the fire. The input features include:
- Precipitation in the month
- Average temperature in the month
- The state where the fire occurred

Results:
- **Mean Squared Error (MSE)**: 29.19
- **Root Mean Squared Error (RMSE)**: 5.40
- **R-squared (R²) score**: 0.096

The model accuracy was relatively low (~9%) due to data limitations, such as a lack of diversity in the dataset (many fires were from Arizona and California). Further improvements could include additional features like wind speed and humidity.

### Fire Size Prediction
We developed both **classification** and **regression** models for predicting fire size. The classification model predicts the class size (A to G), while the regression model predicts the actual number of acres.

- **Classification Model**: Accuracy of 62.89%, but mostly predicts small fires.
- **Regression Model**: Mean Squared Error of 2.44e-6. The model performs better but still struggles with larger fire predictions due to data imbalance (few large fires).

### Cause of Fire Prediction
We developed two models for predicting the cause of the fire:
1. **Binary Classification**: Predicts whether the fire was caused by humans or natural factors. The logistic regression model achieved an accuracy of 73.07%.
2. **Multi-class Classification**: Predicts more specific causes of fire. The Multi-Level Perceptron achieved an accuracy of 59.6%.

### Financial Cost Prediction
Given the lack of financial data in our main dataset, we used a second dataset from the California Department of Forestry and Fire Protection’s “Redbooks.” We built a **Neural Network classification model** to predict the dollar damage. The model achieved an accuracy of 30-40%, which is better than random guessing (20%).

## Conclusion and Discussion
Our models provided valuable insights into wildfire predictions, with environmental factors such as temperature and precipitation being key predictors. However, the project also highlighted data limitations in wildfire records. To improve future models, better data collection—particularly regarding environmental conditions at the time of the fire—will be essential.

## References
- [EPA Climate Change Indicators: Wildfires](https://www.epa.gov/climate-indicators/climate-change-indicators-wildfires)
- [National Interagency Coordination Center 2022 Annual Report](https://www.nifc.gov/sites/default/files/NICC/2-Predictive%20Services/Intelligence/Annual%20Reports/2022/annual_report.2.pdf)
- Gill, A.M., Stephens, S.L., & Cary, G.J. (2013). The worldwide “wildfire” problem. *Ecological Applications*, 23(2), 438-454. https://doi.org/10.1890/10-2213.1.
- Gorte, R. (2013). The Rising Cost of Wildfire Protection. *Headwaters Economics*. https://www.baileyhealthyforests.org/wp-content/uploads/2013/12/fire-costs-background-report.pdf
