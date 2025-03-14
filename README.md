# Data-Analysis
London Bike Sharing Data Analysis
Introduction
This project analyzes the London bike sharing dataset to create an interactive Tableau dashboard. The goal is to demonstrate end-to-end data analysis skills, from data collection and cleaning to dynamic visualization. The dashboard allows users to explore bike ride patterns based on weather, temperature, and time, showcasing proficiency in data handling and visualization.

Dataset
The dataset used is the "London bike sharing dataset" sourced from Kaggle (London bike sharing dataset | Kaggle). It contains 17,414 rows and 10 columns, including:

timestamp: Date and time of the bike rides.
cnt: Number of rides.
t1: Real temperature (Celsius).
t2: "Feels like" temperature (Celsius).
hum: Humidity percentage.
wind_speed: Wind speed (km/h).
weather_code: Weather condition code.
is_holiday: Holiday or not (1 = yes, 0 = no).
is_weekend: Weekend or not (1 = yes, 0 = no).
season: Season code.
Data Collection and Preparation
The dataset was downloaded from Kaggle and uploaded to Google Colab for processing. Python, along with the pandas library, was used to read the data into a DataFrame for exploration and cleaning.

Data Exploration and Manipulation
The data was explored and cleaned using Python and pandas with the following steps:

Basic Exploration:
Checked structure using bikes.info() and bikes.shape (17,414 rows, 10 columns).
Previewed data with bikes.head().
Value Analysis:
Examined distributions with bikes['weather_code'].value_counts() and bikes['season'].value_counts().
Column Renaming:
Renamed columns for clarity:
python

Collapse

Wrap

Copy
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
Humidity Check:
Verified humidity values were between 0 and 1.
Code Mapping:
Converted numeric codes to descriptive labels:
python

Collapse

Wrap

Copy
weather_dict = {1: 'Clear', 2: 'Scattered Clouds', 3: 'Broken Clouds', 4: 'Cloudy', 5: 'Rain', 6: 'Snow', 7: 'Mist'}
bikes['Weather'] = bikes['Weather Code'].map(weather_dict)

season_dict = {0: 'Winter', 1: 'Spring', 2: 'Summer', 3: 'Autumn'}
bikes['Season'] = bikes['Season'].map(season_dict)
Data Export:
Saved the cleaned dataset as London_bikes_final.xlsx for use in Tableau.
Summary of Manipulation Steps
Step	Description	Example Result
Explore Data	Checked structure with info() and shape	17,414 rows, 10 columns
Count Unique Values	Analyzed weather and season distributions	Weather code 1: 6,150 times
Rename Columns	Improved column name clarity	timestamp → Time
Convert Humidity	Confirmed 0-1 range	0.75 = 75%
Map Codes to Descriptions	Added readable labels	Weather code 1 → "Clear"
Save Final Data	Exported to Excel	London_bikes_final.xlsx
Dashboard Design and Implementation in Tableau
The Tableau dashboard is interactive and designed for ease of use, featuring the following components:

Parameters and Calculated Fields
Parameters:
"Moving Average Period": Options include 'day', 'week', 'month'.
"Moving Average Duration": Integer, default set to 10.
Calculated Fields:
"Moving Average Period": Groups time using DATE_TRUNC.
"Min Month" and "Max Month": Define the selected date range.
"In Range": Filters data within the selected range.
Moving Average Chart
Displays trends over time.
Uses "Moving Average Period" on columns and "Number of Rides" on rows.
Applies a moving average based on the duration parameter.
Colors differentiate in-range (green) and out-of-range (purple) data.
Dynamic title, e.g., "50-day moving average".
Total Rides Chart
Shows total rides within the selected date range.
Uses the "In Range Rides" calculated field.
Title updates dynamically, e.g., "London bike rides between [Min Month] and [Max Month]".
Temperature vs. Wind Speed Heat Map
Visualizes the relationship between temperature and wind speed.
Bins temperature and wind speed into categories.
Uses "Number of Rides" for color intensity.
Filtered by the selected date range.
Tooltip Charts
Weather Chart: Bar chart of rides by weather type.
Hour Chart: Bar chart of rides by hour.
Embedded in tooltips for added context.
Set Actions
"Update Moving Average Period Set" action filters the dashboard based on user selections in the moving average chart, ensuring all visuals update dynamically.
Dashboard Layout
Top Left: Total rides chart.
Top Right: Moving average chart.
Bottom: Heat map.
Parameters and filters are placed at the top with clear instructions.
Features light shading and a clean, professional design.
Conclusion
This project demonstrates a complete data analysis workflow, from data collection and manipulation in Python to building an interactive Tableau dashboard. It provides insights into how weather and time influence bike usage in London, making it a valuable addition to my data analysis portfolio.
