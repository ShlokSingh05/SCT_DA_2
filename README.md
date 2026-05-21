Global Superstore Data Cleaning Pipeline
A Python script to clean and preprocess the Global Superstore dataset for analysis. Handles missing values, removes duplicates, converts data types, and adds useful calculated fields.

📋 Overview
This script takes the raw Global Superstore sales data and performs essential data cleaning operations. It's designed to be run in a Google Colab environment but can be adapted for local use.

✨ Features
Missing Value Handling: Fills missing values appropriately (mode for categorical data, median for numerical data)

Duplicate Removal: Removes duplicate rows and duplicate Order-Product combinations

Data Type Conversion: Converts dates, numbers stored as text, and categorical variables to proper data types

Feature Engineering: Adds calculated columns including:

Date components (year, month, quarter, weekday)

Profit margin percentage

Shipping days

Profitability flag

Sales per unit

Data Validation: Generates summary statistics and quality checks

Visualization: Creates basic plots to verify cleaning results

Export: Saves cleaned data to CSV with timestamp

🚀 Getting Started
Prerequisites
bash
pip install pandas numpy matplotlib seaborn
Running the Script
In Google Colab (default path):

Place your superstore.csv.zip in /content/sample_data/

Run the script directly

Locally:

Change the file path in pd.read_csv()

Run the script in any Python environment

python
# Change this line to your file path
df = pd.read_csv("your_file_path_here.csv")
📊 What Gets Cleaned
Issue	Handling Method
Missing text values	Fill with mode (most frequent value)
Missing numerical values	Fill with median
Duplicate rows	Remove completely
Duplicate order-product combinations	Keep first occurrence
Date columns	Convert to datetime
Currency columns	Remove $ and commas, convert to float
Discount values	Convert from whole numbers to decimals (15 → 0.15)
Categorical data	Convert to category type
ID columns	Convert to string
📁 Output Files
The script generates a cleaned CSV file with a timestamp:

text
superstore_cleaned_20240101_120000.csv
📈 Sample Output
After running the script, you'll see:

Missing values summary

Count of duplicates removed

Data type conversion status

New columns added

Validation report with row/column counts

Distribution plots for sales and profit

Profit margin by category chart

Sales trend over years

🛠️ Customization
Adjusting the File Path
python
# Change this line to your specific path
df = pd.read_csv("/your/custom/path/superstore.csv")
Modifying Missing Value Strategy
python
# For numerical columns - change from median to mean
df[col].fillna(df[col].mean(), inplace=True)

# For categorical columns - change from mode to a custom value
df[col].fillna("Not Available", inplace=True)
Adding More Derived Columns
python
# Example: Add customer lifetime value placeholder
# df['Customer.LTV'] = df.groupby('Customer.ID')['Sales'].transform('sum')
📝 Notes
The script assumes your data has standard column names like Order.Date, Ship.Date, Sales, Profit, etc.

If your data has different column names, you'll need to update the references

The discount conversion assumes values >1 need to be divided by 100

🤝 Contributing
Feel free to fork and modify this script for your own data cleaning needs. The approach is pretty standard and should work for most retail datasets with similar structure.
