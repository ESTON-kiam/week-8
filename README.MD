# COVID-19 Dataset Analysis

## Overview

This project analyzes the COVID-19 dataset from Our World in Data (OWID), providing comprehensive insights into the global pandemic trends, vaccination rates, and health statistics across different countries and time periods.

## Dataset Information

- **Source**: Our World in Data COVID-19 Dataset
- **File**: `owid-covid-data.csv`
- **Format**: CSV (Comma Separated Values)
- **Update Frequency**: Daily updates from OWID

### Key Features

The dataset includes various metrics such as:
- Daily confirmed cases and deaths
- Testing data
- Vaccination statistics
- Hospital and ICU admissions
- Population demographics
- Government response measures
- Economic indicators

## Project Structure

```
covid19-analysis/
│
├── data/
│   └── owid-covid-data.csv
├── notebooks/
│   └── covid_analysis.ipynb
├── src/
│   └── analysis.py
└── README.md
```

## Requirements

### Dependencies

```python
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
plotly>=5.0.0
jupyter>=1.0.0
```

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/covid19-analysis.git
cd covid19-analysis
```

2. Install required packages:
```bash
pip install pandas numpy matplotlib seaborn plotly jupyter
```

3. Download the dataset from Kaggle or OWID website and place it in the appropriate directory.

## Usage

### Basic Data Exploration

```python
import pandas as pd

# Load the dataset
data_path = "/kaggle/input/covid19-dataset/owid-covid-data.csv"
df = pd.read_csv(data_path)

# Basic information about the dataset
print("Prime righe del dataset (df.head()):")
print(df.head())

print("\nShape del dataset:", df.shape)

print("\nStatistiche descrittive del dataset:")
print(df.describe())

print("\nVerifica valori nulli:")
print(df.isnull().sum())
```

### Key Analysis Functions

#### 1. Dataset Overview
- **Shape Analysis**: Understand the dimensions of your data
- **Data Types**: Check column types and memory usage
- **Missing Values**: Identify and handle null values
- **Statistical Summary**: Basic descriptive statistics

#### 2. Data Quality Assessment
```python
# Check for duplicate rows
duplicates = df.duplicated().sum()
print(f"Duplicate rows: {duplicates}")

# Check unique countries
unique_countries = df['location'].nunique()
print(f"Number of unique countries/regions: {unique_countries}")

# Date range analysis
if 'date' in df.columns:
    df['date'] = pd.to_datetime(df['date'])
    print(f"Date range: {df['date'].min()} to {df['date'].max()}")
```

## Key Columns Description

| Column | Description |
|--------|-------------|
| `iso_code` | ISO 3166-1 alpha-3 country codes |
| `continent` | Continent name |
| `location` | Country or region name |
| `date` | Date of observation |
| `total_cases` | Total confirmed cases |
| `new_cases` | New confirmed cases |
| `total_deaths` | Total confirmed deaths |
| `new_deaths` | New confirmed deaths |
| `total_vaccinations` | Total vaccine doses administered |
| `people_vaccinated` | Number of people vaccinated (at least 1 dose) |
| `population` | Population size |

## Analysis Capabilities

### 1. Temporal Analysis
- Track case trends over time
- Identify waves and peaks
- Seasonal pattern analysis

### 2. Geographic Analysis
- Country-wise comparisons
- Continental trends
- Population-adjusted metrics

### 3. Vaccination Analysis
- Vaccination rollout progress
- Vaccine effectiveness correlation
- Coverage by demographics

### 4. Mortality Analysis
- Case fatality rates
- Excess mortality calculations
- Age-adjusted death rates

## Sample Insights

The initial data exploration reveals:
- Dataset dimensions and structure
- Missing value patterns
- Statistical distributions of key metrics
- Data quality indicators

## Data Preprocessing Steps

1. **Date Parsing**: Convert date strings to datetime objects
2. **Missing Value Handling**: Strategy for null values
3. **Data Type Optimization**: Efficient memory usage
4. **Outlier Detection**: Identify anomalous data points
5. **Feature Engineering**: Create derived metrics

## Visualization Examples

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Set style
plt.style.use('seaborn-v0_8')
sns.set_palette("husl")

# Example: Cases over time for top countries
top_countries = ['United States', 'India', 'Brazil', 'Russia', 'France']
country_data = df[df['location'].isin(top_countries)]

plt.figure(figsize=(12, 6))
for country in top_countries:
    country_subset = country_data[country_data['location'] == country]
    plt.plot(country_subset['date'], country_subset['total_cases'], 
             label=country, linewidth=2)

plt.title('COVID-19 Total Cases Over Time - Top 5 Countries')
plt.xlabel('Date')
plt.ylabel('Total Cases')
plt.legend()
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/analysis-improvement`)
3. Commit your changes (`git commit -am 'Add new analysis feature'`)
4. Push to the branch (`git push origin feature/analysis-improvement`)
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Data Attribution

The dataset is provided by Our World in Data and is available under the Creative Commons BY license. Please cite appropriately:

```
Mathieu, E., Ritchie, H., Ortiz-Ospina, E. et al. A global database of COVID-19 vaccinations. Nat Hum Behav (2021). https://doi.org/10.1038/s41562-021-01122-8
```


## Changelog

### Version 1.0.0
- Initial dataset exploration
- Basic statistical analysis
- Data quality assessment
- README documentation

---

**Note**: This analysis is for educational and research purposes. Always refer to official health organizations for the most current COVID-19 information and guidance.