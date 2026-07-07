# Animal Shelter Stay Analysis

Exploratory data analysis of the Austin Animal Center dataset to understand factors influencing length of stay before adoption or other outcomes.

## Motivation

Animal shelters face high intake volumes with limited resources. Understanding which factors influence how long animals stay in the shelter can help optimize operations and improve adoption rates. This project analyzes 87,000+ animal records from Austin's animal center over multiple years.

## Dataset

The [Austin Animal Center dataset](https://www.kaggle.com/datasets/thedevastator/austin-animal-center-data) contains:

- **Intakes**: Animals entering the shelter (87,192 records)
- **Outcomes**: Animals leaving the shelter (87,091 records)
- Variables include intake type, condition, breed, age, color, outcome type

Due to the extremely high adoption rate (~99%), predictive modeling for *whether* an animal is adopted was deemed inappropriate. Instead, this project focuses on:

1. **Duration of stay** (time in shelter)
2. **Factors affecting outcome type**
3. **Pattern recognition in shelter operations**

## Project Structure

animal-shelter-stay-analysis/ ├── archive/ # Raw dataset files (not tracked) ├── .gitignore └── notebooks/ (conceptually, all notebooks at root) ├── 01_data_preparation.ipynb └── 02_exploratory_analysis.ipynb


## Methodology

### Data Preparation (01_data_preparation.ipynb)

- **Date/time parsing**: Convert string timestamps to datetime objects
- **Age standardization**: Parse age strings (e.g., "2 years", "11 months") into numeric months
- **Duplicate removal**: Identify and deduplicate ~16 duplicate entries
- **Multi-intake handling**: Some animals enter the shelter repeatedly; track event sequence per animal ID
- **Outcome linkage**: Merge intake and outcome data by animal ID and event order
- **Duration calculation**: Compute time difference between entry and exit; handle edge cases (same-day returns, negative values as NaT)
- **Feature engineering**: Separate sex/status fields, extract month/year from date strings

### Exploratory Analysis (02_exploratory_analysis.ipynb)

- **Univariate distributions**: Histograms/KDE plots for numerical variables
- **Categorical breakdowns**: Barplots for outcome types by intake condition, sex, etc.
- **Correlation heatmap**: Relationships between numerical features
- **Target analysis**: Distribution of adoption outcomes by category
- **Stay duration visualization**: Density plots showing typical shelter durations

## Key Findings

- **High adoption rate**: Majority of dogs are adopted rather than euthanized
- **Intake condition**: Animals in "Normal" condition move through faster than those marked "Injured" or "Sick"
- **Breed diversity**: Over 2,500 unique breed combinations identified
- **Seasonal patterns**: Clear monthly/yearly trends in intake volume
- **Duration outliers**: A small subset stays significantly longer (>1 year)

## Tech Stack

- **Python 3.x**
- **pandas** — data manipulation
- **numpy** — numerical operations
- **matplotlib / seaborn** — visualization
- **Jupyter** — interactive analysis

## Reproduction

```bash
## 1. Clone repository
git clone https://github.com/KKulmus/animal-shelter-stay-analysis.git
cd animal-shelter-stay-analysis

## 2. Download dataset from Kaggle
## Place intakes.csv and outcomes.csv in archive/

## 3. Run notebooks sequentially
jupyter notebook
## First execute: 01_data_preparation.ipynb
## Then execute: 02_exploratory_analysis.ipynb

## Author

Dr. Kathrin Kulmus

    PhD in Theoretical Physics
    Data Scientist (StackFuel certified)
    GitHub: @KKulmus


