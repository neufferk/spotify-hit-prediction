# spotify-hit-prediction
# Predicting Spotify Song Popularity

**Course:** DS 201 – Fall 2025  
**Team:**  
- Katie Neuffer  
- Kate SantaMaria  
- Abby Sobol  
- Thomas Snyder  
- Kevin Duffy  
---

## Project Overview

This project explores the question: **What makes a Spotify track popular?**

Using a public Kaggle dataset of Spotify tracks and their audio features, we build a full data science pipeline in Python to:

1. Understand which sound characteristics (e.g., danceability, energy, tempo) are associated with higher popularity.
2. Train machine learning models to classify tracks as **“hit”** vs **“not hit”** using those audio features.
3. Translate our results into clear recommendations for a **music marketing team / record label**.

Our goal is to help a hypothetical label decide **what kind of sound profile is more likely to succeed** on Spotify.

---

## Business Question

> **For a record label choosing which songs to promote, can we use audio features to predict whether a Spotify track will become popular, and what are the most important sound features of a "hit"?**

**Stakeholder:**  
A record label’s marketing and A&R (Artist & Repertoire) team.

**Key Decisions:**

- Which style of tracks to prioritize for promotion.
- What sonic features (danceability, energy, tempo, etc.) are most worth focusing on in production.
- How to describe “hit potential” in a simple, data-driven way.

---

## Data

**Source:**  
- Kaggle dataset: **Spotify Tracks Popularity – Classification**  
  - URL: https://www.kaggle.com/datasets/lynnxxx/spotify-tracks-popularity-classification  

**Description (high level):**

- Each row = one Spotify track  
- Includes:
  - **Target:** popularity score (0–100) and/or popularity label (we use this to create a binary “hit/not hit” target)
  - **Audio features:** danceability, energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration, etc.
  - **Metadata:** track name, artist name, possibly genre and other identifiers

We focus on **numeric audio features** (and a small set of simple categorical fields if available).

---

## Methods

We follow the **full data science process**:

1. **Business Understanding**
   - Define stakeholder (record label)
   - Clarify the main question and success metrics

2. **Data Understanding**
   - Load the dataset in Python (pandas)
   - Explore structure: shape, column types, missingness
   - Basic descriptive statistics
   - Distributions of popularity and key audio features

3. **Data Preparation**
   - Handle missing values (drop or impute)
   - Drop ID/text columns that do not help prediction (track name, artist, etc.)
   - Create a **binary target variable**:  
     - `hit = 1` if popularity ≥ threshold (e.g., 60),  
     - `hit = 0` otherwise
   - Standardize numeric features for certain models (e.g., logistic regression)
   - Train/test split

4. **Exploratory Data Analysis (EDA)**
   - Histograms of popularity and major audio features
   - Scatter plots (e.g., danceability vs popularity, energy vs popularity)
   - Correlation matrix heatmap for numeric features
   - Group comparisons for “hit” vs “non-hit” tracks

5. **Modeling & Evaluation**
   - **Baseline model:** Logistic Regression
   - **More flexible model:** Random Forest Classifier
   - Metrics:
     - Accuracy
     - Precision, Recall, F1 score
     - Confusion matrix
   - Feature importance analysis (from Random Forest)

6. **Communication & Recommendations**
   - Summarize key drivers of popularity
   - Translate findings into plain-English guidance for the record label:
     - What ranges of danceability/energy/tempo are most promising?
     - What to avoid (e.g., fully instrumental or very low-energy tracks)
   - Discuss limitations & potential next steps

---

## Key Findings (Summary)

> *placeholders*

- Tracks with **higher danceability and energy** are significantly more likely to be classified as **hits**.
- **Instrumentalness** tends to be **negatively** associated with popularity; fully instrumental tracks are under-represented among hits.
- Our best model (Random Forest) achieved around **XX% accuracy** and **YY% F1 score** on the held-out test set.
- Top 3 most important features for predicting hit status:
  1. Danceability  
  2. Energy  
  3. Loudness (or valence / tempo, depending on final model)

**Practical takeaway for the label:**  
> Focus promotional efforts on tracks that are moderately fast, **danceable**, and **energetic**, with lower instrumentalness and a clear rhythmic pulse.

---

## Repository Structure

```text
.
├── README.md                # Project overview (this file)
├── spotify_popularity.ipynb # Main analysis notebook (Colab-friendly)
├── data/                    # (Optional) local data storage if needed
├── img/
│   ├── popularity_hist.png
│   ├── corr_heatmap.png
│   └── feature_importance.png
└── docs/                    # For GitHub Pages, if used
