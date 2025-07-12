# Overview
## About the Dataset
The Post-Pandemic Remote Work Health Impact 2025 dataset presents a comprehensive, global snapshot of how remote, hybrid, and onsite work arrangements are influencing the mental and physical health of employees in the post-pandemic era. Collected in June 2025, this dataset aggregates responses from a diverse workforce spanning continents, industries, age groups, and job roles. It is designed to support research, data analysis, and policy-making around the evolving landscape of work and well-being.

* __Author:__ Pratyush Puri
* __Site:__ Kaggle
* __Dataset URL:__ [Remote Work Health Impact Survey June 2025](https://www.kaggle.com/datasets/pratyushpuri/remote-work-health-impact-survey-2025)

# The Questions
Below are the questions that I answered in the project:
1. What are the top health issues presented, and how do they relate to each mental health status?
2. What mental health issues are associated with the different job arrangements?
3. What is the impact of each work arrangement on work-life balance?
4. What is the relationship between job role and mental health?

# Tools I Used
* __Python__: It was the core tool,it allowed me to clean and analyze and plot the data.
    * __Pandas__: Library used to analyze the data.
    * __Matplot__: Library used to plot the data.
    * __Seaborn__: Library to personalize and create more advanced visuals.
* __Jupyter Notebooks__: I used it to run my `Python` scripts.
* __Visual Studio Code__: Served as the development environment where I wrote, ran, and debugged all my `Python` scripts.

# Data Preparation and Cleanup
For each notebook, I started by importing the necessary libraries, loading the dataset, performing initial data cleaning, and creating the color palette to ensure data quality and standarization.

View the detailed steps in my notebook: [1_EDA.ipynb](project/1_EDA.ipynb)

```python
import ast
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
from matplotlib.colors import LinearSegmentedColormap, to_hex, ListedColormap

# Load the dataset
df = pd.read_csv('data\post_pandemic_remote_work_health_impact_2025.csv')

# Clean the data
df_survey = df.copy()
df_survey['Survey_Date'] = pd.to_datetime(df_survey['Survey_Date'], format='%Y-%m-%d')
df_survey['Physical_Health_Issues'] = df_survey['Physical_Health_Issues'].apply(lambda x: [item.strip() for item in x.split(';')] if pd.notnull(x) else x)
df_survey['Mental_Health_Status'] = df_survey['Mental_Health_Status'].fillna('Non-Diagnosis')

# Definition of the color palette
custom_colors = ['#A6AEAE', '#FB4F2A', '#A90113', '#75000C', '#3C0B09']
custom_cmap = ListedColormap(custom_colors)
smooth_cmap = LinearSegmentedColormap.from_list("custom_gradient", custom_colors, N=256)
```