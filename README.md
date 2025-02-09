# Ecosphere-Forecasting-Competition

This repository contains my solution and submission for the [Ecosphere Forecasting competition](https://www.kaggle.com/competitions/ecosphere-forecasting/overview) on Kaggle. The goal of the competition is to predict the air quality level (Good, Moderate, Poor, Hazardous) based on environmental factors and pollutant concentrations.

---

## Table of Contents

- [Introduction](#introduction)
- [Problem Statement](#problem-statement)
- [Data Description](#data-description)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Modeling Approach](#modeling-approach)
- [Hyperparameter Tuning](#hyperparameter-tuning)
- [Results and Evaluation](#results-and-evaluation)
- [Submission File](#submission-file)
- [How to Run](#how-to-run)
- [Dependencies](#dependencies)
- [References](#references)

---

## Introduction

Air quality is a critical environmental factor that affects public health and quality of life. This competition aims to build a predictive model to classify air quality into four categories: Good, Moderate, Poor, and Hazardous. This repository documents the entire workflow, from data exploration and preprocessing to model training, evaluation, and final submission.

---

## Problem Statement

Given a dataset that includes various environmental and pollutant measurements (e.g., Temperature, Humidity, PM2.5, PM10, NO₂, SO₂, CO, Proximity to Industrial Areas, and Population Density), the task is to predict the air quality level for each record. The target variable is categorical, with the following labels:

- **Good:** Clean air with low pollution levels.
- **Moderate:** Acceptable air quality but with some pollutants present.
- **Poor:** Noticeable pollution that may cause health issues for sensitive groups.
- **Hazardous:** Highly polluted air posing serious health risks.

---

## Data Description

The dataset provided for this competition includes the following columns:

- **Id:** Unique identifier for each observation.
- **Temperature:** Average temperature (°C) of the region.
- **Humidity:** Relative humidity (%) recorded in the region.
- **PM2.5:** Fine particulate matter concentration (µg/m³).
- **PM10:** Coarse particulate matter concentration (µg/m³).
- **NO₂:** Nitrogen dioxide levels (ppb).
- **SO₂:** Sulfur dioxide levels (ppb).
- **CO:** Carbon monoxide levels (ppm).
- **Proximity_to_Industrial_Areas:** Distance (km) to the nearest industrial area.
- **Population_Density:** Number of people per km² in the region.
- **Air Quality:** Target variable representing the air quality level.

---

## Data Preprocessing

- **Missing Values:** No value is missing in the data. 
- **Scaling:** Features were scaled using the `RobustScaler` to mitigate the impact of outliers.
- **Encoding:** The target variable "Air Quality" was encoded as:
  - Good: 0
  - Moderate: 1
  - Poor: 2
  - Hazardous: 3

## Exploratory Data Analysis (EDA)
- **Feature Distributions:**  Histograms and density plots for each feature segmented by air quality level.
- For example: 
![Distribution of Population_Density by Air Quality](https://github.com/user-attachments/assets/85302e7a-721d-46a8-9c47-8fd96b7fe9c3)
- **Correlation Detection:** Display inter-feature correlations to guide feature selection or engineering.
- ![unknown](https://github.com/user-attachments/assets/aa63207c-8a17-4854-8ad4-e71158ece414)

## Modeling Approach 
- **Model Selection:** For this competition, several classifiers were explored:
- Logistic Regression
- Decision Trees
- Random Forests
- CatBoost (final model)
- **CatBoost Model:** The final model was built using CatBoostClassifier due to its superior performance on tabular data and ease of handling various feature types.

## Hyperparameter Tuning

Bayesian optimization (using libraries like Optuna) was used to fine-tune the hyperparameters of the CatBoost model. This section documents the search process and the best hyperparameters discovered.

## Results and Evaluation

Accuracy: validation set accuracies: **0.9583**.

Confusion Matrix: 

![True label](https://github.com/user-attachments/assets/9942f940-86c9-4b1b-938b-57789e8b2387)


## How to Run

git clone [https://github.com/yourusername/ecosphere-forecasting.git](https://github.com/leoooc/Ecosphere-Forecasting-Competition.git)
cd ecosphere-forecasting

## Dependencies

-Python 3.x
-Pandas
-NumPy
-scikit-learn
-CatBoost
-Optuna
-Matplotlib
-Seaborn

## References
[Kaggle Ecosphere Forecasting Competition](https://www.kaggle.com/competitions/ecosphere-forecasting/overview)



