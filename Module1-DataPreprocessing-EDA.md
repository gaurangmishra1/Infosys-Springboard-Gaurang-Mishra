# Module 1: Data Preprocessing & EDA
# Author: Gaurang Mishra
# Repo: Infosys-Springboard-Gaurang-Mishra-

import pandas as pd
import matplotlib.pyplot as plt

# -----------------------------
# Step 1: Load Dataset
# -----------------------------
# Example: Replace with your actual dataset path or download link
try:
    df = pd.read_csv("air_quality_data.csv")  # <-- your dataset
except FileNotFoundError:
    print("⚠️ Dataset not found! Please place 'air_quality_data.csv' in the repo folder.")
    exit()

print("✅ Dataset Loaded Successfully!")
print(df.head())

# -----------------------------
# Step 2: Handle Missing Values
# -----------------------------
print("\nMissing values before cleanup:")
print(df.isnull().sum())

# Fill missing numerical values with median
df = df.fillna(df.median(numeric_only=True))

# Drop duplicate rows if any
df = df.drop_duplicates()

print("\n✅ Missing values handled and duplicates removed!")

# -----------------------------
# Step 3: Exploratory Data Analysis (EDA)
# -----------------------------
print("\n📊 Dataset Info:")
print(df.describe())

# Correlation Matrix
print("\n🔗 Correlation Matrix:")
print(df.corr(numeric_only=True))

# Plot pollutant trends (example with PM2.5 if available)
if "PM2.5" in df.columns:
    plt.figure(figsize=(10, 5))
    df["PM2.5"].plot(title="PM2.5 Trend Over Time")
    plt.xlabel("Time Index")
    plt.ylabel("PM2.5")
    plt.grid()
    plt.show()

# -----------------------------
# Step 4: Resampling (Time Series)
# -----------------------------
# Assuming dataset has a datetime column named 'timestamp'
if "timestamp" in df.columns:
    df["timestamp"] = pd.to_datetime(df["timestamp"])
    df = df.set_index("timestamp")

    daily_data = df.resample("D").mean()  # Daily resampling
    weekly_data = df.resample("W").mean()  # Weekly resampling

    print("\n✅ Resampling Done (Daily & Weekly averages created)")
else:
    print("\n⚠️ No timestamp column found, skipping resampling.")

# Save cleaned dataset
df.to_csv("air_quality_cleaned.csv", index=True)
print("\n💾 Cleaned dataset saved as 'air_quality_cleaned.csv'")
