# The death cycle of Pollution

This repository contains an analysis of greenhouse gas (GHG) emissions in relation to temperature and primary energy consumption. The notebook provides insights into how these variables interact and offers methods to visualize trends, smooth fluctuations, and filter data for clearer analysis.

## Project Overview

The purpose of this analysis is to understand the correlation between temperature, primary energy consumption, and GHG emissions. By smoothing the data and removing fluctuations, the goal is to highlight any steadily increasing trends, offering a cleaner visualization for analysis.

## Contents

- `ghg_emission_analysis.ipynb`: Jupyter Notebook with the full analysis, including:
  - Data import and preprocessing.
  - Smoothing of temperature and energy consumption data using a rolling average.
  - Fluctuation removal to ensure a steadily increasing trend in visualizations.
- `data/`: Folder containing the dataset used for this analysis (you may need to provide the actual dataset file in this folder).

## Installation and Requirements

To run the notebook, you need the following packages:

- Python 3.x
- Jupyter Notebook
- Required libraries (install via pip):
  ```bash
  pip install pandas matplotlib
  ```

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/HS5760TermProject/SemProject.git
   ```
2. Navigate to the repository and open the notebook:
   ```bash
   ghg_emission_analysis.ipynb
   ```

3. Follow the steps in the notebook to load, preprocess, and visualize the data.

### Key Sections in the Notebook

1. **Data Loading and Preprocessing**: Import the temperature and primary energy consumption data, then perform any necessary cleaning or transformation steps.
2. **Data Smoothing**: Apply a moving average to the data to smooth out fluctuations.
3. **Fluctuation Removal**: Filter out rows causing fluctuations to create a steadily increasing trend in both temperature and energy consumption.
4. **Visualization**: Plot the smoothed and filtered data with a reference line (x = y) for trend analysis.

### Example Code

Below is an example of how fluctuations were removed for steady trend visualization:

```python
import matplotlib.pyplot as plt
import pandas as pd

# Filter out rows with non-increasing values in Temperature or primary_energy_consumption
filtered_data = merged_data_3[(merged_data_3['Temperature'].diff() >= 0) & 
                              (merged_data_3['primary_energy_consumption'].diff() >= 0)]

# Plot the filtered data
plt.figure(figsize=(12, 6))
plt.plot(filtered_data['Temperature'], filtered_data['primary_energy_consumption'], color='blue', label='Filtered Data')
plt.plot(filtered_data['Temperature'], filtered_data['Temperature'], color='red', linestyle='--', label='x=y Line')
plt.xlabel('Temperature')
plt.ylabel('Primary Energy Consumption')
plt.legend()
plt.title('Temperature vs Primary Energy Consumption with Fluctuations Removed')
plt.show()
```

## Results

The visualizations produced show trends between temperature and energy consumption with fluctuations minimized, allowing for a clearer analysis of potential correlations.

## License

This project is licensed under the MIT License.