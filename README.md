# Steam Playtime Prediction

A machine learning project predicting how many hours a Steam user will play a game using review data, user behavior, game metadata, and text-derived features.

## Overview

This project explores the problem of predicting Steam game playtime from a highly sparse user-item interaction dataset. The goal was to compare collaborative filtering, baseline regression models, and feature-based machine learning approaches for a recommendation-style prediction task.

The dataset contained approximately 500,000 reviews, 350,000 users, and 994 games, creating a highly sparse interaction matrix. I engineered collaborative, content-based, and text-derived features, then evaluated multiple models using held-out test performance.

## Motivation

Predicting playtime is more difficult than predicting whether a user liked a game because playtime is continuous, noisy, and strongly affected by user behavior, game popularity, genre, price, and review context.

This project was designed to answer:

- Can user and item behavior explain playtime?
- Do game metadata and text-derived review features improve predictions?
- How do simple baselines compare to regularized regression and matrix factorization approaches?
- What are the limitations caused by cold-start users/items and sparse interactions?

## Dataset

The project used a Steam reviews dataset with approximately:

- 500,000 reviews
- 350,000 users
- 994 games
- 99.86% sparse user-item interaction matrix

Due to dataset size and licensing considerations, raw data is not included in this repository. See `data/README.md` for dataset setup notes.

## Features

I engineered 36 total features across three categories:

### Collaborative Features
- User average playtime
- Game average playtime
- User activity level
- Game popularity
- User-item interaction statistics

### Content Features
- Game price
- Genre indicators
- Early access status
- Game metadata features

### Text-Derived Features
- Review length
- Sentiment-style indicators
- Emotion keywords
- Keyword frequency features

## Models Evaluated

The project compared several approaches:

- Global mean baseline
- User mean baseline
- Item mean baseline
- User + item bias model
- Linear regression
- Ridge regression
- Lasso regression
- Matrix factorization / ALS-style collaborative filtering

## Evaluation

Models were evaluated using:

- R² score
- Mean Absolute Error (MAE)
- Median Absolute Error
- Train/test split validation
- Baseline comparisons
- Leakage prevention checks

The best-performing models achieved approximately **R² = 0.54** on held-out data, showing that user behavior, game-level trends, and engineered features explain a meaningful portion of playtime variance.

## Key Findings

- Collaborative features were the strongest predictors of playtime.
- User and item average behavior provided strong baseline performance.
- Regularized regression helped control overfitting across engineered features.
- Text-derived features added some signal but were weaker than user/game behavior.
- Sparse interactions and cold-start users/items remained major limitations.
- A hybrid recommendation strategy would likely perform better in production.

## Limitations

- The dataset was highly sparse, limiting predictions for users or games with few interactions.
- Review text features were relatively simple and could be improved with embeddings or transformer-based models.
- The project focused on offline evaluation rather than production deployment.
- More robust time-based validation could better simulate real recommendation settings.

## Future Improvements

- Add transformer embeddings for review text
- Improve cold-start prediction with richer game metadata
- Add neural collaborative filtering
- Build a lightweight API for model inference
- Add experiment tracking with MLflow or Weights & Biases
- Use time-based validation for more realistic evaluation

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-Learn
- SciPy
- Matplotlib
- Jupyter Notebook

## Project Status

Completed as a machine learning / recommender systems project. Currently being cleaned and documented as part of my AI/ML portfolio.