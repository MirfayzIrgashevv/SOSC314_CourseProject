# 📊 Understanding Review Helpfulness in Online Marketplaces

Even though online reviews are not equally helpful, they play important role when consumer is making decision. This project applies machine learning and text-as-data methods to examine how consumers express opinions in product reviews and how these expressions influence others

Using the **Amazon Fine Food Reviews dataset**, we perform sentiment analysis and investigate linguistic and stylistic features that affect how much value other users assign to a review.

## 🎯 Research Objectives

In addition to **sentiment analysis (positive vs. negative)**, this project addresses the following questions:

* **Are emotionally expressive reviews or informational reviews more helpful to consumers?**
* **Does review length increase perceived credibility and helpfulness?**
* **Are negative reviews perceived as more helpful than positive reviews?**

Together, these questions explore how **tone, content, and effort** shape trust in online reviews.

## 📂 Dataset

**Amazon Fine Food Reviews Dataset**
🔗 [https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews](https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews)

### Dataset Features

* `ProductId`, `UserId`, `ProfileName`
* `HelpfulnessNumerator`, `HelpfulnessDenominator`
* `Score` (numeric rating)
* `Time` 
* `Summary`, `Text` (review content)

**Unit of analysis:** Individual product review

## ⚠️ Dataset Setup Instructions (Required)

Due to GitHub’s file size limitations (the dataset exceeds **100MB**), the dataset is **not included in this repository**.

To run the project successfully:

1. Download the dataset from Kaggle using the link above.
2. Place the downloaded file into the project directory.
3. Rename the file from **`Reviews.csv`** to **`reviews.csv`** (lowercase), as the code expects this exact filename.

## 🛠️ Methods Used

* Sentiment analysis
* Text preprocessing and feature extraction
* Statistical comparison of review characteristics
* Machine learning models for classification and interpretation

## 🎓 Course Information

**Course:** SOSC 314

# 📊 Weekly Progress Report — SOSC 314 Course Project

**Project:** Understanding Review Helpfulness in Online Marketplaces

---

## Week 2: Research Topic, Dataset Selection & Initial Exploration

This week focused on defining the research topic, selecting an appropriate dataset, and conducting initial exploratory analysis.

* Defined the research focus on **review helpfulness and credibility** in online marketplaces
* Selected the **Amazon Fine Food Reviews** dataset from Kaggle (SNAP dataset)
* Examined dataset structure, features, and missing values
* Analyzed key variables related to helpfulness and ratings

Initial exploration showed that the dataset contains over **568,000 reviews**, with strong class imbalance in review scores. Most reviews are highly positive, with **5-star ratings dominating the distribution**, while lower ratings appear less frequently. Descriptive statistics revealed a strong positive bias in ratings (mean score = 4.18, median = 5), which is important to consider for later modeling and interpretation. 

---

## Week 3: Feature Construction & Sentiment Analysis

The main objective of this week was to transform unstructured text into meaningful and interpretable features.

* Inspected all columns for missing values and handled incomplete entries
* Created a **helpfulness_ratio** feature using HelpfulnessNumerator and HelpfulnessDenominator
* Addressed zero-denominator cases by assigning a ratio of 0 to preserve data
* Added **review_length** to capture informational content
* Filtered out reviews with fewer than 15 words to reduce noise

Sentiment analysis was conducted using **TextBlob**, generating:

* `sentiment_score` (continuous, −1 to 1)
* `sentiment_label` (POSITIVE, NEGATIVE, NEUTRAL)

This step enabled early incorporation of emotional tone into the analysis while maintaining a lightweight and interpretable pipeline. The sentiment distribution showed a heavy dominance of positive reviews, highlighting another form of imbalance in the dataset. 

---

## Week 4: Text Preprocessing & Modeling Review Helpfulness

This week focused on preparing text data and modeling how review characteristics affect perceived helpfulness.

* Converted all text to lowercase to ensure consistency
* Removed punctuation, numbers, and non-alphabetic characters to reduce noise
* Expanded the stopword list and applied **Porter stemming** to normalize vocabulary
* Created a `clean_text` column for modeling

To address the question *“Does review length increase perceived credibility and helpfulness?”*:

* A correlation analysis showed a weak positive relationship (r = 0.123)
* Linear Regression estimated a small but positive effect of review length
* Random Forest Regressor captured non-linear patterns but still explained limited variance (R² ≈ 0.023)

Feature importance analysis showed that **review length accounted for ~96.7% of predictive power**, while sentiment contributed a smaller share. This suggests that informational content matters more than emotional tone for helpfulness. 

---

## Week 5: Diagnostics, Robustness & Expressiveness Analysis

The final week focused on diagnostics, robustness checks, and answering the third research question:
**“Are emotionally expressive reviews or informational reviews more helpful to consumers?”**

* Computed **subjectivity scores** using TextBlob to measure emotional expressiveness
* Classified reviews as:
  * **INFORMATIONAL** (subjectivity < 0.5)
  * **EMOTIONAL** (subjectivity ≥ 0.5)
* Compared average helpfulness ratios across expressiveness types

Results showed that **informational reviews have higher average helpfulness ratios (0.424) than emotional reviews (0.399)**. A Welch’s two-sample t-test confirmed this difference is **statistically significant** (p ≪ 0.05).

Robustness checks included:

* Redefining helpfulness as a binary outcome
* Varying subjectivity thresholds (0.4, 0.5, 0.6)

Across all tests, the conclusion remained stable: **informational reviews are consistently perceived as more helpful than emotionally expressive ones**, supporting the robustness and validity of the findings. 

