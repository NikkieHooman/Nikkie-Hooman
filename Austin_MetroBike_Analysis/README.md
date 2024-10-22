# Austin MetroBike Analysis
## Project Overview
This project analyzes Austin MetroBike trip data to predict the attractiveness of different bike kiosks based on socio-economic factors, crime rates, and other demographic data. The analysis includes data preprocessing, visualizations, feature engineering, and modeling techniques like PCA, t-SNE, and UMAP to study trends in micromobility usage in Austin, TX.

## Project Structure
1. **Data Preparation**: 
   - Clean and merge multiple datasets (trip data, demographic data, and geographic data).
   - Fill in missing data and transform features.
   - Subset data for further analysis.

2. **Exploratory Data Analysis**: 
   - Correlation analysis to understand relationships between socioeconomic factors and bike trip destinations.
   - Visualize distribution of factors like higher education, age, racial diversity, etc.

3. **Feature Engineering**: 
   - Create new variables such as kiosk attractiveness (`Order`), trip duration, crime rate around kiosks, and demographic factors.

4. **Dimensionality Reduction**: 
   - Use PCA, t-SNE, and UMAP to reduce the number of features and visualize the results.

5. **Modeling**: 
   - Predict the attractiveness of bike kiosks using Random Forest, Logistic Regression, and KNN.

## How to Run the Project
1. Clone the repository:  
