🏥 Healthcare Data Cleaning & Validation Pipeline

Production-style healthcare data audit and cleaning workflow built using Python and pandas.

📌 Project Overview

This project demonstrates a real-world healthcare data cleaning pipeline applied to a messy synthetic dataset containing 150,000+ patient records.

The dataset intentionally includes:

Missing values (NaN, None, empty strings)

Inconsistent categorical labels

Mixed data types

Out-of-range medical values

Duplicate patient records

Mixed date formats

Whitespace issues

Invalid blood pressure formats

Extreme billing outliers

The objective is to simulate a production-level ETL (Extract, Transform, Load) data preparation workflow used in:

Hospital EHR systems

Insurance analytics

Healthcare BI platforms

Clinical ML pipelines

📂 Dataset

Input File

messy_healthcare_dataset_150k.csv


Columns

Column	Description
Patient_ID	Unique patient identifier
Age	Patient age
Gender	Gender category
Height_cm	Height in centimeters
Weight_kg	Weight in kilograms
BMI	Provided BMI
Blood_Pressure	Systolic/Diastolic format
Heart_Rate	Beats per minute
Cholesterol	mg/dL
Diabetes	Yes/No indicator
Smoking_Status	Smoking category
Admission_Date	Hospital admission date
Discharge_Date	Discharge date
Hospital	Hospital name
Billing_Amount	Total billing
🏗️ Project Architecture
🔷 High-Level Data Flow
                ┌──────────────────────────┐
                │  Raw Healthcare Dataset  │
                │ (150K+ messy records)    │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Phase 1: Data Audit     │
                │  - Null detection        │
                │  - Type validation       │
                │  - Range checks          │
                │  - Date inspection       │
                │  - Categorical preview   │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Phase 2: Cleaning       │
                │  - Standardize nulls     │
                │  - Remove duplicates     │
                │  - Fix data types        │
                │  - Normalize categories  │
                │  - Validate medical data │
                │  - Parse dates           │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Feature Engineering     │
                │  - Recalculate BMI       │
                │  - Extract BP metrics    │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Outlier Handling        │
                │  - IQR on billing        │
                └──────────────┬───────────┘
                               │
                               ▼
                ┌──────────────────────────┐
                │  Clean, ML-Ready Dataset │
                └──────────────────────────┘

🧹 Data Cleaning Pipeline
🔍 Phase 1 — Data Audit

Performed comprehensive validation:

Null counts & percentages

Empty string detection

Whitespace validation

Mixed dtype inspection

Non-numeric detection

Categorical variation analysis

Date format validation

Duplicate detection

Out-of-range medical values

Custom data_audit() function generates structured dataset diagnostics.

🧽 Phase 2 — Cleaning & Standardization
1️⃣ Standardize Missing Values

Replaced invalid placeholders:

"", "unknown", "invalid", "N/A"


→ Converted to NaN

2️⃣ Remove Duplicate Patients
drop_duplicates(subset="Patient_ID")

3️⃣ Normalize String Columns

Trim whitespace

Convert to lowercase

Standardize categorical labels

4️⃣ Fix Data Types

Safe numeric conversion using:

pd.to_numeric(errors="coerce")

5️⃣ Medical Range Validation
Field	Valid Range
Age	0–120
Height	100–250 cm
Weight	30–300 kg
Heart Rate	30–220 bpm
Cholesterol	100–400 mg/dL
Systolic BP	70–250
Diastolic BP	40–150

Invalid values → converted to NaN

6️⃣ Date Parsing & Logical Validation

Mixed format handling

Invalid date coercion

Ensured Discharge ≥ Admission

7️⃣ Feature Engineering

Recalculated BMI from height & weight

Split Blood Pressure into Systolic/Diastolic

8️⃣ Missing Value Imputation
Type	Strategy
Numeric	Median
Categorical	Mode
9️⃣ Outlier Handling (IQR Method)

Applied IQR filtering to:

Billing_Amount


Removed extreme financial outliers.

📊 Final Dataset Quality Checks

df.describe()

df.info()

Null validation

Shape verification

Statistical distribution inspection

🧠 Technical Stack

Python 3.x

pandas

NumPy

💼 Skills Demonstrated

Data Profiling

ETL Pipeline Design

Data Quality Validation

Healthcare Domain Validation Rules

Outlier Detection (IQR)

Feature Engineering

Defensive Pandas Programming

Mixed Date Format Handling

Chained Assignment Handling

Schema Consistency Debugging

📁 Recommended Repository Structure
healthcare-data-cleaning/
│
├── data/
│   └── messy_healthcare_dataset_150k.csv
│
├── notebooks/
│   └── healthcare_cleaning.ipynb
│
├── src/
│   └── cleaning_pipeline.py
│
├── README.md
└── requirements.txt

🚀 Future Improvements

Automated Data Quality Score

Validation Rule Engine

Logging & Exception Handling

Sklearn-style preprocessing pipeline

Unit tests for validation logic

CI/CD integration

Performance optimization for 1M+ rows

🏥 Real-World Application

This workflow mirrors cleaning processes used in:

Electronic Health Record (EHR) systems

Healthcare analytics platforms

Insurance fraud detection systems

Clinical risk prediction models

Healthcare BI dashboards

📌 Author

Healthcare Data Cleaning Project
Built for mastering real-world messy data handling.
