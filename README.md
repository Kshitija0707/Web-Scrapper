# Web-Scrapper
import pandas as pd
import plotly.express as px

def generate_interactive_visualizations(data_file):
    try:
        df = pd.read_csv(data_file)
    except FileNotFoundError:
        print(f"Error: File '{data_file}' not found.")
        return
    except pd.errors.EmptyDataError:
        print(f"Error: File '{data_file}' is empty.")
        return

    # Check if required columns exist
    required_columns = ['price', 'sqft_living', 'waterfront', 'zipcode']
    for column in required_columns:
        if column not in df.columns:
            print(f"Error: Column '{column}' not found in the dataset.")
            return

    # Generate interactive visualizations using Plotly
    fig = px.scatter(df, x='price', y='sqft_living', color='waterfront', hover_data=['zipcode'])
    fig.show()

def main():
    # Specify path to the dataset
    data_file = "C:/Users/ACT/Downloads/RealEstateData.csv" 

    generate_interactive_visualizations(data_file)

if __name__ == "__main__":
    main()
