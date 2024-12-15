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

<img src="https://github.com/user-attachments/assets/0b694606-9233-4686-a692-51f320d2fe08" alt="missingvalues" width="100"/>

- Data Distribution Visualization
  - Selected relevant numerical columns to analyze.
  - Created side-by-side histograms for multiple features to visualize their distributions.
  - Customized histograms by adjusting spines for a cleaner visual presentation.

![freq](https://github.com/user-attachments/assets/f342a7cf-273c-4442-8ff3-505d007a5d58)


 --- 
### 2. Standardization and Clustering Analysis
- Applying Standardization
  -	Utilized StandardScaler to standardize the numeric columns, ensuring that each feature has a mean of 0 and a standard deviation of 1.
  -	Replaced the original numeric columns in the DataFrame with their standardized values.

- Elbow Method for Optimal Clusters
  -	Implemented the elbow method to determine the optimal number of clusters for KMeans clustering.
  -	Collected inertia values for cluster numbers ranging from 1 to 10.
  -	Plotted the elbow curve to visualize the relationship between the number of clusters and inertia, helping to identify the "elbow" point for optimal clustering.

![elbow](https://github.com/user-attachments/assets/91a26950-3b9b-44f6-a2da-f2d504701d85)

> Interpretation: The elbow is around k=3. After this point, the inertia decreases at a much slower rate, which suggests that using 3 clusters would be the optimal choice for the data.

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

![pca](https://github.com/user-attachments/assets/b1314dd1-bd3f-4434-8647-7685b87a1849)


 --- 
### 4. Clustering and Principal Component Analysis (PCA) Visualization
- Visualization of Mean Values
  -	Created bar charts to visualize the mean values of specific features (exports, health, imports, income, inflation, life_expec, total_fer, and gdpp) across the identified clusters (Cluster 1, 2, and 3).
  -	Generated bar charts for the mean of the first principal component (PC1) by cluster to visualize differences in the PCA results across clusters.

<img src="https://github.com/user-attachments/assets/6826ee31-5091-4ec4-983a-e363b28140c5" alt="missingvalues" width="700"/>

  - Interpretation:
    - Cluster 1 (Mean PC1 = 0.1752): Countries in Cluster 1 are relatively balanced across the features most influential in PC1, such as life expectancy, income, and exports
    - Cluster 2 (Mean PC1 = -2.4346): Countries in Cluster 2 are characterized by lower values of features positively correlated with PC1 (e.g., income, life expectancy, exports) and higher values of features negatively correlated with PC1 (e.g., child mortality, fertility rate, inflation)
    - Cluster 3 (Mean PC1 = 2.7698): Countries in Cluster 3 exhibit higher values for features positively correlated with PC1, such as income, life expectancy, exports, and health expenditures, and lower values for features negatively correlated with PC1, like child mortality and fertility rate

<img src="https://github.com/user-attachments/assets/6fad93f0-0ec8-4208-902b-cf4168da3a32" width="700"/>
<img src="https://github.com/user-attachments/assets/d2426c44-b3d7-4107-843a-c94a8895f82d" width="700"/>

- Interpretation:
  - Cluster 1 represents countries with moderate levels of exports, imports, and income. These countries have moderate health metrics, lower fertility rates, and GDP, but higher life expectancy. PC1 is slightly positive, indicating moderate overall economic and health development.
    - **Cluster 1 represents moderately developed countries with balanced features**
  - Cluster 2 represents countries with low exports, imports, income, and GDP. These countries also have low life expectancy and high fertility rates. High inflation is present, but overall, this cluster indicates countries with poorer economic and health conditions, reflected in the very low PC1 value.
    - **Cluster 2 represents underdeveloped countries with low economic and health indicators**
  - Cluster 3 represents countries with high exports, income, health, life expectancy, and GDP. These countries have low fertility rates and inflation, which is indicative of highly developed economies and societies. The very high PC1 value reflects the positive contributions of these features to the overall development
    - **Cluster 3 represents highly developed countries with strong economic and health indicators**

- Output of Mean Values
  -	Printed mean values of the specified features and mean PCA1 values for each cluster for detailed analysis and interpretation.

![mean3](https://github.com/user-attachments/assets/57dd9ff7-9e44-4be4-97a8-78f24976f052)


 --- 
### 5. Cluster Analysis Visualization: Scatter Plots of Key Indicators
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

## Outcome
