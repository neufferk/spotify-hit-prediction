# spotify-hit-prediction
# Predicting Spotify Song Popularity

DS 201 – Fall 2025  
 
- Katie Neuffer  
- Kate SantaMaria  
- Abby Sobol  
- Thomas Snyder  
- Kevin Duffy  
---

## Project Overview

Project Question: What makes a Spotify track popular?

Using a public Kaggle dataset of Spotify song, we have created a project to

- Understand which parts of a song result in it being popular, for example, energy, tempo, danceability.
- Train machine learning models to classify tracks as hit or not a hit using the features identified from the first part.
- Make a reccommendation for a recording label of what aspects they should include in a song to ensure they make a hit.

Our goal is to help an recording label decide what kind of song characteristics are more likely to succeed on Spotify.

---

## Business Question

Can we use sound features to predict whether a Spotify track will become popular?

What are the most important sound features to make a hit?

---

## Data
 
Kaggle dataset: Spotify Tracks Popularity
  - https://www.kaggle.com/datasets/lynnxxx/spotify-tracks-popularity-classification  

- Each row = one Spotify track (Includes: track name, artist name, possibly genre and other identifiers)
- popularity score (0–100) (above or equal to 60 is a hit)
- variables include: danceability, energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration, etc

---

## Methods

We followed the data science process:

1. Business Understanding
   - Define stakeholder - The Perspective Musician
   - State the main question and success metrics

2. Data Understanding
   - Load the dataset in Python
   - Basic descriptive statistics
   - Distributions of popularity and important features

3. Data Preparation
   - Drop missing values (Data set had already dropped missing vals)
   - Create a binary target variable:  
     - `hit = 1` if popularity ≥ 60,  
     - `hit = 0` otherwise
     - Histograms of popularity and major audio features
     - Correlation matrix heatmap for numeric features

5. Modeling & Evaluation
   - Baseline Model - Logistic Regression
   - Other Model - Random Forest Classifier
   - Metrics:
     - Accuracy
     - Precision
     - Recall
     - F1 score
     - Confusion matrix

6. Communication & Recommendations
   - Summarize key traits of popular songs
   - Take the results and transform into an easily understandable guide to inform recording labels.
   - Discuss limitations & potential next steps

---

## Key Findings (Summary)
![Correlation Heatmap](confusionlogistic)
![Correlation Heatmap](confusionrandomforest)
![Correlation Heatmap](top15)

- Tracks with **higher danceability and energy** are significantly more likely to be classified as **hits**.
- **Instrumentalness** tends to be **negatively** associated with popularity; fully instrumental tracks are under-represented among hits.
- Our best model (Random Forest) achieved around **XX% accuracy** and **YY% F1 score** on the held-out test set.
- Top 3 most important features for predicting hit status:
  1. Danceability  
  2. Energy  
  3. Loudness (or valence / tempo, depending on final model)

**Practical takeaway for the label:**  
> Focus promotional efforts on tracks that are moderately fast, **danceable**, and **energetic**, with lower instrumentalness and a clear rhythmic pulse.


