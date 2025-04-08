# Chicago Taxi Data ETL Project

A complete end-to-end **ETL pipeline** for automating the extraction, transformation, and loading of **Chicago taxi trip data** and **weather data**, built with **Python, Jupyter Notebooks**, and **AWS Services** including Lambda, S3, Glue, and Athena.
##  Project Overview
This project is a complete ETL pipeline that works with open data from the city of Chicago. It performs the following steps:

- **Extracts** Gets taxi trip and weather data using APIs and web scraping.
- **Transforms** Cleans the data, adds helpful information (like dates and company names), and organizes it into tables.
- **Loads** Saves the final data into Amazon S3 bucket, where it can be queried using AWS Athena

The ETL steps are done using **AWS Lambda** for processing, and **Jupyter Notebooks** for development, testing, and visualization.
## Data Sources

- [City of Chicago Data Portal](https://data.cityofchicago.org/) – Taxi trip data
- [Open-Meteo](https://open-meteo.com/) – Weather data
- [Wikipedia](https://en.wikipedia.org/wiki/Community_areas_in_Chicago) – Community area names and codes

##  Notebooks & Functions

### 1. **Data Collection**
| Notebook | Description |
|---------|-------------|
| `02_webscraping.ipynb` | Scrapes community area names and codes from Wikipedia |
| `03_get_taxidata.ipynb` | Collects daily taxi trip records from City of Chicago API |
| `04_get_weather_data.ipynb` | Acquire historical weather data from Open-Meteo API |

### 2. **Data Preparation**
| Notebook | Description |
|---------|-------------|
| `05_date_dimension_table.ipynb` | Creates a date dimension table |
| `06_chicago_data_mapping.ipynb` | Cleans raw taxi trip data and creates master tables for companies and payment types |

### 3. **Lambda Function Development**
| Notebook | Description |
|---------|-------------|
| `07_transform_load.ipynb` | Transforms raw taxi and weather data into dataframes, Updates master tables and maps taxi trip data with master tables |

### 4. **AWS Lambda Functions**
- **Extract Function**  
  - Pulls and transforms raw taxi and weather data.
- **Transform & Load Function**  
  - Updates and uploads transformed data and master tables to AWS S3..

### 5. **Visualization**
| Notebook | Description |
|---------|-------------|
| `08_local_visualisation.ipynb` | Downloads processed data from S3, merges datasets for analysis and generates plots using Seaborn. |

---
## Data Analysis & Visualization

Using the transformed datasets. Visualizations are generated using **Seaborn**, with processed data pulled from S3.
##  Output Tables

| Table Name | Description |
|------------|-------------|
| `taxi_trips_data` | Transformed taxi trip data |
| `weather_data` | Daily weather details such as temperature, rain, precipitation and wind |
| `date_dimension` | A table with date info for easier time-based analysis |
| `company_master` | Mapping of taxi companies with IDs |
| `payment_type_master` | Mapping of payment types with IDs |
| `community_areas_master` | Reference table for Chicago's community areas |
---
## Technologies Used
- **Languages:** Python
- **Libraries:** Pandas, NumPy, Seaborn, requests
- **Cloud Services:** AWS Lambda, AWS S3, AWS Glue, AWS Athena
- **APIs:** Chicago Data Portal, Open Meteo
- **Other Tools:** Jupyter Notebooks, BeautifulSoup (for web scraping)
