# Surprise Analysis Pipeline

A three-stage NLP pipeline for detecting and measuring surprise intensity in Russian text reviews.

## Overview

This project processes user reviews from the **Geo Reviews Dataset 2023** (`geo-reviews-dataset-2023.csv`) to identify and quantify surprise expressions in Russian text. The pipeline transforms raw reviews through three stages: lemmatisation, semantic weighting, and rule-based surprise labeling.

## Dataset

The dataset contains user reviews with the following columns:

| Column | Description |
|--------|-------------|
| `id` | Unique review identifier |
| `rating` | User rating |
| `text` | Original review text in Russian |
| `is_surprise` | Binary flag (0/1) indicating surprise presence |
| `surprise_intensity` | Intensity level (0 = no surprise, 1 = weak, 2 = medium, 3 = strong) |

## Pipeline

### 1. Text Lemmatisation
Preprocesses Russian text while preserving semantic context. Converts emojis into semantic markers (`EMOJI_HAPPY`, `EMOJI_ANGRY`), recognises CAPS words (`CAPS_важно`), handles punctuation, and applies morphological analysis with POS filtering.

### 2. Weight Calculation
Transforms lemmatised tokens into weighted category vectors using a dictionary-based approach. Each token is mapped to `(category, weight)` pairs, creating dense vector representations for downstream analysis.

### 3. Surprise Labeling
Rule-based system that detects surprise through category combinations and support maps. Assigns intensity levels based on category weights and configurable thresholds.

## License
Distributed under the MIT License. See the LICENSE file for details.
