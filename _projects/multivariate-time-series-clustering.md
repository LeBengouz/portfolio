---
layout: page
title: Multivariate Time-Series Clustering
description: Benchmarking clustering methods on GPS trajectories and adapting ShapeNet for fully unsupervised shapelet discovery.
img: assets/img/graph_shapelets.png
importance: 1
category: work
related_publications: false
---

**Python · PyTorch · tslearn · scikit-learn · Marimo · Plotly**

[View source code on GitHub](https://github.com/LeBengouz/PFE_Clustering_Multivariate_Time_Series)

## Project Overview

This end-of-studies project explores **unsupervised clustering of multivariate time series**. It first compared classical distance-based methods then tackled **deep representation learning**.

The objective was to identify **characteristic subsequences (shapelets)** in time series. This projects explored and benchmarked different algorithms on **GPS traces** to apply them to I/O time series. The identified shapelets could later be represented as a transition graph of recurring patterns.



## Data

Experiments were conducted on the **CabSpotting dataset**, containing GPS traces from **536 taxis in San Francisco**.


I transformed the raw taxi histories into individual trips by detecting changes in occupancy status. Each trip is therefore represented as a **variable-length 2 dimensions time series** of latitude and longitude coordinates. However, the tested algorithms should be robust to higher-dimensional time series.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cabspotting.jpg" title="Cabspotting data on a map." class="img-fluid rounded z-depth-1" %}
    </div>
</div>



## Approach

I first implemented classical clustering baselines using `tslearn`:

- **TimeSeries K-Means with Euclidean distance**
- **TimeSeries K-Means with Dynamic Time Warping (DTW) and DBA barycenters**

In order to qualitatively evaluate the clusters, reference groups of similar trajectories where selected, such as:
- routes around **Golden Gate Park**,
- trips between **San Francisco Airport and the city center**,
- short trajectories corresponding to passenger-search behavior...

It allowed me to compare clustering results against interpretable patterns.


## From Clustering to Shapelets

This first work helped me familiarize myself with the data and compare basic algorithms. However, it did not directly solve the second objective of the project: **identifying characteristic subsequences inside the time series**. 

I therefore explored and adapted **ShapeNet**, a deep-learning method that learns representations of candidate subsequences before clustering them into representative shapelets.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Schema_ShapeNet.png" title="ShapeNet pipeline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
ShapeNet pipeline: subsequences are encoded into a latent space before representative shapelets are selected.
</div>

## Main Contributions

No usable version of ShapeNet was available. Therefore, the algorithm had to be reimplemented.

I adapted the implementation to:
- run on **fully unlabeled datasets**,
- convert CabSpotting trajectories into **ARFF format**,
- adjust the **model pipeline**,
- support **DBSCAN** instead of K-Means for shapelet discovery, as it was better suited to our problem.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/graph_shapelets.png" title="Shapelet transition graph concept" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
Project goal: Represent characteristic subsequences as nodes, with connections showing the probability of transitions between important patterns.
</div>

## Key Takeaways

This project combined **data preprocessing, time-series clustering, model evaluation, deep representation learning, and adaptation to projects needs**.

