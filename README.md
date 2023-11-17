# SALSA-and-HITS

This repository contains the Python code to perform network analysis on maternal care data using SALSA and HITS algorithms. The analysis aims to identify hub counties and authoritative counties in the context of maternal care based on the birth occurrence and mother's residence data. The input consisted of natality data from https://www.cdc.gov/nchs/nvss/birth_methods.htm (confidential data must be requested), from the years observed (2014-2020) there were over 20 million records used in this analysis. Both algorithms were tested, but were found to generate similar results. 

## Use

1. Install the required packages from `requirements.txt`:
pip install -r requirements.txt

2. Prepare your dataset to have at least two columns: `OC_County_FIPS` and `MR_County_FIPS` (destination, source) Can use code to generate Mock Data (it has also been uploaded). 

3. Run the provided Python script by passing your dataframe to the `process_data_and_run_algorithms` function.
  
## Data Privacy

The code is designed to work with a confidential dataset and as such does not include any real data.

## Results

The results found were quite unique and can be interpreted from many different presepctives.

### These are some images generated from HITS:

![HITS](/HITSOutput.jpg)  
![Exporters](/Exporters.jpg)  
![Importers](/Importers.jpg)  


_Note: The images were generated using ArcGIS, and this code does not contain the steps for this._


