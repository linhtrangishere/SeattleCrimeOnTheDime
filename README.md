# Seattle Crime on the Dime

## Overview
Seattle Crime on the Dime analyzes the relationship between time, crime type, and location in Seattle using data from the Seattle Police Department (SPD). By examining over 1.49 million crime records, this project investigates whether crime locations can be predicted using partial, non-geographic information such as offense type and time of occurrence.

---

## Problem Statement
Seattle experiences a high volume of reported crimes each year. Delays in reporting or missing location data can hinder emergency response and crime analysis. This project aims to identify patterns linking crime characteristics and geography to support faster decision-making and improved public safety awareness.

---

## Dataset
- **Source:** Seattle Police Department (SPD Crime Data)
- **Size:** 1.49 million rows, 19 columns
- **Time Range:** 2000–2024  
- **Analysis Period:** 2008–2024 (standardized reporting years)
- **Key Features:**
  - Offense Type / Offense Subcategory
  - Crime Category
  - Offense Date
  - Report Date/Time
  - Shooting Type
  - Latitude & Longitude
  - Neighborhood
  - Precinct

---

## Data Preprocessing
- Approximately **33%** of neighborhood values were missing.
- **Geospatial Integration:** Used a GeoJSON boundary file to infer neighborhoods from latitude and longitude, filling **99.32%** of missing values.
- **External API:** Used the official **MCPP (Micro-Community Policing Plans) API** to fill remaining boundary cases.
- **Feature Engineering:**
  - Hour of Day
  - Day of Week
  - Month
  - Time difference between offense and report

---

## Exploratory Data Analysis (EDA)

### Spatial Analysis
- Crime is concentrated in:
  - Downtown Commercial
  - Capitol Hill
  - Northgate
  - Queen Anne

### Crime Type Distribution
- Property crimes dominate, especially **Larceny-Theft**.

### Temporal Patterns
- Offenses peak around **midnight**
- Reports peak during **9 AM – 6 PM**
- **Friday** has the highest number of offenses
- **Monday** has the highest number of reports

---

## Modeling and Results
Classification models were trained to predict **Neighborhood** or **Precinct** using non-geographic features.

### Model Performance

| Model | Target | Accuracy | Key Features |
|------|--------|----------|--------------|
| Random Forest | Neighborhood | **66%** | Offense Subcategory, Hour, Day, Month |
| Naïve Bayes | Precinct | 32.89% | Month, Crime Category, Offense Subcategory |
| Decision Tree | Precinct | 32.72% | Offense Subcategory, Hour, Day |
| KNN | Precinct | 30.34% | Hour, Month, Offense Subcategory |

*SMOTE was applied to address class imbalance.*

---

## Key Findings
- Neighborhood prediction achieved **66% accuracy**, indicating a strong relationship between crime type, time, and location.
- Predicting precincts was more challenging, particularly for distance-based models like KNN.
- Results suggest meaningful geographic patterns exist even without explicit spatial features.

---

## Future Work
- Experiment with advanced ensemble and deep learning models
- Incorporate probabilistic location predictions
- Explore real-time crime data integration
- Assess ethical considerations and model fairness

---

## Team Members
- Adamou Tidjani  
- Gina Philipose  
- Trinh Tran  

---

## Disclaimer
This project is for academic and exploratory purposes only and should not be used for real-world law enforcement decisions.
