#**EXPERIMENT 20 : COVID DATA ANALYSIS**

##*AIM*: **To perform a complete Exploratory Data Analysis (EDA) on a global Covid-19 dataset to identify patterns, clean structural inconsistencies, and extract localized statistical insights using Python** 

*THEORY*:
1. Initial Data Exploration
import pandas as pd, import numpy as np: Importing standard analytical libraries.
data = pd.read_csv("covid_19_data.csv"): Loading the raw CSV file into a DataFrame.
data.head(): Previewing the first 5 records.
data.shape: Checking the total number of rows and columns.
data.info(): Inspecting data types and memory usage.
data.isnull().sum(): Counting missing values in each feature.
2. Data Cleaning & Column Management
data.drop(['SNo', 'Last Update'], axis=1, inplace=True): Removing non-essential tracking columns to clean the dataset.
data.rename(columns={'ObservationDate':'Date'}, inplace=True): Renaming columns for better readability.
data['Date'] = pd.to_datetime(data['Date']): Converting date strings into DateTime objects for time-series operations.
3. Global & Regional Aggregations
Grouping is used to summarize metrics across different geographic layers.

data.groupby('Country/Region')['Confirmed'].sum(): Calculating total confirmed cases per country.
data.groupby('Country/Region')[['Confirmed', 'Deaths', 'Recovered']].sum(): Multi-variable aggregation for a global overview.
data.groupby('Date')['Confirmed'].sum(): Tracking the growth of cases over time.
4. Advanced Filtering & Comparative Analysis
Using conditional logic to extract specific subsets of the data.

data[data.Confirmed < 10]: Filtering regions with minimal case counts.
data[data.Confirmed == 0]: Identifying regions that reported zero cases.
data[data.Region == 'India']: Subsetting data for specific country analysis.
data[data['Deaths'] == 0]['Region'].unique(): Finding regions that maintained a zero-fatality record.
5. Statistical Extremes & State-Level Analysis
top_state = data[data['Country/Region'] == 'Mainland China']: Creating a specific subset for regional deep-dives.
top_state['Confirmed'].max(): Finding the highest single-day or regional confirmed count within a subset.
top_state[top_state['Confirmed'] == top_state['Confirmed'].max()]['Province/State'].values[0]: A nested query to retrieve the exact name of the state/province holding the maximum value.
data.sort_values(by='Confirmed', ascending=False): Ranking the data from most to least impacted.


*CONCLUSION:*
In this project-based experiment, we executed a full Exploratory Data Analysis (EDA) on a complex, real-world Covid-19 dataset. We implemented essential data preparation steps, including handling missing values, dropping redundant features, and performing type conversions on dates. By utilizing the groupby function, we successfully aggregated confirmed, death, and recovery statistics at both global and regional levels. Furthermore, we demonstrated advanced subsetting techniques to isolate high-risk areas and identify regions with high recovery rates. This experiment highlights the power of the Pandas library in transforming raw, messy public health data into structured, meaningful statistical summaries.
