# BLOOD PRESSURE MEASUREMENT AND ANALYSIS# 🩺 Blood Pressure Measurement and Analysis

## 📘 Project Overview
This project focuses on measuring and analyzing blood pressure data using a digital blood pressure monitor and Python for data analysis.  
The goal is to visualize, interpret, and understand blood pressure trends for healthcare insights.

## ⚙️ Hardware Used
- Digital Blood Pressure Measurement Machine (Sensor-based)
- Microcontroller Interface / USB Data Transfer
- Computer with Python installed

## 💻 Software & Tools
- Python (NumPy, pandas, matplotlib)
- Jupyter Notebook or VS Code
- CSV data files for readings

## 🧠 Working Principle
1. Collect blood pressure readings (systolic, diastolic, pulse).
2. Store readings in a `.csv` file.
3. Use Python to analyze and visualize the data:
   - Calculate average, min, and max blood pressure.
   - Plot graphs for better visualization.
4. Interpret results to determine health status.

## 📊 Sample Code
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the data
df = pd.read_csv('bp_data.csv')

# Basic stats
print(df.describe())

# Visualization
plt.plot(df['Time'], df['Systolic'], label='Systolic')
plt.plot(df['Time'], df['Diastolic'], label='Diastolic')
plt.xlabel('Time')
plt.ylabel('Blood Pressure (mmHg)')
plt.title('Blood Pressure Trend')
plt.legend()
plt.show()
