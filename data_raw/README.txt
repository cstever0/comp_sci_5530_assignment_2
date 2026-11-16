1. USED-CAR LISTINGS DATASET: train.csv
======================================

Purpose
-------
Explore and clean used-car listings. The response (target) variable is
Price, representing the listed used-car price in Indian lakhs.

Dataset size
------------
  Records (rows):             5,847
  Original columns:             14
  Data format:                 CSV (comma-separated values)
  Unit of used-car Price:      lakh (100,000 Indian rupees)

Column reference
----------------
  Unnamed: 0           Existing row/index identifier; not a car feature
  Name                 Vehicle make, model, and variant
  Location             City where the car is listed
  Year                 Year of manufacture
  Kilometers_Driven    Odometer reading in kilometers
  Fuel_Type            Fuel category (Diesel, Petrol, or Electric)
  Transmission         Transmission category (Manual or Automatic)
  Owner_Type           Previous ownership category (First, Second,
                       Third, or Fourth & Above)
  Mileage              Fuel-economy value stored as text with units,
                       including kmpl or km/kg
  Engine               Engine displacement, usually expressed in CC
  Power                Engine power, usually expressed in bhp
  Seats                Number of seats
  New_Price            New-vehicle price, stored as text with units
                       such as Lakh or Cr (crore); often unavailable
  Price                Used-vehicle listing price, in lakhs; target

Missing-value summary (original file)
-------------------------------------
  Mileage                         2
  Engine                         36
  Power                          36
  Seats                          38
  New_Price                   5,032 (86.1% of listings)
  All other columns               0

Important data considerations
-----------------------------
* Mileage, Engine, Power, and New_Price are not purely numeric in the
  original file; units must be parsed before numerical analysis.
* Fuel economy appears in both kmpl and km/kg. These are different
  measurement conventions and should not automatically be equated.
* One crore equals 100 lakhs; price conversion must respect this.
* New_Price has extensive missing data. If imputed, results should be
  interpreted cautiously and original missingness should be flagged.
* Price is the used-car target and should remain unchanged during
  cleaning so it can be compared with the raw values.

Use in the assignment
---------------------
The notebook src/01_used_cars.ipynb performs missing-value treatment,
unit removal, one-hot encoding, car-age feature creation, and the
select/filter/rename/mutate/arrange/group-and-summarize operations.
Its processed dataset is exported to data_clean/used_cars_cleaned.csv.


2. DIABETES DATASET: diabetes.csv
================================

Purpose
-------
Practice random sampling, comparison with a defined population, and
bootstrap resampling using patient measurements. The assignment treats
all 768 records in this file as the COMPLETE POPULATION for analysis.

Dataset size
------------
  Records (rows):               768
  Original columns:               9
  Predictor attributes:           8
  Outcome attributes:             1
  Data format:                 CSV (comma-separated values)

Column reference
----------------
  Pregnancies                Number of pregnancies
  Glucose                    Glucose measurement
  BloodPressure              Blood pressure measurement
  SkinThickness              Skinfold thickness measurement
  Insulin                    Insulin measurement
  BMI                        Body mass index (kg/m^2)
  DiabetesPedigreeFunction   Diabetes pedigree score
  Age                        Age in years
  Outcome                    Binary diabetes outcome:
                             1 = diabetes; 0 = no diabetes

Data completeness and possible placeholders
-------------------------------------------
The original file has NO explicit missing (NaN) values in any column.
However, some clinical measurement fields contain zero values:

  Glucose                         5 zeros
  BloodPressure                  35 zeros
  SkinThickness                 227 zeros
  Insulin                       374 zeros
  BMI                            11 zeros

Zero measurements may reflect unavailable clinical readings, rather
than meaningful observations. The assignment's statistical notebook
retains these original values to analyze the supplied population, and
reports this limitation instead of silently modifying the data.

Use in the assignment
---------------------
The notebook src/02_diabetes_sampling_bootstrap.ipynb performs:
  A. Reproducible simple random sampling of 25 records without
     replacement; comparison of mean and maximum Glucose values.
  B. Comparison of the sample and population 98th percentiles of BMI.
  C. 500 bootstrap samples, each containing 150 observations drawn
     WITH replacement; comparison of BloodPressure mean, standard
     deviation, and 98th percentile against population values.

Tables from this analysis are written to the results/ folder.


3. REPRODUCIBILITY AND FILE HANDLING
===================================

* Keep train.csv and diabetes.csv unchanged in data_raw/.
* Execute notebooks from the project root or src/ directory; the
  notebooks locate the data_raw/ folder relative to the project.
* The notebooks use a fixed random seed (42) for reproducibility.
* Processed files belong in data_clean/; analysis tables in results/.
* Only the .ipynb files in src/ contain assignment Python source code.
* Do not place the local .venv/ environment under version control.
