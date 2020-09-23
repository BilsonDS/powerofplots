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
