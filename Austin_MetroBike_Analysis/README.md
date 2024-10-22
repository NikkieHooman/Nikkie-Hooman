# Austin MetroBike Analysis

## Project Overview

This project analyzes Austin MetroBike trip data to predict the attractiveness of different bike kiosks as a destination based on socio-economic factors, crime rates, and other demographic data. The dataset includes information on over 1.8 million bike trips recorded from 2014 to 2022, providing detailed insights into the travel behavior of MetroBike users in Austin, Texas. The analysis aims to help city planners and decision-makers understand the factors influencing bike kiosk usage, thus promoting micromobility as a sustainable transport option.

### Goals
1. **Predict Kiosk Attractiveness**: Understand what makes certain bike kiosks more attractive to riders.
2. **Feature Engineering**: Create new variables such as demographic factors, crime rate near kiosks, and trip-related metrics.
3. **Modeling**: Apply classification models to predict which bike kiosks are more likely to be used as a destination.
4. **Dimensionality Reduction**: Use PCA, t-SNE, and UMAP to reduce the number of features and visualize patterns in the data.
5. **Sensitivity Analysis**: Perform sensitivity analysis to guide city officials on actionable insights, such as focusing on reducing crime to increase ridership.

## Datasets Used

1. **MetroBike Trip Data** (2014-2022): Contains details about each trip such as duration, checkout/return kiosks, and membership type.
   - Download: [Austin MetroBike Kiosk Locations](https://data.austintexas.gov/dataset/Austin-MetroBike-Kiosk-Locations/qd73-bsdg/data)

2. **Demographic Data**: Data from the U.S. Census Bureau containing socioeconomic data of residents near bike kiosks.
   - Download: [Austin Demographic Data](https://data.census.gov/profile/Austin_city,_Texas?g=1600000US4805000)

3. **Geographic Data**: Latitude and longitude of each MetroBike kiosk and associated details.
   - Download: [Kiosk Locations](https://data.austintexas.gov/Transportation-and-Mobility/Austin-MetroBike-Kiosk-Locations/qd73-bsdg/data)

## Project Structure

### 1. Data Preparation
The data preparation stage includes loading, merging, and cleaning multiple datasets to ensure consistency and completeness. This step addresses missing values, formats data correctly, and transforms features for analysis.

#### Data Preparation Includes:
- **Data Loading**: Loading the MetroBike trips, demographic data, and geographical locations of the bike kiosks.
- **FIPS Code Matching**: Identifying which demographic zone (FIPS code) each kiosk falls into by matching their latitude and longitude with FIPS data using the FCC API.
- **Data Cleaning**: Handling missing values, removing irrelevant columns like 'Bike Type,' and subsetting the data for specific months for manageable analysis.
  
Notebooks:
- `01_Data_Preprocessing.ipynb`

### 2. Exploratory Data Analysis (EDA)
In this stage, various visualizations and correlation matrices are created to understand the relationships between factors like education levels, crime rates, age, and kiosk attractiveness.

#### Key Visualizations Include:
- **Correlation Matrix**: Displaying relationships between different factors, including education, crime rate, and racial diversity.
- **Distribution Plots**: Showing the distribution of features like population over 25, higher education levels, and crime rates in areas surrounding bike kiosks.
- **Bar Plots**: Visualizing the number of trips to various bike kiosks, grouped into "hot," "medium," and "cold" destinations based on trip volume.

Notebooks:
- `02_Exploratory_Data_Analysis.ipynb`

### 3. Feature Engineering
In this section, new features are engineered to enhance the prediction of kiosk attractiveness. These features are derived from demographic data, crime rates, and trip statistics.

#### Key Features:
- **Order (Kiosk Attractiveness)**: Kiosks are categorized into three groups based on the number of trips ending at that kiosk: 
   - 1: Cold Destinations
   - 2: Medium Destinations
   - 3: Hot Destinations
- **Crime Rate**: The number of crimes that occurred within a 5-minute walking distance of the kiosks.
- **Demographic Features**: Factors like percentage of population with higher education, racial diversity, and household income near each kiosk.

Notebooks:
- `02_Exploratory_Data_Analysis.ipynb`

### 4. Dimensionality Reduction
Since the dataset contains multiple features, dimensionality reduction techniques like PCA, t-SNE, and UMAP are used to visualize and better understand how features contribute to kiosk attractiveness.

#### Techniques:
- **PCA (Principal Component Analysis)**: Reduces data to two or three principal components while retaining key variance in the data.
- **t-SNE (t-Distributed Stochastic Neighbor Embedding)**: Preserves local structures and visualizes high-dimensional data.
- **UMAP (Uniform Manifold Approximation and Projection)**: Provides more accurate separation between attractive and less attractive kiosks by preserving both local and global data structures.

Notebooks:
- `04_Dimensionality_Reduction.ipynb`

### 5. Modeling and Classification
We use machine learning classification models to predict kiosk attractiveness based on various features.

#### Models Applied:
- **Random Forest**
- **Logistic Regression**
- **K-Nearest Neighbors (KNN)**

#### Model Evaluation:
- Models are evaluated based on accuracy, precision, recall, and F1 score.
- Sensitivity analysis is performed on factors like crime rate and demographic features to assess their impact on kiosk attractiveness.

Notebooks:
- `03_Modeling.ipynb`

### 6. Data Visualization
Key insights are visualized on an interactive map of Austin, showing the geographical distribution of kiosks and how demographic features affect their attractiveness.

- **Folium Maps**: Showing bike kiosk locations with color-coding based on attractiveness.
- **Trip Routes**: Visualizing the starting and ending points of the first 50 trips using geographical data.

Notebooks:
- `02_Exploratory_Data_Analysis.ipynb`
  
## How to Run the Project
Run the Jupyter notebooks in the following order:
01_Data_Preprocessing.ipynb
02_Exploratory_Data_Analysis.ipynb
03_Modeling.ipynb
04_Dimensionality_Reduction.ipynb


## Dependencies
Ensure you have these Python libraries installed:
```c 
pandas
numpy
matplotlib
seaborn
xgboost
scikit-learn
plotly
umap-learn
folium
```

## Results
- Correlation Analysis: We observed that kiosks located near areas with higher levels of education and racial diversity are more attractive to riders.
- Dimensionality Reduction: UMAP provided the clearest separation between kiosks of different attractiveness levels, indicating that our feature set is appropriate for clustering.
- Modeling: Random Forest and Logistic Regression provided good accuracy in predicting kiosk attractiveness, allowing city planners to prioritize kiosks for improvement.
- Geographical Insights: The map visualizations showed that kiosks near UT Austin were the most attractive, likely due to the high number of educated young people living in the area.


## Future Improvements
- Expand Dataset: Include more recent data or data from other cities to validate the model’s effectiveness.
- Advanced Modeling: Apply more advanced machine learning models like XGBoost to improve the prediction accuracy.
