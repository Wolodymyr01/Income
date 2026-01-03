# Income Data Wrangling - Proof of Concept

## Overview

This is a **Proof of Concept (PoC)** project demonstrating advanced data wrangling and transformation techniques applied to the UCI Adult dataset. The project showcases practical approaches for handling real-world data challenges including missing values, categorical encoding, feature engineering, and outlier detection.

## Project Objectives

- **Data Transformation**: Convert categorical and ordinal variables into numerical formats
- **Missing Value Imputation**: Implement probabilistic imputation using machine learning models
- **Feature Engineering**: Create meaningful binary and ordinal features
- **Outlier Detection**: Identify and report anomalies in numerical features
- **Data Visualization**: Generate comprehensive visualizations for exploratory data analysis

## Key Features

### 1. Data Transformations
- **Marital Status Binary Variable**: Creates `is_married` (1 = married, 0 = not married) from categorical data
- **Education Ordinal Encoding**: Converts education levels to ordered numeric values preserving educational progression
- **Sex Numerification**: Encodes gender as binary (1 = Male, 0 = Female)

### 2. Missing Value Handling
- **Feature-Based Probabilistic Imputation**: Uses logistic regression trained on non-missing observations to predict immigrant status for records with missing native country information
- **Intelligent Feature Selection**: Considers age, education, hours per week, marital status, and sex for prediction
- **Reproducibility**: Fixed random seed for consistent results

### 3. Outlier Detection & Reporting
- **IQR Method**: Identifies outliers using 1.5 × IQR threshold on numerical features
- **Detailed Statistics**: Reports Q1, Q3, IQR, and outlier bounds for each feature
- **Review Dataset**: Generates annotated dataframe with flagged outlier rows for manual inspection

### 4. Comprehensive Visualization
- **Numerical Features**: Histograms and boxplots for distribution and outlier visualization
- **Ordinal Features**: Ordered bar charts with educational level labels and color gradients
- **Binary Features**: Labeled bar charts with meaningful category names and count annotations
- **Categorical Features**: Top-10 value distribution charts with cardinality notes

## Dataset

**UCI Adult Dataset** (Dua, D. and Graff, C., 2019)
- Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/adult)
- Target: Income prediction (>50K / ≤50K)
- Features: 14 demographic and employment attributes
- Samples: ~32,561 records

## Project Structure

```
.
├── income_data_wrangling.ipynb      # Main analysis notebook
├── README.md                        # This file
└── .github/
    └── workflows/
        └── run_notebook.yml         # GitHub Actions workflow
```

## Notebook Sections

### Cell 1: Data Loading
- Fetches UCI Adult dataset
- Displays metadata and variable information

### Cell 2: Data Transformations
- Applies all feature engineering and encoding transformations
- Reports data shape and new feature statistics

### Cell 3: Missing Values Analysis
- Summarizes missing values per column
- Calculates missing percentages

### Cell 4: Immigrant Status Imputation
- Trains logistic regression on non-missing data
- Applies probabilistic imputation for missing values
- Reports model accuracy and imputation statistics

### Cell 5: Outlier Detection
- Identifies outliers using IQR method
- Generates review dataset for manual inspection
- Provides summary statistics and action items

### Cell 6: Feature Visualization
- Creates publication-quality visualizations
- Handles different feature types appropriately
- Generates PNG diagrams for all features

## Technical Stack

- **Python 3.9+**
- **pandas**: Data manipulation and analysis
- **scikit-learn**: Machine learning (LogisticRegression, StandardScaler)
- **matplotlib & seaborn**: Data visualization
- **ucimlrepo**: Dataset fetching
- **Jupyter**: Interactive analysis

## Installation & Usage

### Local Setup

```bash
# Clone the repository
git clone <repository-url>
cd Income

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the notebook
jupyter notebook income_data_wrangling.ipynb
```

### Running with GitHub Actions

The workflow automatically runs on:
- Push to `main` or `develop` branches
- Pull requests to `main` or `develop`
- Weekly schedule (Sunday midnight)

All outputs are stored as artifacts and can be downloaded from the Actions tab.

## Output Artifacts

The GitHub Actions workflow generates:

1. **Executed Notebook (HTML)**: Interactive HTML version of the notebook with all outputs
2. **Visualization Diagrams (PNG)**: All generated charts and graphs
3. **Console Output**: Data summaries and statistical reports

## Key Insights from PoC

- **Data Quality**: Approximately X% missing values in native-country field
- **Feature Distributions**: Age follows near-normal distribution; education skewed toward higher levels
- **Outliers**: Identified extreme values in hours-per-week
- **Imputation Effectiveness**: Logistic regression model achieved ~X% accuracy on non-missing data

## Future Enhancements

- [ ] Additional feature engineering (interaction terms, polynomial features)
- [ ] Advanced imputation methods (KNN, Multiple Imputation by Chained Equations)
- [ ] Model training pipeline (classification, regression)
- [ ] Cross-validation and model evaluation
- [ ] Feature importance analysis
- [ ] Interactive dashboard with Plotly/Dash

## Notes

- This is a **Proof of Concept** demonstrating data wrangling techniques
- Not optimized for production use
- Results should be validated before business decisions
- Imputation uses probabilistic approach; alternative methods may be explored

## Author

Created as a PoC for demonstrating data transformation and wrangling best practices.

## License

This project uses the UCI Adult dataset. Please refer to the dataset's terms of use.

## References

- Dua, D. and Graff, C. (2019). UCI Machine Learning Repository [http://archive.ics.uci.edu/ml]. Irvine, CA: University of California, School of Information and Computer Science.
- Kohavi, R. (1996). Scaling Up the Accuracy of Naive-Bayes Classifiers: a Decision-Tree Hybrid. Proceedings of the Second International Conference on Knowledge Discovery and Data Mining.
