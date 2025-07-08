#DATA PIPE LINE
import pandas as pd

def extract(file_path):
    """Extract data from a CSV file."""
    df = pd.read_csv(file_path)
    return df

def transform(df):
    """Transform the data: clean and process."""
    # Drop rows with missing values
    df = df.dropna()
    # Convert column 'date' to datetime
    if 'date' in df.columns:
        df['date'] = pd.to_datetime(df['date'])
    # Example: create a new column 'amount_usd' from 'amount_inr' (assuming 1 USD = 83 INR)
    if 'amount_inr' in df.columns:
        df['amount_usd'] = df['amount_inr'] / 83
    return df

def load(df, output_path):
    """Load the transformed data to a new CSV file."""
    df.to_csv(output_path, index=False)

if __name__ == "__main__":
    # File paths
    input_csv = 'input_data.csv'
    output_csv = 'cleaned_data.csv'

    # Pipeline steps
    data = extract(input_csv)
    transformed_data = transform(data)
    load(transformed_data, output_csv)
    print("Data pipeline executed successfully.")

