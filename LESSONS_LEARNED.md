# Lessons Learned

This document captures short, practical lessons from the recent data-review additions to `job_skill_analysis.ipynb`.

## Goal
- Do a quick, reproducible exploratory data review of the job-postings dataset(s): shapes, dtypes, summary statistics, uniques, distributions, per-feature checks, and correlations.

## What worked well
- Adding small, focused cells at the end of the notebook made the review easy to run interactively.
- Using Pandas' built-in methods (shape, dtypes, describe, value_counts) gives fast, reliable summaries.
- Seaborn + matplotlib produce readable boxplots and heatmaps that highlight distributional issues and feature correlations.

## Issues encountered / cautions
- Large numbers of numeric columns produce very tall histogram outputs when plotted one-per-row. Consider grouping or plotting only selected features.
- Object/date-like columns may need parsing or dtype conversion to extract meaningful numeric/date summaries.
- Some categorical columns may have many unique values; printing full value_counts can be noisy — limit to top-k.
- Missing values are not automatically handled; visual summaries and value_counts include NaNs but further imputation/cleaning is required for downstream modeling.

## Recommendations / next steps
- Clean and standardize dtypes early: parse dates, convert numeric-like strings, cast low-cardinality object columns to `category`.
- Add a small export (CSV/HTML) of the per-feature summary for faster offline review.
- For plotting, either sample the dataset or select a subset of important numeric features to avoid huge figures.
- Add a data-quality cell that reports percent missing per column and basic cardinality checks.
- If downstream modeling is planned, add feature-engineering cells and split into a reproducible pipeline (e.g., saving cleaned data to `data/cleaned.csv`).

## How to re-run
1. Open `job_skill_analysis.ipynb` in Jupyter or VS Code.
2. Run the already-loaded import cell (top of the notebook) so `pandas`, `numpy`, `matplotlib`, and `seaborn` are available.
3. Run the new cells appended at the end (or choose "Run All Cells").

Dependencies: pandas, numpy, matplotlib, seaborn


---
Generated: October 27, 2025
