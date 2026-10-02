# Customer Feedback Analysis & Automated Response

The idea of this project was to take customer reviews from an e-commerce dataset, identify the reviews that need more attention, understand the common complaints, and use Generative AI to draft responses for a few critical cases.

## What I did

The project has four main parts:

1. Cleaned and prepared the review data using Pandas.
2. Identified critical reviews using a simple rule: 1 or 2 star ratings.
3. Looked at common complaint keywords and grouped some complaints into categories such as Fit & Size, Quality, Material & Fabric, and Delivery / Shipping.
4. Selected 3 detailed critical reviews and used the Gemini API to generate personalized apology emails.

No machine learning model was used for identifying critical reviews. The filtering is intentionally rule-based as required in the assessment.

## Data Cleaning

The dataset contains customer reviews along with ratings, product information, recommendation information, and other fields.

The cleaning steps include:

- Removing the exported index column.
- Removing duplicate rows.
- Stripping extra spaces from text columns.
- Checking missing values.
- Removing rows where the review text is missing.
- Converting the review text to lowercase.
- Removing HTML tags, special characters, and extra spaces.
- Keeping the original review text unchanged.

## Critical Review Logic

For this project, I treated reviews with a rating of 1 or 2 as critical.

```python
critical_reviews = review_df[review_df["Rating"] <= 2].copy()
