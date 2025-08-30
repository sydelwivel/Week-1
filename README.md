# ⚡️ The Sustainable Energy & Efficiency Project - Week 1 ⚡️

Welcome to the Week 1 submission for the Sustainable Energy & Efficiency Project! This initial phase focuses on understanding the global landscape of power generation by exploring a comprehensive dataset of power plants across the world. Our goal is to lay the groundwork for future analysis and machine learning applications.

## 📜 Table of Contents
* [Problem Statement](#-problem-statement)
* [Data Collection and Understanding](#-data-collection-and-understanding)
* [Data Preprocessing](#-data-preprocessing)
* [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
* [Data Splitting](#-data-splitting)
* [Next Steps](#-next-steps)

---

## 🎯 Problem Statement

The world is at a critical juncture in its energy transition. To build a sustainable future, we must understand the current state of global energy production. This project aims to analyze the distribution and capacity of power plants worldwide to answer key questions:

* What are the dominant primary fuel sources for energy generation globally?
* Which countries lead in total power generation capacity?
* What is the balance between renewable and non-renewable energy sources in top-producing countries?

By exploring these questions, we set the stage for more advanced analysis, such as predicting a power plant's primary fuel type based on its characteristics.

---

## 📊 Data Collection and Understanding

For this analysis, we are using the **Global Power Plant Database**, a comprehensive, open-source dataset of power plants around the world.

* **Source**: The dataset was sourced from Kaggle, containing information on approximately 35,000 power plants.
* **Key Features**: The dataset includes crucial information for our analysis, such as:
    * `country_long`: The name of the country.
    * `capacity_mw`: The installed capacity in megawatts.
    * `primary_fuel`: The primary fuel source used by the plant (e.g., Coal, Gas, Hydro, Solar).
    * `latitude` & `longitude`: Geographic coordinates of the plant.

Initial exploration using `.info()`, `.describe()`, and `.isnull().sum()` revealed that the dataset had a significant number of missing values in columns related to generation data and ownership, which guided our preprocessing strategy.

---

## ⚙️ Data Preprocessing

A clean dataset is the foundation of any reliable analysis. The following steps were taken to prepare the data:

1.  **Handling Missing `primary_fuel`**: Rows with no `primary_fuel` data were dropped, as this is our primary variable of interest.
2.  **Dropping High-Null Columns**: Columns with over 50% missing values (e.g., `other_fuel2`, `other_fuel3`, `generation_gwh_*`) were removed to reduce noise.
3.  **Imputing Missing Values**:
    * Missing **numerical** values were filled with the **mean** of their respective columns.
    * Missing **categorical** values (like `owner`) were filled with the **mode** (most frequent value).
4.  **Feature Engineering**: A new column, `fuel_category`, was created to classify each power plant as either **Renewable** (`Hydro`, `Solar`, `Wind`, etc.) or **Non-Renewable** (`Coal`, `Gas`, `Oil`, etc.). This simplifies comparative analysis.

The cleaned dataset has been saved to `preprocessed_global_power_plant_database.csv`.

---

## 📈 Exploratory Data Analysis (EDA)

Visualizations are essential for uncovering insights. We created three key plots to understand the data:

1.  **Global Distribution of Primary Energy Sources (Pie Chart)**: This chart shows the market share of each primary fuel. It highlights the global reliance on a few key sources like coal, hydro, and natural gas.
2.  **Top 10 Countries by Total Capacity (Bar Chart)**: This visual identifies the global leaders in energy infrastructure, providing context on which nations have the largest-scale power systems.
3.  **Renewable vs. Non-Renewable Capacity (Stacked Bar Chart)**: This chart breaks down the energy mix of the top 10 countries, revealing the extent of their investment in sustainable energy sources versus traditional fossil fuels.

---

## 🔪 Data Splitting

To prepare for the next phases of the project (Weeks 2 & 3), which will likely involve machine learning, the preprocessed data was split into training and testing sets.

* **Features (X)**: All relevant columns after preprocessing. Categorical variables were one-hot encoded to be used in a model.
* **Target (y)**: The `fuel_category` column ('Renewable' or 'Non-Renewable').
* **Ratio**: The data was split with 80% for training and 20% for testing. `stratify=target` was used to ensure the proportion of renewable and non-renewable plants was the same in both the train and test sets.

This step ensures that we can train a model and then test its performance on unseen data.

---

## 🚀 Next Steps

This Week 1 submission successfully establishes a clean, well-understood foundation. The project is now ready for the next exciting phase: **Model Training & Evaluation**! In the coming weeks, we will use this prepared data to build and refine a machine learning model to predict whether a power plant is renewable or non-renewable.
