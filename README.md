# powerofplots
matplotlib homework 9/22
# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import scipy.stats as st

# Study data files
mouse_metadata_path = "data/Mouse_metadata.csv"
study_results_path = "data/Study_results.csv"

# Read the mouse data and the study results
mouse_metadata= pd.read_csv(mouse_metadata_path)
study_results= pd.read_csv(study_results_path)

# Combine the data into a single dataset
data_df = pd.merge(mouse_metadata, study_results, how = 'outer', on= 'Mouse ID')

# Display the data table for preview
data_df.head()

# Checking the number of mice.
mice=len(data_df["Mouse ID"].unique())
print(mice)

# Getting the duplicate mice by ID number that shows up for Mouse ID and Timepoint
duplicate=data_df.loc[data_df.duplicated(subset=["Mouse ID", "Timepoint"]),'Mouse ID'].unique()
print(duplicate)

# Create a clean DataFrame by dropping the duplicate mouse by its id
data_df.drop_duplicates("Mouse ID")


# Checking the number of mice in the clean DataFrame.
print(mice)

summary_df
print(summary_df)

# Generate a bar plot showing the total number of mice for each treatment throughout the course of the study using pandas. 

grouped_df = pd.DataFrame(merge_table.groupby(["drug Regimen"]).count()).

# Generate a summary statistics table of mean, median, variance, standard deviation, and SEM of the tumor volume for each regimen
mean = merge_table.groupby('Drug Regimen')['Tumor Volume (3mm)'].mean()
median =  merge_table.groupby('Drug Regimen')['Tumor Volume (3mm)'].median()
variance = merge_table.groupby('Drug Regimen')['Tumor Volume (3mm)'].var()
stdv = merge_table.groupby('Drug Regimen')['Tumor Volume (3mm)'].std()
sem = merge_table.groupby('Drug Regimen')['Tumor Volume (3mm)'].sem()
summary_df = pd.DataFrame({"Mean": mean, "Median": median, "variance":variance, "Standard Deviation": stvd, "SEM": sem})

summary_df
# This method is the most straighforward, creating multiple series and putting them all together at the end.
