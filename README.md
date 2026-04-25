# Chi-Square Term Analysis with MRJob

This project implements a complete **MapReduce pipeline** using `mrjob` to compute **Chi-Square statistics** for measuring the association between terms and categories in a dataset of Amazon reviews.

The pipeline processes raw JSON reviews and outputs the most relevant terms per category based on statistical significance.

---

## Overview

The program performs the following steps:

1. **Tokenization & Filtering**
   - Extracts words from review text
   - Converts to lowercase
   - Removes stopwords
   - Keeps unique words per document (binary presence)

2. **Aggregation**
   - Counts:
     - Term occurrences across documents
     - Documents per category
     - Term-category co-occurrences

3. **Chi-Square Computation**
   - Builds contingency tables
   - Computes Chi-Square score for each (term, category)
   - Outputs top terms per category

---

## Input Format

Each line must be a JSON object with at least:

```json
{
  "reviewText": "This product is great",
  "category": "Electronics"
}
