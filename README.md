# GEOG5990M
# Project Overview
Urban green spaces are very important in the daily lives of residents. However, the green spaces distribution may be affected by the economic situation. This may result in poorer groups having less access to green space resources. This study combines the Leeds 2021 deprived households, the public green space data and the administrative boundary data of Leeds for spatial data analysis. The aim is to explore the relationship between them and and provide support for a more equitable allocation of urban green space resources. This project is divided into three main parts: data exploration and cleaning, K clustering modeling and results.

# Data Exploration and Cleaning
## Data Description
This study used three datasets which from public data platforms.
Households_Deprivation_Leeds_2021Census_LSOA.xlsx
This is a data on the deprivation dimension of family poverty for Leeds Lower Super Output Areas (LSOA) 2021 from the Office for National Statistics (Nomis) in Excel file format. The poverty dimension variable is a direct measure of poverty, while households in three or four dimensions of it can be considered to disadvantaged socioeconomic status (ONS, 2022).
Link: https://www.nomisweb.co.uk/default.asp

LSOA2021_Leeds.shp
This is 2021 LSOA Leeds Boundary vector data in shapefile format from the ONS Open Geography Portal for spatial geographic analysis. 
Link: https://geoportal.statistics.gov.uk/datasets/2bbaef5230694f3abae4f9145a3a9800_0/explore?location=52.609880%2C-2.489483%2C6.90

GB_GreenspaceSite.shp
This is open green space data in shapefile format from Ordnance Survey data centres and contains all public green spaces in the UK.
Link: https://osdatahub.os.uk/downloads/open/OpenGreenspace


## Data Exploration
The raw datasets need to go through exploration and preprocessing to ensure the quality, select appropriate variables for subsequent analysis, and provide support for subsequent operations.

Configuration Work Environment
Access data files through the associated Google Drive to meet subsequent analysis needs. Then install necessary Python libraries and packages,and read the datasets.

## Preliminary Exploration
Exploratory analyses can help identify data quality issues. It checks on the data are completed by using a range of data exploration functions. This provides an understanding of the distribution, completeness and potential outliers of the dataset. It can also inform subsequent data cleaning, modelling and visualisation decisions.Overall, the datasets can support repeatable analyses due to the structure are clear and complete.

## Data Preprocessing
Poverty tables and boundary data are merged to allows socio-economic and spatial attributes for each LSOA. It can help subsequent analysis, mapping and modelling of derived variables and visualisation of spatial distribution.

The Coordinate Reference Systems (EPSG:27700) of the two spatial data are confirmed consistency. This avoids geometric distortion and spatial overlay errors (Chrisman, N.R. 1987). 

OS Open Greenspace covers the UK and needs to be clipped to the Leeds boundary, which name ’greenspace_leeds’. It can ensure that subsequent calculations and analyses are made for the study area. The greenspace polygons in ’greenspace_leeds’ should match to LSOA polygons accurate.

Standardized percentage variables for spatial analysis at the small area level can reveal spatial patterns of poverty. Four variables are created to build a link between social and environment: ‘Severe_Deprivation_Households’, ‘Deprivation_Percentage’, ‘lsoa_area_m²’, ‘greenspace_percentage’


Besides, delete old area fields and validate dtypes before merging again to avoid duplicate fields and type errors and improve code stability and reproducibility. 

The histogram showing the distribution of data according to the level of poverty and the total number of families in Leeds presents a more extreme situation for multi-dimensional deprived families, suggesting that subsequent analysis should be converted to proportional indicators. 

The spatial maps can be used to support data cleaning through visual comparison. First, the visualization and superposition of green space data and Leeds boundary data will intuitively compare the data range and support the rationality of cropping. Second, it verifies the CRS consistency.

# K-means clustering
This study uses the K-means clustering model to divide the LSOA areas of Leeds into groups with different characteristics based on ‘the proportion of families in severe poverty’ and ‘green land coverage’. This model is a reasonable choice for this study because it is computationally efficient and intuitive. It can reveal the spatial relationship between social vulnerability and resource accessibility. 

# Visualization results
## Non-spatial Visualization
This scatter diagram uses Severe Deprivation Rate (%) as the vertical axis and Greenspace Coverage (%) as the horizontal axis. The different colors are used to represent K-means clustering results based on clustering labels. The distribution of points does not show a clear linear trend. 

## Spatial Visualization
This figure visually presents the spatial relationship between areas of different poverty levels and the distribution of green spaces by means of spatial superposition. The spatial pattern can be observed effectively by overlaying the green space layer on the LSOA area, which is coded according to the ten equal parts.

