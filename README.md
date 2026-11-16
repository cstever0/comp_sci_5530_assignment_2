# Assignment 2 — Data Preprocessing and Statistical Analysis

## Project Overview

This project completes Assignment 2 using Python and Jupyter notebooks. It demonstrates data cleaning, feature engineering, data manipulation, random sampling, descriptive statistics, and bootstrap analysis.

Two datasets are analyzed:

- **Used Cars Dataset (`train.csv`):** Used to demonstrate data preprocessing, categorical encoding, feature engineering, and data manipulation.
- **Diabetes Dataset (`diabetes.csv`):** Used to investigate sampling variability and compare sample statistics with population statistics through visualization and bootstrap resampling.

All Python source code is contained in Jupyter notebooks (`.ipynb`).

## Project Structure

```text
Assignment_2_Project/
├── data_raw/
│   ├── train.csv
│   ├── diabetes.csv
│   └── README.txt
├── data_clean/
│   └── used_cars_cleaned.csv
├── results/
│   ├── glucose_comparison.csv
│   ├── bmi_comparison.csv
│   ├── blood_pressure_bootstrap_statistics.csv
│   └── blood_pressure_bootstrap_comparison.csv
├── src/
│   ├── 01_used_cars.ipynb
│   └── 02_diabetes_sampling_bootstrap.ipynb
└── README.md
```

## Requirements

- Python 3.10 or later
- NumPy
- pandas
- Matplotlib
- IPython
- ipykernel
- JupyterLab

### Installation

Create and activate a virtual environment.

**macOS, Linux, or WSL:**

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install numpy pandas matplotlib ipython ipykernel jupyterlab
```

**Windows PowerShell:**

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install numpy pandas matplotlib ipython ipykernel jupyterlab
```

Launch JupyterLab:

```bash
python -m jupyter lab
```

Open the notebooks in `src/` and select **Run All**.

The notebooks support execution from either the project root directory or the `src/` directory. Running them regenerates the processed dataset and statistical results.

## Question 1 — Used Cars Data Preprocessing

**Notebook:** `src/01_used_cars.ipynb`

The used-car dataset contains 5,847 observations.

### Tasks Completed

**(a) Missing Values**

- Inspected missing values across all columns.
- Applied median imputation to selected numerical attributes.
- Created `New_Price_Missing` to identify originally missing new-car prices.
- Preserved the original used-car price target.

**(b) Numerical Conversion**

- Removed text-based measurement units from `Mileage`, `Engine`, and `Power`.
- Standardized `New_Price` values to lakhs.
- Retained `Mileage_Unit` to distinguish kilometers per liter from kilometers per kilogram.

**(c) Categorical Encoding**

- Applied one-hot encoding to `Fuel_Type` and `Transmission`.
- Validated the resulting binary indicator columns.

**(d) Feature Engineering**

- Created `Car_Age` using the vehicle's manufacturing year and the current calendar year.

**(e) Data Manipulation**

Demonstrated the following pandas operations:

- Select
- Filter
- Rename
- Mutate
- Arrange
- Group By and Summarize

### Output

`data_clean/used_cars_cleaned.csv`

## Question 2 — Diabetes Statistical Analysis

**Notebook:** `src/02_diabetes_sampling_bootstrap.ipynb`

The diabetes dataset contains 768 patient observations, treated as the complete population for this assignment.

### (a) Random Sampling and Glucose Analysis

- Initialized a random number generator with seed `42`.
- Selected 25 observations without replacement.
- Calculated sample and population glucose means and maximum values.
- Compared the statistics using tables and charts.

### (b) BMI Percentile Analysis

- Calculated the 98th percentile of body mass index (BMI) for the sample.
- Calculated the corresponding population percentile.
- Visualized and interpreted the difference.

### (c) Blood Pressure Bootstrap Analysis

- Generated 500 bootstrap samples containing 150 observations each.
- Sampled with replacement.
- Calculated the mean, standard deviation, and 98th percentile for every sample.
- Averaged the 500 bootstrap statistics and compared them with population statistics.
- Created bootstrap distribution histograms and comparison charts.
- Documented the observed findings and data quality limitations.

The 98th percentile was selected for the bootstrap analysis to maintain consistency with Question 2(b), because Question 2(c) does not specify a percentile.

## Bootstrap Results

| Statistic | Population | Average Bootstrap | Difference |
|---|---:|---:|---:|
| Mean | 69.105 | 69.136 | +0.031 |
| Standard Deviation | 19.343 | 19.059 | -0.284 |
| 98th Percentile | 99.320 | 97.656 | -1.664 |

The bootstrap mean closely approximated the population mean. The standard deviation was slightly lower, while the 98th percentile demonstrated the largest absolute difference in the observed comparison.

These results describe the particular bootstrap simulation and should not be interpreted as evidence of statistical significance or causation.

## Data Quality and Limitations

**Used Cars Dataset**

The `New_Price` attribute contains substantial missing data. Median imputation was applied to preserve records, but the resulting values should not be interpreted as reliable original vehicle prices.

Mileage measurements originally expressed in `kmpl` and `km/kg` remain distinguishable through the `Mileage_Unit` column.

**Diabetes Dataset**

The population contains 35 observations with `BloodPressure` equal to zero. These observations were retained to preserve the supplied population, although they may represent missing or invalid clinical measurements.

The statistical findings should be interpreted with this limitation in mind.

## Reproducibility

The diabetes notebook initializes a NumPy random number generator using seed `42`. Running the notebook sequentially from beginning to end reproduces the same random samples and bootstrap analysis.

Processed datasets are stored in `data_clean/`, and statistical comparison tables are exported to `results/`.

Generated charts and accompanying interpretations are included directly in the Jupyter notebooks.

## Conclusion

Assignment 2 demonstrates the application of Python-based data preprocessing and statistical analysis to two distinct datasets.

The used-car analysis emphasizes data cleaning, numerical conversion, feature engineering, and structured data manipulation. The diabetes analysis demonstrates random sampling, population comparisons, bootstrap estimation, and statistical visualization.

Together, the notebooks provide a reproducible workflow for preparing datasets and interpreting descriptive statistical results.
