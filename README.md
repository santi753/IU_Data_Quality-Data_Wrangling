# Data Quality & Data Wrangling: Cafe Sales Dataset

## Project Overview

This project demonstrates advanced data wrangling techniques on a deliberately "dirty" cafe sales dataset. The goal is to transform noisy, untidy, and incomplete data into a clean, analysis-ready format following tidy data principles.

**Course:** Data Quality and Data Wrangling (DLBDSDQDW01)  
**Assignment:** Tidy Up Your Data  
**Dataset:** Augmented Dirty Cafe Sales Data (10,000 transactions)

## Data Quality Issues Addressed

The original dataset contained multiple data quality problems:

- **Missing Values:** 10,731 NaN values across columns
- **Invalid Markers:** 1,678 ERROR markers and 2,018 UNKNOWN markers
- **Unstructured Contact Data:** Mixed email/phone formats with prefixes and suffixes
- **Multiple Date Formats:** 10+ different date/time representations
- **Misspelled Items:** Typos, variations, and inconsistent naming
- **Mixed Currency Formats:** Various symbols, codes, and decimal separators
- **Calculation Errors:** Inconsistent quantity × price calculations

## Cleaning Techniques Applied

1. **Regular Expression Extraction**
   - Parsed unstructured customer contact strings
   - Extracted clean email addresses and phone numbers

2. **Pattern-Based Date Parsing**
   - Handled multiple date formats (ISO, US, European, etc.)
   - Removed prefixes and validated date values

3. **Fuzzy String Matching**
   - Used `difflib.SequenceMatcher` to standardize misspelled item names
   - Mapped variations to standard menu items (60%+ similarity threshold)

4. **Currency Normalization**
   - Removed currency symbols and codes
   - Standardized decimal formats (European comma → period)
   - Extracted numeric values with regex

5. **Imputation Strategies**
   - Mode for categorical variables
   - Median for quantities
   - Mean for tip amounts
   - Item-specific medians for prices

## Results

- **Before:** 14,427 total data quality issues
- **After:** 0 issues (100% improvement)
- **Completeness:** All core columns improved to 100%
- **Final Dataset:** 10,000 rows × 20 columns (8 original + 12 derived features)

## Repository Structure

```
├── augmented_dirty_cafe_sales.xlxs         # Dataset
├── notebook_data_quality.ipynb             # Main analysis notebook
├── clean_cafe_sales.csv                    # Cleaned output dataset
└── README.md                               # This file
```

## Key Technologies

- Python 3.x
- pandas, numpy
- Regular expressions (re module)
- difflib (fuzzy matching)
- matplotlib, seaborn (visualization)

## How to Run

1. Clone this repository
2. Install required packages: `pip install pandas numpy matplotlib seaborn`
3. Open and run `notebook_data_quality.ipynb` in Jupyter
