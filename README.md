🏥 Healthcare Dataset - Exploratory Data Analysis (EDA)
📌 Project Overview

This project performs Exploratory Data Analysis (EDA) on a Healthcare dataset using Python.

The analysis focuses on understanding the dataset structure, handling missing values, cleaning categorical data, converting date columns, creating a new feature for hospital stay duration, performing statistical analysis, and visualizing categorical data.

🎯 Objectives

Load and inspect the healthcare dataset

Understand the shape and columns of the dataset

Check and handle missing values

Clean categorical data

Convert date columns into datetime format

Extract year, month, and day from admission dates

Calculate hospital stay duration

Perform descriptive statistical analysis

Analyze medical conditions by gender

Visualize admission types using a bar chart

🛠️ Technologies Used

🐍 Python

🐼 Pandas

🔢 NumPy

📊 Matplotlib

📈 Seaborn

☁️ Google Colab / Jupyter Notebook

📊 Dataset

The project uses a healthcare dataset containing patient and hospital-related information.

Important Columns
Column	Description
Patient_ID	Unique patient identifier
Age	Patient age
Gender	Patient gender
Medical_Condition	Patient's medical condition
Medical_Code	Medical-related code
Admission_Type	Type of hospital admission
Date_of_Admission	Patient admission date
Discharge_Date	Patient discharge date
Billing_Amount	Hospital billing amount
🔍 EDA Process
1. Data Loading

The dataset is loaded using Pandas.

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("healthcare_data_for_task.csv")

2. Data Inspection

The dataset is inspected using:

df.shape
df.columns
df.info()
df.head()


These commands help understand the dataset structure, number of rows and columns, column names, data types, and sample records.

3. Missing Value Handling

Missing values are checked using:

df.isnull().sum()


Missing values in the Medical_Code column are replaced with "unknown":

df['Medical_Code'] = df['Medical_Code'].fillna('unknown')

4. Data Cleaning

The Admission_Type column is cleaned by removing extra spaces and standardizing capitalization:

df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.title()
)

5. Admission Type Analysis

Unique admission types are identified using:

df['Admission_Type'].unique()


The frequency of each admission type is calculated using:

df['Admission_Type'].value_counts()


A bar chart is used to visualize the distribution:

df['Admission_Type'].value_counts().plot(kind='bar')

plt.xlabel('Admission Type')
plt.ylabel('Number of Patients')
plt.title('Frequency of Admission Types')
plt.xticks(rotation=45)
plt.show()

6. Date Conversion

Admission and discharge dates are converted into datetime format:

df['Date_of_Admission'] = pd.to_datetime(df['Date_of_Admission'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])


Year, month, and day are extracted from the admission date:

df['Admission_Year'] = df['Date_of_Admission'].dt.year
df['Admission_Month'] = df['Date_of_Admission'].dt.month
df['Admission_Day'] = df['Date_of_Admission'].dt.day

7. Feature Creation - Hospital Stay Duration

A new column Stay_Days is created to calculate the number of days a patient stayed in the hospital:

df['Stay_Days'] = (
    df['Discharge_Date'] - df['Date_of_Admission']
).dt.days

8. Statistical Analysis

Descriptive statistics are performed on Billing_Amount:

df['Billing_Amount'].describe()


This provides:

Count

Mean

Standard deviation

Minimum

25th percentile

Median

75th percentile

Maximum

9. Categorical Analysis

A cross-tabulation is performed between Medical_Condition and Gender:

pd.crosstab(
    df['Medical_Condition'],
    df['Gender']
)


This shows the frequency of different medical conditions across genders.

📈 Visualization

The project includes a bar chart showing the frequency of different admission types.

Admission Type Distribution
df['Admission_Type'].value_counts().plot(kind='bar')

plt.title('Admission Type Distribution')
plt.xlabel('Admission Type')
plt.ylabel('Frequency')
plt.show()


The visualization makes it easier to understand the distribution of admission categories.

📁 Project Structure
EDA-Healthcare-Task/
│
├── EDA_TASK_5.ipynb
├── healthcare_data_for_task.csv
└── README.md

💡 Skills Demonstrated

Data Loading

Data Inspection

Data Cleaning

Missing Value Handling

Categorical Data Processing

DateTime Conversion

Feature Engineering

Descriptive Statistics

Cross Tabulation

Data Visualization

Exploratory Data Analysis

✅ Conclusion

This project demonstrates how Python and Pandas can be used to inspect, clean, transform, analyze, and visualize healthcare data.

The analysis provides an understanding of:

👤 Patient information

🏥 Admission types

🩺 Medical conditions

📅 Hospital stay duration

💰 Billing amounts

👥 Medical conditions across genders

Overall, this project provides a practical demonstration of the fundamental steps involved in performing Exploratory Data Analysis on healthcare data using Python.
