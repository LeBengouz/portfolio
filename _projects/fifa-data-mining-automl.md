---
layout: page
title: From Data Mining to AutoML
description: Student project exploring the main stages of an end-to-end machine learning workflow on FIFA 2025 player data.
img: assets/img/projects/fifa-automl/fifa_25.jpeg
importance: 2
category: work
related_publications: false
---

**Python · Pandas · scikit-learn · TPOT · PyCVI · Matplotlib · Seaborn**

[View source code on GitHub](https://github.com/LeBengouz/Fouille_Donnees_et_Auto_ML)

## Project Overview

This **Master's student project** was meant to explore a wide range of tasks involved in a machine learning project, from raw data preparation to model evaluation and AutoML.

Using **FIFA 2025 player data**, I worked through four main stages:

1. data cleaning, data exploration and analysis, feature engineering,
2. unsupervised clustering,
3. classification and regression,
4. automated machine learning with TPOT.

The goal was to obtain good predictive performance, but also to understand **preprocessing choices, feature and model selection**.


## Data & Feature Engineering

The initial dataset contained **more than 18,000 players and 79 attributes**, including player characteristics, technical abilities, club information, wages, market values...

Since some attributes were missing, two datasets had to be merged by matching player's ID.


The preprocessing pipeline included:

- **Data cleaning**: handling missing values and converting raw fields into usable numerical formats.
- **new features**: creating age groups, BMI, broader player roles, and aggregated football skill scores.
- **Transforming features**: discretizing features into meaningful categories, standardizing features, and encoding categorical variables.


## Unsupervised Learning

I compared several clustering approaches, including **K-Means, DBSCAN and Ward hierarchical clustering**. The experiments highlighted the difficulty of finding clearly interpretable groups in high-dimensional and heterogeneous player data. 

I also used cluster similarity as a simple **recommendation system**. Then, one can find the player closest to another one. For example, Kylian Mbappé could be replaced by **Vinícius Júnior** based on algorithms that identify the nearest profile.



## Prediction & Model Comparison

I then studied both **classification and regression** problems.

For classification, I predicted discretized player wages (`DWage`) and market values (`DValue`) using:

- Logistic Regression,
- Random Forest,
- Gradient Boosting.

Player ratings and potential were strongly linked to market value. Then, using only the five most informative features showed that most of the predictive signal came from a small set of variables.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/fifa-automl/top_20_corr.png" title="Most correlated features with player value" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
Feature-correlation analysis for player-value prediction.
</div>

## AutoML

Finally, I used **TPOT** to explore automated machine learning and compare automatically generated pipelines with the manually designed workflow from the previous experiments.

