✅ DATA PIPE LINE
Here is a basic yet practical ETL (Extract, Transform, Load) pipeline using pandas for data manipulation and scikit-learn for preprocessing

✅ .Compny: CODETECH IT SOLUTIONS PVT.LTD
   .Name: Jatothu Praveen
   .Intern Id: CT06DF436
   .Domain: Data Science
   .Duration: 6 Weeks
   .Mentor: Neela Santhosh Kumar.


✅ Objective:

To create a pipeline that:

1.⁠ ⁠Loads raw data (CSV format)


2.⁠ ⁠Handles missing values


3.⁠ ⁠Encodes categorical variables


4.⁠ ⁠Scales numeric features


5.⁠ ⁠Splits the data into training and test sets




---

🧰 Required Libraries:

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer
from sklearn.impute import SimpleImputer
from sklearn.preprocessing import StandardScaler, OneHotEncoder

1. Extract: Load raw data from a CSV file.
python
Copy
Edit
import pandas as pd

def extract_data(file_path):
    return pd.read_csv(file_path)
2. Transform: Clean and process the data.
python
Copy
Edit
def transform_data(df):
    # Drop rows with missing values
    df = df.dropna()
    # Convert 'date' column to datetime format
    df['date'] = pd.to_datetime(df['date'])
    # Normalize 'sales' column
    df['sales'] = (df['sales'] - df['sales'].mean()) / df['sales'].std()
    return df3. Load: Save the transformed data to a new CSV file.
python
Copy
Edit
def load_data(df, output_path):
    df.to_csv(output_path, index=False)4. Pipeline Execution
python
Copy
Edit
def run_pipeline(input_path, output_path):
    data = extract_data(input_path)
    transformed_data = transform_data(data)
    load_data(transformed_data, output_path)
    print("Data pipeline executed successfully.")
    Input CSV (sales_data.csv):

csv
Copy
Edit
date,sales
2025-07-01,100
2025-07-02,150
2025-07-03,200
Output CSV (processed_sales_data.csv):

cs
Copy
Edit
date,sales
2025-07-01,-1.224745
2025-07-02,0.000000
2025-07-03,1.224745

