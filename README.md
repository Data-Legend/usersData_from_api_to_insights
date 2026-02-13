# USERS DATA: FROM API TO EXPLORATORY DATA ANALYSIS

A Python-based data pipeline that fetches, flattens, cleans, and visualizes user data from the DummyJSON API. 

## Overview
This repository contains a Jupyter Notebook demonstrating an end-to-end workflow for handling nested JSON data retrieved via a paginated REST API. It utilizes `pandas` for efficient data manipulation and `seaborn` for clean, minimal data visualizations.

## 1. Fetching and Handling Data from API
- **Pagination Logic:** Implements a `while` loop to dynamically update the `limit` and `skip` parameters to extract all available records iteratively.
- **Header Spoofing:** Uses a custom `User-Agent` header via Pandas' `storage_options` to bypass HTTP 403 Forbidden restrictions on the public API.
- **JSON Flattening:** Employs `pd.json_normalize()` to automatically unpack and flatten deeply nested JSON dictionaries (like `address` and `company` fields) into standard, accessible DataFrame columns.

## 2. Data Exploration
Performs basic exploratory data analysis to quickly understand the dataset's structure:
- Extracting the DataFrame's shape and mapping out column data types.
- Identifying missing values and checking for duplicate rows.
- Generating summary statistics (`describe()`) for numerical features.
- Analyzing value counts for key categorical columns (e.g., gender, city, blood group).

## 3. Data Cleaning
- Focuses on preparing numerical data for accurate visualization.
- Imputes missing values in critical numeric columns (`age`, `height`, `weight`) using the **median** rather than the mean to prevent skewness from potential outliers.

## 4. Data Visualization
Uses heavily commented, minimalistic `seaborn` and `matplotlib` code without redundant boilerplate to answer specific data questions visually:

### Key Insights: Top 10 Cities
![Top 10 Cities with the Most Users](/images/top_10_cities_by_users.png)

- **Demographics:** Horizontal count plots to display the Top 10 cities without text overlap, and standard count plots for user gender distribution.
- **Averages:** Side-by-side bar plots detailing overall average age, height, and weight.
- **Correlations:** A multi-variable scatterplot mapping Age (x-axis) vs. Height (y-axis), with dot size representing Weight and color hue grouping by Gender, to identify potential trends.

## Requirements
- `pandas`
- `seaborn`
- `matplotlib`
