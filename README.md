# Uber Fares Dataset Analysis using Power BI

## Project Overview

This project analyzes Uber ride data to uncover patterns in fare pricing, ride patterns, and operational metrics. Using a dataset of 200,000 Uber rides, I performed comprehensive data cleaning, exploratory analysis, and created an interactive Power BI dashboard to visualize key insights.

**Course:** Introduction to Big Data Analytics (INSY 8413)  
**Instructor:** Eric Maniraguha  
**Student:** NISHIMWE GASARO M. Nicole  
**Date:** July 2025  

---

## Table of Contents

1. [Dataset Overview](#dataset-overview)
2. [Methodology](#methodology)
3. [Data Cleaning Process](#data-cleaning-process)
4. [Feature Engineering](#feature-engineering)
5. [Exploratory Data Analysis](#exploratory-data-analysis)
6. [Power BI Dashboard](#power-bi-dashboard)
7. [Key Findings](#key-findings)
8. [Business Recommendations](#business-recommendations)
9. [Files in Repository](#files-in-repository)
10. [Technical Requirements](#technical-requirements)

---

## Dataset Overview

**Source:** Uber Fares Dataset from Kaggle  
**Original Size:** 200,000 rides  
**Time Period:** 2009-2015  
**Geographic Coverage:** New York City area  

### Original Dataset Structure
- **key:** Unique ride identifier
- **fare_amount:** Trip fare in USD
- **pickup_datetime:** Timestamp of ride start
- **pickup_longitude/latitude:** Starting location coordinates  
- **dropoff_longitude/latitude:** Ending location coordinates
- **passenger_count:** Number of passengers

<img width="1435" height="944" alt="image" src="https://github.com/user-attachments/assets/8a15f5bc-50a7-4cff-b538-56b5004d02d0" />


---

## Methodology

### 1. Data Collection and Loading
- Downloaded Uber dataset from Kaggle
- Loaded data into Python using pandas
- Performed initial data exploration to understand structure

### 2. Data Analysis Approach
- **Tool Stack:** Python (pandas, matplotlib, seaborn) for analysis, Power BI for visualization
- **Analysis Type:** Descriptive and exploratory data analysis
- **Visualization Strategy:** Interactive dashboards with multiple perspectives on the data

---

## Data Cleaning Process

### Initial Data Quality Issues
- **Missing Values:** 1 missing coordinate pair (0.0005%)
- **Data Inconsistencies:** Invalid fare amounts, unrealistic coordinates
- **Outliers:** Extreme values in fares and distances

### Cleaning Steps Performed

#### 1. Missing Value Treatment
- Removed 1 ride with missing dropoff coordinates
- No missing fare amounts found
- Data completeness: 99.95%

<img width="1280" height="323" alt="image" src="https://github.com/user-attachments/assets/099d319c-4b0a-48d6-82e5-ffb17bc53b0c" />


#### 2. Invalid Data Removal
- **Negative/Zero Fares:** Removed rides with fare ≤ $0
- **Extreme Fares:** Capped fares at 99th percentile ($47.83)
- **Invalid Passengers:** Kept only rides with 1-6 passengers
- **Same Location Rides:** Removed rides with identical pickup/dropoff

#### 3. Coordinate Validation
- Removed rides with unrealistic coordinates outside NYC area
- Filtered extreme longitude/latitude values

### Cleaning Results
- **Original Records:** 200,000
- **Cleaned Records:** 189,872
- **Records Removed:** 10,128 (5.1%)
- **Data Retention Rate:** 94.9%

<img width="922" height="511" alt="image" src="https://github.com/user-attachments/assets/32e382ec-c9f1-409e-94b9-bd31fd4ff619" />


---

## Feature Engineering

### Time-Based Features Created
- **hour:** Hour of day (0-23)
- **day_of_week:** Day of week (0=Monday, 6=Sunday)  
- **day_name:** Day name (Monday, Tuesday, etc.)
- **month:** Month number (1-12)
- **year:** Year (2009-2015)
- **is_peak_hour:** Peak hours indicator (7-9 AM, 5-7 PM)
- **is_weekend:** Weekend indicator (Saturday/Sunday)
- **time_period:** Time categories (Morning/Afternoon/Evening/Night)

### Distance and Economic Features
- **trip_distance:** Calculated distance between pickup/dropoff points
- **fare_per_mile:** Economic efficiency metric (fare ÷ distance)

### Feature Engineering Summary
- **Original Features:** 9
- **Enhanced Features:** 18
- **New Features Added:** 9

<img width="1177" height="839" alt="image" src="https://github.com/user-attachments/assets/b56d9ba7-0c49-4124-925a-a58fe95afc3a" />
<img width="985" height="870" alt="image" src="https://github.com/user-attachments/assets/c512070d-efc1-430e-b114-28121e0fc7fa" />



---

## Exploratory Data Analysis

### Descriptive Statistics

#### Fare Amount Analysis
- **Mean Fare:** $10.45
- **Median Fare:** $8.50
- **Standard Deviation:** $7.04
- **Range:** $0.01 - $47.83
- **Outliers:** 14,275 (7.5% of data)

#### Trip Distance Analysis  
- **Mean Distance:** 17.14 miles
- **Median Distance:** 2.99 miles
- **Highly Right-Skewed:** Most trips are short distance

#### Passenger Count Distribution
- **Most Common:** 1 passenger (68.4% of rides)
- **Average:** 1.69 passengers per ride
- **Range:** 1-6 passengers

### Correlation Analysis
Key correlations discovered:
- **Fare vs Distance:** Moderate positive correlation (r = 0.295)
- **Time patterns:** Significant fare variations by hour and day
- **Passenger impact:** Minor correlation with fare amounts

<img width="1137" height="854" alt="image" src="https://github.com/user-attachments/assets/a0c54802-7f79-4b20-9030-0ecdbdb64775" />


---

## Power BI Dashboard

### Dashboard Structure

#### Page 1: Executive Summary (KPI Dashboard)
**Key Performance Indicators:**
- **Total Rides:** 189,872
- **Total Revenue:** $1,984,328
- **Average Fare:** $10.45
- **Average Distance:** 17.14 miles
- **Average Passengers:** 1.69

<img width="1918" height="983" alt="image" src="https://github.com/user-attachments/assets/9dff2173-4d78-4aee-82ad-80fbc3797e46" />


#### Page 2: Time Pattern Analysis
**Visualizations:**
- **Hourly Fare Distribution:** Bar chart showing average fare by hour
- **Daily Ride Volume:** Bar chart of rides by day of week
- **Monthly Trends:** Line chart showing seasonal patterns
- **Interactive Filters:** Hour, month, and day slicers

<img width="1309" height="831" alt="image" src="https://github.com/user-attachments/assets/3c11106f-ef3a-4c53-8ae1-c2d736fadf9b" />


**Key Insights:**
- Peak hours: 6-7 PM (highest ride volume)
- Highest fares: Early morning hours (4-6 AM)
- Busiest days: Friday and Saturday
- Seasonal trend: May shows highest activity

#### Page 3: Fare Distribution Analysis
**Visualizations:**
- **Fare Amount Distribution:** Histogram showing fare frequency
- **Fare vs Distance:** Scatter plot revealing relationship patterns

<img width="1290" height="734" alt="image" src="https://github.com/user-attachments/assets/2b0596ea-0a9f-4093-bd01-4161e61d3e04" />


#### Page 4: Advanced Pattern Analysis
**Visualizations:**
- **Hour vs Day Heatmap:** Shows fare patterns across time dimensions
- **Peak vs Off-Peak:** Donut chart comparing ride volumes

<img width="1136" height="614" alt="image" src="https://github.com/user-attachments/assets/93c7a6e5-5e41-469a-bfb0-ea184ab040a0" />


#### Page 5: Distance Analysis
**Visualizations:**
- **Fare vs Trip Distance:** Detailed scatter plot analysis
- **Distance Distribution:** Understanding trip length patterns

<img width="1166" height="706" alt="image" src="https://github.com/user-attachments/assets/ecbbd5e9-80cb-4a46-8362-748eeae06567" />


---

## Dash Measures
-- Total number of rides
Total Rides = COUNTROWS('uber_data_enhanced')

-- Average fare per ride
Average Fare = AVERAGE('uber_data_enhanced'[fare_amount])

-- Total revenue from all rides
Total Revenue = SUM('uber_data_enhanced'[fare_amount])

-- Average trip distance
Average Distance = AVERAGE('uber_data_enhanced'[trip_distance])

-- Average number of passengers
Average Passengers = AVERAGE('uber_data_enhanced'[passenger_count])

-- Total weekend rides
Weekend Rides = 
CALCULATE(
    COUNTROWS('uber_data_enhanced'),
    'uber_data_enhanced'[is_weekend] = TRUE
)

-- Total weekday rides
Weekday Rides = 
CALCULATE(
    COUNTROWS('uber_data_enhanced'),
    'uber_data_enhanced'[is_weekend] = FALSE
)

-- Total peak hour rides
Peak Hour Rides = 
CALCULATE(
    COUNTROWS('uber_data_enhanced'),
    'uber_data_enhanced'[is_peak_hour] = TRUE
)

-- Weekend vs. Weekday ride difference (percentage)
Weekend vs Weekday Difference = 
DIVIDE([Weekend Rides], [Weekday Rides], 0) - 1

---

## Key Findings

### 🚀 Peak Activity Patterns

#### Busiest Hours (Highest Ride Volume):
1. **7:00 PM** - 12,012 rides
2. **6:00 PM** - 11,504 rides  
3. **8:00 PM** - 11,212 rides

#### Highest Fare Hours (Premium Pricing):
1. **5:00 AM** - $12.53 average
2. **4:00 AM** - $12.49 average
3. **3:00 AM** - $11.15 average

#### Day of Week Patterns:
1. **Friday** - 29,286 rides (busiest)
2. **Saturday** - 28,871 rides
3. **Thursday** - 28,513 rides

### 💰 Economic Insights

#### Revenue Patterns:
- **Total Revenue Generated:** $1,984,328
- **Weekend vs Weekday:** No significant fare premium on weekends
- **Seasonal Peak:** May shows highest monthly activity (17,863 rides)
- **Premium Hours:** Early morning hours command 20% higher fares

#### Distance Economics:
- **Fare-Distance Correlation:** Moderate relationship (r = 0.295)
- **Short Trips Dominate:** 75% of trips under 5 miles
- **Efficiency Metric:** Average $0.61 per mile

### 📊 Operational Insights

#### Demand Patterns:
- **Peak Period:** 5-8 PM represents 18% of daily rides
- **Off-Peak Opportunity:** Late night/early morning shows premium pricing
- **Weekend Distribution:** Consistent demand across Saturday-Sunday

#### Customer Behavior:
- **Solo Travelers:** 68% of rides have 1 passenger
- **Group Rides:** Only 15% of rides have 3+ passengers
- **Distance Preference:** Short urban trips are most common

---

## Business Recommendations

### 1. Dynamic Pricing Strategy
- **Implement surge pricing** during identified peak hours (6-8 PM)
- **Maintain premium rates** for early morning hours (3-6 AM) 
- **Consider distance-based pricing adjustments** for longer trips

### 2. Supply Management
- **Increase driver availability** during Friday-Saturday peak periods
- **Optimize driver positioning** in high-demand areas during 6-8 PM
- **Reduce supply** during low-demand periods (10 PM - 4 AM) except weekends

### 3. Revenue Optimization
- **Target group ride promotions** to increase average passengers per trip
- **Focus marketing** on underutilized time periods with competitive pricing
- **Develop monthly campaigns** targeting seasonal demand variations

### 4. Operational Efficiency
- **Route optimization** for short-distance trips (majority of rides)
- **Driver incentives** for off-peak hour availability
- **Geographic expansion** analysis based on current demand patterns

---

## Files in Repository

### Data Files
- `uber.zip` - Original dataset from Kaggle
- `uber_data_cleaned.zip` - Cleaned dataset ready for analysis
- `uber_data_enhanced.zip` - Final dataset with engineered features

### Analysis Files
- `Uber Data Analysis Project.ipynb` - Complete Python analysis notebook
- `Uber Data Visualization.pbix` - Power BI dashboard file

### Documentation
- `README.md` - This comprehensive report
- `screenshots/` - Folder containing dashboard screenshots

### Visualization Outputs
- `fare_distribution.png` - Fare amount histogram
- `fare_boxplot.png` - Fare distribution box plot  
- `passenger_distribution.png` - Passenger count analysis
- `fare_relationships.png` - Fare vs distance and time analysis
- `correlation_heatmap.png` - Variable correlation matrix
- `time_patterns_analysis.png` - Comprehensive time analysis
- `monthly_analysis.png` - Seasonal trend analysis

---

## Technical Requirements

### Python Libraries Used
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from datetime import datetime
```

### Power BI Features Utilized
- **Data Import:** CSV file connection
- **Visualizations:** Bar charts, histograms, scatter plots, heatmaps, KPI cards
- **Interactivity:** Slicers, filters, drill-down capabilities
- **Calculations:** DAX formulas for time-based metrics

### System Requirements
- **Python 3.8+** with pandas, numpy, matplotlib, seaborn
- **Power BI Desktop** (latest version)
- **Memory:** Minimum 4GB RAM for dataset processing

---

## Data Quality Assurance

### Validation Steps Performed
1. **Range Checks:** Verified fare amounts within realistic bounds
2. **Completeness Checks:** Identified and handled missing values
3. **Consistency Checks:** Ensured coordinate values within NYC area
4. **Outlier Analysis:** Statistical identification and treatment of extreme values

### Data Integrity Measures
- **Backup Preservation:** Original dataset retained unchanged
- **Process Documentation:** All cleaning steps logged and reproducible
- **Quality Metrics:** 94.9% data retention rate maintained

---

## Conclusion

This analysis successfully identified key patterns in Uber ride data that can inform business strategy and operational decisions. The interactive Power BI dashboard provides stakeholders with tools to explore data from multiple perspectives, while the comprehensive data cleaning and feature engineering ensures reliable insights.

The project demonstrates strong data analysis fundamentals, from initial exploration through final presentation, and provides actionable recommendations based on statistical evidence from nearly 190,000 ride records.

---

**Project Status:** ✅ Complete  
**Last Updated:** July 2025  
**Dashboard Access:** Available in repository as .pbix file

*For questions or additional analysis requests, please refer to the course instructor or repository documentation.*
