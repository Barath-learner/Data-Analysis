# London Bike Sharing Data Analysis

## Overview
This project analyzes the London bike sharing dataset to create an interactive Tableau dashboard. The goal is to demonstrate end-to-end data analysis skills, from data collection and cleaning to dynamic visualization. The dashboard allows users to explore bike ride patterns based on weather, temperature, and time, showcasing proficiency in data handling and visualization.

## Dataset
The dataset used is the "London bike sharing dataset" sourced from Kaggle ([London bike sharing dataset | Kaggle](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)). It contains **17,414 rows** and **10 columns**, including:

- `timestamp`: Date and time of the bike rides.
- `cnt`: Number of rides.
- `t1`: Real temperature (Celsius).
- `t2`: "Feels like" temperature (Celsius).
- `hum`: Humidity percentage.
- `wind_speed`: Wind speed (km/h).
- `weather_code`: Weather condition code.
- `is_holiday`: Holiday or not (1 = yes, 0 = no).
- `is_weekend`: Weekend or not (1 = yes, 0 = no).
- `season`: Season code.

## Data Collection and Preparation
The dataset was downloaded from Kaggle and uploaded to Google Colab for processing. Python, along with the **pandas** library, was used to read the data into a DataFrame for exploration and cleaning.

## Data Exploration and Manipulation
The data was explored and cleaned using Python and pandas with the following steps:

1. **Basic Exploration:**
   - Checked structure using `bikes.info()` and `bikes.shape` (17,414 rows, 10 columns).
   - Previewed data with `bikes.head()`.

2. **Value Analysis:**
   - Examined distributions with `bikes['weather_code'].value_counts()` and `bikes['season'].value_counts()`.

3. **Column Renaming:**
   - Renamed columns for clarity:
     ```python
     new_columns = {
         'timestamp': 'Time',
         'cnt': 'Number of Rides',
         't1': 'Temperature Real',
         't2': 'Temperature Felt',
         'hum': 'Humidity',
         'wind_speed': 'Wind Speed',
         'weather_code': 'Weather Code',
         'is_holiday': 'Is Holiday',
         'is_weekend': 'Is Weekend',
         'season': 'Season'
     }
     bikes.rename(columns=new_columns, inplace=True)
