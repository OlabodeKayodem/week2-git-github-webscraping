# Week 2 AI Saturday Assignment webscraping
Week 2 Assessment for ML Flipped Cohort — Git &amp; GitHub, Web Scraping, This repository contains my submission for Week 2 of the ML Flipped Cohort.

## Project Overview
The goal is to:
- Create a GitHub repository
- Scrap data from a publicly available website
- Push both the scraping code and the scraped dataset to this repository

## Website Chosen
I chose to scrape **IBM Video Data** because it provides useful data that can be used for future ML projects.

## Project Timeline & Challenges Faced

### 1. IBM Dataset Stage
- **Goal:** Practice basic data cleaning, inspection, and transformation.
- **Tools Used:** Python (Pandas), VS Code.
- **Challenges:**
  - **Data Import Errors:** Some CSV files had encoding mismatches that required specifying `encoding= utf-8'`.
  - **Column Mismatch:** Unexpected headers due to an extra row in the dataset.
  - **Missing Values:** Several columns had missing data, requiring imputation or removal.

### 2. Transition to Book Dataset
- **Goal:** Apply the same cleaning principles to a new dataset containing book information and currency values.
- **Challenges:**
  - **Currency Symbol Issues:** Prices were stored with symbols like `Â£`, `£`, and other characters due to encoding problems.
  - **Encoding Problem:** The `Â` before the pound sign came from a UTF-8 file being misread as Windows-1252 or similar encoding.
  - **String-to-Number Conversion:** Needed to strip currency symbols and convert prices to `float` for calculation.
  - **Data Consistency:** Some price fields were blank or contained unexpected strings, which caused conversion errors.

### 3. Fixing the Currency Issue
- **Approach Taken:**
  1. Used Python string replacement methods (`str.replace`) to remove unwanted symbols.
  2. Corrected encoding at file load by explicitly using:
     ```python
     df = pd.read_csv('filename.csv', encoding='utf-8')
     ```
  3. Converted cleaned strings to numeric using:
     ```python
     df['price'] = df['price'].str.replace('£', '').str.replace('Â', '')
     df['price'] = pd.to_numeric(df['price'], errors='coerce')
     ```
- **Outcome:** Prices now display correctly as numeric values (`51.77` instead of `Â£51.77`).

## Tools & Environment
- **Editor:** Visual Studio Code (VS Code)
- **Language:** Python
- **Libraries:** bs4, pandas


## Lessons Learned
- Always check **file encoding** when importing CSVs.
- Clean and standardize strings before converting to numbers.
- Encoding mismatches (`UTF-8` vs `Windows-1252`) can cause hidden characters like `Â`.
- Work incrementally — test your cleaning steps before running them on the full dataset.
