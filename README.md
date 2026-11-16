# Assignment 2 — Jupyter Notebook Submission

## Folder layout

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
└── src/
    ├── 01_used_cars.ipynb
    └── 02_diabetes_sampling_bootstrap.ipynb
```

## Run

Install Python 3.10 or later and the required packages.

macOS, Linux, or Windows Subsystem for Linux:

```bash
python3 -m pip install numpy pandas matplotlib ipython ipykernel jupyterlab
python3 -m jupyter lab
```

Windows PowerShell:

```powershell
py -m pip install numpy pandas matplotlib ipython ipykernel jupyterlab
py -m jupyter lab
```

Open the two notebooks in `src/` and select **Run All**. Run them either with the project root or the `src/` folder as working directory. Both notebooks have already been run successfully and contain saved chart outputs. Re-running regenerates `data_clean/` and `results/` files.

## Coverage

**Question 1:** missing-value audit and documented treatment; remove measurement units; one-hot encode `Fuel_Type` and `Transmission`; engineer car age; demonstrate select, filter, rename, mutate, arrange, and group-by summarize operations. The cleaned used-car dataset is in `data_clean/`.

**Question 2:** seed 42; random sample of 25; sample and population Glucose means/maxima; BMI 98th percentiles; 500 BloodPressure bootstrap samples of 150 observations with replacement, with comparisons of means, standard deviations and percentiles. Charts and observations are embedded in the notebook; tables are in `results/`.
