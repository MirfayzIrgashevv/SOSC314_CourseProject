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


### **Week 2: Text-as-Data Methods**

* Defined the research focus on sentiment analysis of online product reviews.
* Selected the Amazon Fine Food Reviews dataset containing user-generated review text and metadata.
* Framed the task as a **text-as-data problem**, treating each review as a document unit.
* Applied text preprocessing and basic exploratory analysis to understand review characteristics and text structure.

### **Week 3: Data Construction, Cleaning**

* Cleaned the dataset by removing reviews with missing text and invalid entries.
* Created additional features such as **review length** to capture effort and informational depth.
* Applied **TextBlob** to perform sentiment analysis and generate sentiment-related variables.

