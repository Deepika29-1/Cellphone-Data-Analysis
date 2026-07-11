# Cellphone-Data-Analysis

A statistical exploration of smartphone specifications, pricing, and buyer demographics — built with Python (Jupyter Notebook) for analysis and Tableau for interactive visualization.

## Project Overview

This project analyzes a dataset of 990 smartphone purchase/review records to uncover relationships between device specifications (RAM, camera, battery, performance), pricing, and buyer demographics (age, gender, occupation, salary, region). It combines exploratory data analysis, data quality checks, and formal hypothesis testing to answer questions such as:

- Do device prices differ meaningfully across brands, occupations, or operating systems?
- Are modern smartphone specs (RAM, camera, battery) significantly above older baseline expectations?
- Is there an association between brand, operating system, gender, and occupation?
- How does income relate to the devices people buy?

## Repository Contents

| File | Description |
|---|---|
| `CELLPHONE_DATA_ANALYSIS_.ipynb` | Main Jupyter Notebook containing the full analysis workflow |
| `cellphone_data.csv` | Source dataset (990 rows × 22 columns) |
| `CELLPHONE_DATA_ANALYSIS.twbx` | Tableau packaged workbook with interactive dashboards |
| `README.md` | This file |

## Dataset

**File:** `cellphone_data.csv` — 990 records, 22 columns

| Column | Description |
|---|---|
| `user_id`, `cellphone_id` | Identifiers |
| `rating` | User rating for the device |
| `brand`, `model` | Device brand and model name |
| `operating system` | Android / iOS |
| `internal memory`, `RAM` | Storage and memory (GB) |
| `performance` | Performance score |
| `main camera`, `selfie camera` | Camera resolution (MP) |
| `battery size` | Battery capacity (mAh) |
| `screen size` | Screen size (inches) |
| `weight` | Device weight (g) |
| `price(INR)` | Device price in ₹ |
| `release date` | Device release date |
| `user_name` | Reviewer name |
| `Region(City)` | Reviewer's city (8 unique cities) |
| `Salary_in_INR` | Reviewer's salary |
| `age`, `gender`, `occupation` | Reviewer demographics (46 unique occupations) |

**Brands covered:** Samsung, Apple, Xiaomi, Motorola, OnePlus, Google, Oppo, Asus, Sony, Vivo

## Notebook Workflow

The notebook (`CELLPHONE_DATA_ANALYSIS_.ipynb`) is organized into six steps:

### Step 1 — Libraries & Setup
Imports `pandas`, `numpy`, `matplotlib`, `seaborn`, and `scipy.stats`; configures plotting theme.

### Step 2 — Load Dataset
Reads `cellphone_data.csv` and previews shape and first rows.

### Step 3 — Data Preprocessing
- **3.1** Data types & statistical summary
- **3.2** Missing value check (none found — dataset is complete)
- **3.3** Duplicate row check (no full duplicates)
- **3.4** Verification of numerical vs. categorical columns
- **3.5** Outlier detection using the IQR method

### Step 4 — Data Exploration and Visualization
- **4.1** Splitting variables into numerical/categorical groups
- **4.2** Boxplots for all numerical variables (outlier inspection)
- **4.3** Correlation heatmap (price shows strong positive correlation with performance, RAM, camera, and memory)
- **4.4** Count plots for categorical variable distributions (Android 83% vs. iOS 17%; Samsung leads brand share)
- **4.5** Pair plots of key numerical variables, colored by operating system

### Step 5 — Statistical Analysis
**5.1 Hypothesis Testing (T-Tests)**
- Salary difference: Male vs. Female
- One-sample tests: mean RAM > 4GB, main camera > 12MP, selfie camera > 8MP, battery > 4000mAh
- Price difference: Android vs. iOS
- Salary difference: Delhi vs. Mumbai

**5.2 ANOVA Tests**
- Price across brands
- Price across occupations
- Performance rating across age groups (<30, 30–50, >50)
- Battery size across brands
- Screen size across operating systems
- RAM across operating systems
- Main camera resolution across brands

**5.3 Chi-Square Tests**
- OS choice vs. gender
- Brand choice vs. OS
- Brand choice vs. occupation

### Step 6 — Summary of Findings

| Category | Key Finding |
|---|---|
| Missing Values | None — dataset is complete |
| Duplicates | No duplicate rows found |
| Data Types | All types correct; `release date` should be converted to datetime; `occupation` needs casing standardization |
| Outliers | Found in price, RAM, internal memory, main camera, and salary columns — flagged for later treatment |
| Correlations | Strong: price ↔ performance ↔ RAM; Weak: salary ↔ device specs |
| OS Distribution | Android 83% vs. iOS 17% |
| Brand Distribution | Samsung leads; Apple second |
| T-Tests | RAM, main camera, and selfie camera significantly exceed their baseline thresholds |
| ANOVA | Price, battery, and camera specs differ significantly across brands |
| Chi-Square | Brand and OS are structurally associated; gender–OS link to be verified |

## Tableau Dashboard

`CELLPHONE_DATA_ANALYSIS.twbx` is a packaged Tableau workbook that visualizes the same dataset interactively — useful for filtering by brand, region, or demographic segment and exploring pricing/spec trends visually. Open it with [Tableau Desktop](https://www.tableau.com/products/desktop) or [Tableau Reader](https://www.tableau.com/products/reader) (free).

## How to Run

### Notebook
1. Ensure Python 3 is installed with the following packages:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```
2. Place `cellphone_data.csv` in the same directory as the notebook.
3. Launch Jupyter and run all cells:
   ```bash
   jupyter notebook CELLPHONE_DATA_ANALYSIS_.ipynb
   ```

### Tableau Workbook
1. Install Tableau Desktop or Tableau Reader.
2. Open `CELLPHONE_DATA_ANALYSIS.twbx` directly — it's a self-contained packaged workbook with the data embedded.

## Key Insights

- **Price is driven by specs:** performance, RAM, camera quality, and storage are the strongest positive predictors of device price.
- **Android dominates volume** (83% of the sample) while **iOS commands a price premium**.
- **Samsung is the most represented brand**, followed by Apple, Xiaomi, and Motorola.
- Modern devices in this dataset **significantly exceed older baseline specs** (RAM > 4GB, camera > 12MP, battery > 4000mAh).
- **Brand and OS are structurally linked** (Apple = iOS only), while **income and occupation show weaker but still measurable influence** on brand/price choices.
