# Entity-Resolution-Project
Entity resolution and fuzzy matching system for structured company data.

This project showcases a complete data processing and entity resolution built for presales data, with the goal of identifying and scoring the best company matches from Veridion data.

## Project Overview

The dataset includes company records enriched with various metadata (e.g., name, address, URLs, etc.). The objective was to clean, normalize, and match the input company records with the most relevant Veridion profiles using fuzzy logic and scoring heuristics.

---

## Key Steps and Functionality

### 1. **Library Imports & Data Loading**
- Essential libraries such as `pandas`, `numpy`, `seaborn`, and `fuzzywuzzy` are used.
- The input dataset is loaded from a `.csv` file.

### 2. **Data Preparation**
- All string fields are cleaned: converted to lowercase, stripped of whitespace and unwanted special characters.
- This ensures consistency for all downstream text comparisons.

### 3. **Entity Resolution with Fuzzy Matching**
- Company name variants (e.g., `company_legal_names`, `company_commercial_names`) are compared against the `input_company_name` using fuzzy logic.
- Scores are computed for each name match and aggregated.

### 4. **Location-Based Scoring**
- Location fields (e.g., country, city, postcode) are scored separately.
- All `_score` variables are mapped to normalized `_grade` values between 0 and 1.

### 5. **Weighted Aggregation**
- A weighted average is used to compute a final `match_grade` score across all relevant dimensions (name, address components).
- Weights can be tuned based on match importance.

### 6. **Best Match Selection**
- For each input row, the highest scoring Veridion match is selected.
- Duplicates based on `veridion_id` are resolved by keeping only the match with the highest score.

### 7. **Confidence Labeling**
- A confidence label (e.g., “Very High Confidence”, “Moderate Confidence”, etc.) is applied based on `match_grade` ranges.

---

## Outputs & Visualizations

- **Distribution of Match Grades**  
  Histogram and KDE plots to evaluate how confident the model is overall.

- **Confidence Label Breakdown**  
  Count plots showing how many matches fall into each confidence category.

- **Top Countries by Match Quality**  
  Aggregated statistics to evaluate country-level matching performance.

---

## How to Run

1. Clone the repository.
2. Install required packages (e.g., via `pip install -r requirements.txt`).
3. Run the notebook `Veridion_Assignment.ipynb`.

---

## Notes

- The matching logic is highly configurable.
