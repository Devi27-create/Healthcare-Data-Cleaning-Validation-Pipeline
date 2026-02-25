# Healthcare Data Cleaning & Validation Pipeline

A production-style healthcare data preprocessing pipeline designed to clean, validate, standardize, and transform a messy synthetic dataset of 150,000+ patient records into a clean, ML-ready dataset.

This project demonstrates real-world data engineering practices including schema validation, profiling, rule enforcement, outlier handling, feature engineering, and final quality validation.

## Project Overview

Raw healthcare datasets are often:

- Inconsistent

- Contain missing values

- Have mixed data types

- Include outliers

- Contain duplicate records

- Have inconsistent categorical formats

- Contain invalid date logic

This project builds a structured, multi-phase cleaning architecture to transform messy healthcare data into trusted analytical data.

## Architecture

Healthcare Data Cleaning Architecture

![Diagram](https://github.com/Devi27-create/Healthcare-Data-Cleaning-Validation-Pipeline/blob/main/Healthcare%20Architecture.drawio.png)


## Pipeline Flow

Data Ingestion
      ⬇️
Schema Validation
      ⬇️
Data Profiling
      ⬇️
Validation Rules
      ⬇️
Data Cleaning
      ⬇️
Outlier Handling
      ⬇️
Feature Engineering
      ⬇️
Final Data Validation
      ⬇️
Analytics & ML Ready Dataset


## Dataset Description

Synthetic dataset with 150,000+ patient records including:

- Patient_ID

- Age

- Gender

- Height_cm

- Weight_kg

- BMI

- Blood_Pressure

- Heart_Rate

- Cholesterol

- Diabetes

- Smoking_Status

- Admission_Date

- Discharge_Date

- Hospital

- Billing_Amount

The dataset intentionally contains:

- Null values

- Mixed formats

- Duplicates

- Outliers

- Inconsistent categorical labels

- Mixed date formats

- Invalid medical ranges


## Pipeline Stages

**1️⃣ Schema Validation**

- Ensures structural correctness before processing.

- Required columns check

- Data type enforcement

- Column naming standardization

**2️⃣ Data Profiling**

- Understands dataset structure and anomalies.

- Null analysis

- Distribution analysis

- Duplicate detection

**3️⃣ Validation Rules**

Applies business logic rules.

- Age range validation (0–120)

- Height range validation (100–250 cm)

- Weight validation (30–300 kg)

- Heart rate validation (30–220 bpm)

- Cholesterol validation (100–400 mg/dL)

- Systolic BP validation (70-250)

- Diastolic BP validation (40-150)

- Date logic validation (Discharge ≥ Admission)

- Category mapping consistency


**4️⃣ Data Cleaning**

- Corrects detected issues.

- Missing value treatment (Median for numeric, Mode for categorical)

- Standardize categorical fields

- Parse mixed date formats

- Strip whitespace

- Remove duplicates


**5️⃣ Outlier Handling**

- Uses IQR-based filtering for financial outliers.

- Billing amount IQR filtering
  

**6️⃣ Feature Engineering**

- Derives reliable medical metrics.

- Recalculated BMI from height & weight

- Split Blood Pressure into Systolic/Diastolic


**7️⃣ Final Data Validation**

- Ensures data integrity before downstream usage.

- No impossible medical values

- Temporal consistency validation

- No duplicate Patient_ID

- Schema consistency

## Key Data Engineering Concepts Demonstrated

- Data lifecycle design

- Schema enforcement

- Data profiling techniques

- Business rule validation

- Handling mixed data types

- Outlier detection using IQR

- Feature engineering best practices

- Final quality gating

- Clean ML-ready dataset preparation


## Missing Value Strategy

| Data Type                              | Strategy                           |
| -------------------------------------- | ---------------------------------- |
| Numeric (Age, Heart_Rate, Cholesterol) | Median                             |
| Categorical (Gender, Diabetes)         | Mode                               |
| Out-of-range values                    | Converted to NaN before imputation |


## Technologies Used

- Python

- Pandas

- NumPy

## Skills Demonstrated

- Data Profiling

- ETL Pipeline Design

- Data Quality Validation

- Healthcare Domain Validation Rules

- Outlier Detection (IQR)

- Feature Engineering

- Defensive Pandas Programming

- Mixed Date Format Handling

- Chained Assignment Handling

- Schema Consistency Debugging

## Project Structure

healthcare-data-cleaning/
│
├── messy_healthcare_dataset_150k.csv
├── data_cleaning_pipeline.py
├── README.md
└── architecture.png

**Dataset**

Input File

[Healthcare_Dataset.csv](https://github.com/Devi27-create/Healthcare-Data-Cleaning-Validation-Pipeline/blob/main/Healthcare_Dataset.csv)

**How to Run**

`pip install pandas`

`pip install numpy`

`import pandas as pd`

`df = pd.read_csv("messy_healthcare_dataset_150k.csv")`

Run the cleaning pipeline script to generate the cleaned dataset.

## Output

Final dataset characteristics:

- Cleaned & standardized

- Validated medical ranges

- Outliers removed

- No duplicate patients

- Proper date consistency

- ML-ready format


## Future Improvements

- Automated Data Quality Score

- Validation Rule Engine

- Logging & Exception Handling

- Sklearn-style preprocessing pipeline

- Unit tests for validation logic

- CI/CD integration

- Performance optimization for 1M+ rows


## Real-World Application

This workflow mirrors cleaning processes used in:

- Electronic Health Record (EHR) systems

- Healthcare analytics platforms

- Insurance fraud detection systems

- Clinical risk prediction models

- Healthcare BI dashboards

## Author

Healthcare Data Cleaning Project
Built for mastering real-world messy data handling.
