# MobilityForCO2Prediction 
This is the repository for all the data and code for reproducing the analysis in the manuscript: Wang MN, Zhang XZ, Tan SY, Zhang Q, Sai B, Cai MS, Guo SH, Wrathall D, Obersteiner M, Li MJ, Liu Z, Chen XH, and Lu X. Inferring Carbon Emissions from Human Mobility Data. 2023, under review. 
## Computational environment

```
Python version 3.7.4 
JupyterNotebook Anaconda3
Platform: Intel(R) Core(TM) i7-10875H CPU @ 2.30GHz   2.30 GHz (64-bit)
Running under: Windows Feature Experience Pack1000.19053.1000.0
```
Python packages versions are specified as follows:

```
[1] conda                     4.12.0           py37h03978a9_0    conda-forge
[2] lightgbm                  3.0.0            pypi_0            pypi
[3] matplotlib                3.4.2            pypi_0            pypi
[4] networkx                  2.6.1            pypi_0            pypi
[5] numpy                     1.21.5           pypi_0            pypi
[6] pandas                    1.3.5            pypi_0            pypi
[7] scikit-learn              0.24.1           pypi_0            pypi
[8] scipy                     1.7.3            pypi_0            pypi
[9] seaborn                   0.12.1           pypi_0            pypi
[10] tqdm                     4.36.1           py_0              defaults
[11] xgboost                  1.6.2            pypi_0            pypi
```


## 1. CO<sub>2</sub> emissions data
This dataset is sourced from the Global Gridded Daily CO2 Emissions Dataset (GRACED), accessible at <https://carbonmonitor-graced.com/>. This dataset is supported by the work in [Scientific Data 7, 392 (2020)](https://doi.org/10.1038/s41597-020-00708-7), [Nature Communication 11, 5172 (2020)](https://doi.org/10.1038/s41467-020-18922-7), [The Innovation, 3, 1 (2022) ](https://doi.org/10.1016/j.xinn.2021.100182) and [Scientific Data 10, 69 (2023)](https://www.nature.com/articles/s41597-023-01963-0). GRACED has been processed to derive daily CO2 emission within distinct regional boundaries. 

## 2. Mobility data
* **China** - Mobility data for China, collected between January 1 to February 29, 2020, is aggregated at the city level.
  
The mobility data in Italy, the U.S., and Mexico are open-source and accessible through the following links.
* **Italy** - Mobility data for Italy, spanning from January 18 to June 26, 2020, encompasses aggregated origin-destination movements between different Italian provinces. The dataset is available at <https://data.humdata.org/dataset/covid-19-mobility-italy>.
* **the U.S.** - Mobility data for the U.S., spanning from January 1 to February 15, 2020, offers valuable insights into population movement patterns at the county and state levels. The datasets are accessible at <https://github.com/GeoDS/COVID19USFlows>.
* **Mexico** - Mobility data for Mexico, depicting travel patterns between municipalities in Mexico, covers the period from January 1 to December 31, 2020, and can be accessed at <https://osf.io/42xqz/>.

## 3. Correlation
This module presents the correlation analysis between human mobility and CO<sub>2</sub> emissions. 

* **`spatiotemporal correlations.ipynb`** - Code for Subplots Fig. 1a-c: calculate changes in intercity mobility and CO<sub>2</sub> emissions of multi-source, domestic aviation, and ground transportation.
* **`calculatie global features.ipynb`** - Calculate global features using `Mobility Data`.
* **`calculatie node features.ipynb`** - Calculate node features using `Mobility Data`.
* **`correlations between network features and CO2 emissions.ipynb`** - Code for Fig. 1e: calculate the correlation coefficient.
* **global** - Results of `calculatie global features.ipynb`, with the summary available in `global_features.csv`.
* **node** - Results of `calculatie node features.ipynb`, with the summary available in `node features.csv`.

## 4. Prediction
This module presents the prediction algorithm for the CO<sub>2</sub> emissions with Strategy 1 and Strategy 2.
* **`LGBM-strategy1.ipynb`** and **`LGBM-strategy2.ipynb`** - The respective code for Strategy 1 and Strategy 2.
* **`res_lgbm_s1.csv`** and **`res_lgbm_s2.csv`** - The respective prediction result of `LGBM-strategy1.ipynb` and `LGBM-strategy2.ipynb`.
* **`plot the predicted result.ipynb`** - Code for Fig. 2: analyze the relations between the predicted CO<sub>2</sub> emissions and observed CO<sub>2</sub> emissions for each strategy.

## 5. Evaluation
This module presents the code and data for evaluating the importance of features and robustness analysis.
* **`LGBM-strategy1-null model.ipynb`** and **`LGBM-strategy2-null model.ipynb`** - The different strategies for predicting CO<sub>2</sub> emissions with population and latitude-longitude features.
* **`res_lgbm_s1_null.csv`** and **`res_lgbm_s2_null.csv`** - The respective prediction result of `LGBM-strategy1-null.ipynb` and `LGBM-strategy2-null.ipynb`.
* **`ablation experiment.ipynb`** - Code for Fig. 3c: conduct ablation experiments.
* **`prediction with all historial data.ipynb`** - Code for Fig. 3d: predict CO<sub>2</sub> emissions with all historical data.


## 6. Extrapolation
This module prepares the input data for predictive models for various countries by incorporating network features from their respective mobility data. The outputs were then stored in the specified files. Subsequently, the data and predictive model were employed with the code shown in 4. Prediction to generate the results in Fig. 4.
* **`input_Italy.csv`**
* **`input_USA_county.csv`**
* **`input_Mexico.csv`**
  
## 7. City clusters
This module includes the input data and code for city cluster analysis.
* **`city cluster- normal times.csv`** - The input data for `city cluster.ipynb`, includes total CO<sub>2</sub> emission data for cities, along with information about their respective city clusters.
* **`city cluster.ipynb`** - Code for Fig. 5: analyze the characteristics of human mobility and CO<sub>2</sub> emissions in city clusters.
 
