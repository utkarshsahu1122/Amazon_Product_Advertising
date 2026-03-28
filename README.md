# Amazon Apparel Recommendation System

A content-based filtering recommendation engine built on a 183K-item Amazon apparel dataset, using TF-IDF vectorization and cosine similarity to surface relevant product matches.

## Overview

This project scrapes and preprocesses a large-scale Amazon apparel dataset, then builds a recommendation pipeline that matches products based on textual and categorical attributes — without relying on user history or collaborative signals.

## Features

- **Data pipeline**: Handles missing values, duplicates, and inconsistent categories across 183K+ items
- **TF-IDF vectorization**: Encodes 10+ product attributes (title, category, brand, description, etc.) into feature vectors
- **Cosine similarity matching**: Computes pairwise similarity to retrieve the most relevant recommendations
- **Threshold tuning**: Iteratively calibrated similarity thresholds and feature weights for precision improvement
- **Baseline comparison**: Evaluated against a popularity-based baseline across 5+ apparel categories

## Results

| Metric | Score |
|---|---|
| Recommendation precision | ~85% |
| Reduction in irrelevant results | ~30% over baseline |

## Tech Stack

- **Python**
- **Scikit-learn** — TF-IDF, cosine similarity
- **Pandas** — data preprocessing and feature engineering
- **NumPy** — numerical operations

## How It Works

1. Raw dataset is scraped and cleaned (null handling, deduplication, category normalization)
2. Product attributes are combined and vectorized using `TfidfVectorizer`
3. Cosine similarity matrix is computed across all items
4. Given a query product, the top-N most similar items are returned
5. Precision is evaluated against manually labeled relevant items per category

## Dataset

Amazon apparel dataset — ~183,000 items across multiple categories (shirts, dresses, footwear, etc.)

## Usage

```bash
git clone https://github.com/<your-username>/amazon-apparel-recommendation
cd amazon-apparel-recommendation
pip install -r requirements.txt
python recommend.py --product_id <ID> --top_n 10
```

## Project Structure

```
├── data/                  # Raw and cleaned dataset
├── notebooks/             # EDA and experimentation
├── src/
│   ├── preprocess.py      # Data cleaning pipeline
│   ├── vectorizer.py      # TF-IDF feature extraction
│   └── recommend.py       # Similarity and recommendation logic
├── requirements.txt
└── README.md
```
