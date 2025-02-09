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
- [Conclusion and Future Work](#conclusion-and-future-work)
- [Acknowledgements](#acknowledgements)
- [References](#references)

---

##Introduction

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

- **Missing Values:** Describe any missing values handling (if applicable).
- **Scaling:** Features were scaled using the `RobustScaler` to mitigate the impact of outliers.
- **Encoding:** The target variable "Air Quality" was encoded as:
  - Good: 0
  - Moderate: 1
  - Poor: 2
  - Hazardous: 3

Example code snippet:
```python
from sklearn.preprocessing import RobustScaler

# Map target labels to numbers
y = train_raw['Air Quality'].map({'Good': 0, 'Moderate': 1, 'Poor': 2, 'Hazardous': 3})
X = train_raw.drop(columns=['Id', 'Air Quality'])

# Apply scaling
scaler = RobustScaler()
X_scaled = scaler.fit_transform(X)
