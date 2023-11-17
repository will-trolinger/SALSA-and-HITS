# SALSA-and-HITS

This repository contains the Python code to perform network analysis on maternal care data using SALSA and HITS algorithms. The analysis aims to identify hub counties and authoritative counties in the context of maternal care based on the birth occurrence and mother's residence data. The input consisted of natality data from https://www.cdc.gov/nchs/nvss/birth_methods.htm (confidential data must be requested), from the years observed (2014-2020) there were over 20 million records used in this analysis. Both algorithms were tested, but were found to generate similar results. 
  
## Data Privacy

The code is designed to work with a confidential dataset and as such does not include any real data.

## Use

1. Install the required packages from `requirements.txt`:
  ```
    pip install -r requirements.txt
  ```

2. Prepare your dataset to have at least two columns: `OC_County_FIPS` and `MR_County_FIPS` (destination, source) Can use code to generate Mock Data (it has also been uploaded):
   ```
     mock_data = pd.DataFrame({'OC_County_FIPS': np.random.choice(fips_codes, size=100), 'MR_County_FIPS': np.random.choice(fips_codes, size=100)})
   ```

4. Create Graph from sources and destinations:
   ```
    nodes = dataframe[["OC_County_FIPS", "MR_County_FIPS"]].drop_duplicates().values.flatten()
    edges = list(zip(dataframe["OC_County_FIPS"], dataframe["MR_County_FIPS"]))

    G = nx.DiGraph()
    G.add_nodes_from(nodes)
    G.add_edges_from(edges)

   ```
5. Run SALSA and HITS:
   ```
    salsa_hubs, salsa_authorities = salsa_algorithm(G)
    hits_hubs, hits_authorities = nx.hits(G, max_iter=100, tol=1.0e-6)
   ```
6. Save Results:
   ```
    dfScores = pd.DataFrame({
        "County": nodes,
        "SALSA_Hub_Score": salsa_hub_scores,
        "SALSA_Authority_Score": salsa_authority_scores,
        "HITS_Hub_Score": hits_hub_scores,
        "HITS_Authority_Score": hits_authority_scores,
    })
   ```
   ...
   ```
   scores.to_csv("scores.csv", index=False)
   ```

## Results

The results found were quite unique and can be interpreted from many different presepctives.

### These are some images generated from HITS:

![HITS](/HITSOutput.jpg)  
![Exporters](/Exporters.jpg)  
![Importers](/Importers.jpg)  


_Note: The images were generated using ArcGIS, and this code does not contain the steps for this._


