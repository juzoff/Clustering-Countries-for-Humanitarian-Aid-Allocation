# Clustering-Countries-for-Strategic-Aid-Allocation
This project involved using unsupervised learning techniques, specifically clustering, to categorize countries based on socio-economic and health factors that influence their overall development. The goal was to help HELP International, an NGO focused on humanitarian aid, strategically allocate $10 million in funding by identifying countries most in need of support. As a data scientist, I was responsible for analyzing the data to suggest which countries should receive priority attention from the organization.

## Components:

### 1. Data Exploration and Initial Insights
- Loading Data, Initial Data Display
  - Loading Data: Imported the CSV file containing country data into a pandas DataFrame.
  - Initial Data Display: Displayed the first few rows of the DataFrame to understand the structure and content of the data.
- Missing Values Check
  - Checked for missing values in the dataset.
  - Displayed the number of missing values for each column to assess data quality.
- Data Distribution Visualization
  - Selected relevant numerical columns to analyze.
  - Created side-by-side histograms for multiple features to visualize their distributions.
  - Customized histograms by adjusting spines for a cleaner visual presentation.

 --- 
### 2. Standardization and Clustering Analysis
- Applying Standardization
  -	Utilized StandardScaler to standardize the numeric columns, ensuring that each feature has a mean of 0 and a standard deviation of 1.
  -	Replaced the original numeric columns in the DataFrame with their standardized values.

- Elbow Method for Optimal Clusters
  -	Implemented the elbow method to determine the optimal number of clusters for KMeans clustering.
  -	Collected inertia values for cluster numbers ranging from 1 to 10.
  -	Plotted the elbow curve to visualize the relationship between the number of clusters and inertia, helping to identify the "elbow" point for optimal clustering.

- Performing KMeans Clustering
  -	Executed KMeans clustering with the number of clusters set to 3 on the standardized data.
  -	Assigned cluster labels to the DataFrame, adjusting the labels to start from 1 for better interpretation.

- Creating Cluster DataFrame
  -	Created a new DataFrame (country_cluster) containing the country names and their corresponding cluster labels for verification
 
 --- 
### 3. Conducting Principal Component Analysis (PCA)
- Applying PCA
  -	Initialized the PCA model and fitted it to the standardized numeric data to reduce dimensionality.
  -	Transformed the data into principal components and created a new DataFrame containing these components.

- Displaying PCA Results
  -	Displayed the DataFrame (Countrydata2) which includes the principal components alongside non-numeric data.

- Reducing to Specific PCA Components
  -	Initialized a new PCA model to extract exactly 4 principal components.
  -	Created a new DataFrame (Countrydata4) for these 4 components while including non-numeric data as well.
- Analyzing PCA Loadings
  -	Retrieved the weights (loadings) for each feature across the first four principal components, providing insights into how each feature contributes to the components.
  -	Displayed the PCA loadings to summarize the contribution of the original features to the transformed principal components.

 --- 
### 4. Clustering and Principal Component Analysis (PCA) Visualization
- Visualization of Mean Values
  -	Created bar charts to visualize the mean values of specific features (exports, health, imports, income, inflation, life_expec, total_fer, and gdpp) across the identified clusters.
  -	Generated bar charts for the mean of the first principal component (PC1) by cluster to visualize differences in the PCA results across clusters.
- Output of Mean Values
  -	Printed mean values of the specified features and mean PCA1 values for each cluster for detailed analysis and interpretation.

 --- 
### 5. Clustering and Principal Component Analysis (PCA) Visualization
- Visualization of Key Relationships
  -	Created scatter plots to visualize relationships between key socioeconomic indicators and their variations by cluster.
- Scatter Plot Analyses using Seaborn
  -	GDP vs Life Expectancy: Illustrated the relationship between GDP per capita and life expectancy, highlighting clusters for comparative analysis.
  -	Exports vs Fertility Rate: Analyzed the interaction between exports (as a percentage of GDP) and total fertility rate, using cluster differentiation.
  -	Income vs Child Mortality: Explored the correlation between income per capita and child mortality rates, categorized by cluster.
  -	Inflation vs GDP: Examined the relationship between inflation percentages and GDP per capita, colored by cluster membership.
  -	Health Expenditure vs Life Expectancy: Provided insights into how health expenditure (as a percentage of GDP) relates to life expectancy across different clusters.

 --- 
### 6. Conclusion - Data Filtering and Clustering Analysis of the Chosen Cluster
- Filtering and Displaying the Chosen Cluster
  -	Filtered the dataset to isolate and display only the countries that belong to Cluster 2 for focused analysis.
  -	Used the display() function to present the filtered data in a clear format for review.

