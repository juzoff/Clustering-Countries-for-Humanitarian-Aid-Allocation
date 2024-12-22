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
  -	Income vs. Life Expectancy: 
The scatter plot below shows the relationship between income and life expectancy, grouped by development level. Highly developed countries (Cluster 3) are positioned in the top-right quadrant, reflecting high income and life expectancy. Underdeveloped countries (Cluster 2) are located in the bottom-left quadrant, indicating low income and shorter life expectancy. Moderately developed countries (Cluster 1) are placed in the middle, exhibiting characteristics between the two extremes. This visualization highlights how income levels are closely linked with life expectancy, with more affluent countries generally enjoying longer lifespans.

 ![incomele](https://github.com/user-attachments/assets/1bac958d-5bc1-41b0-8b81-453bbbd3b032)

  
  -	Exports vs. Imports: The scatter plot below illustrates the relationship between imports and exports, grouped by development level. Highly developed countries (Cluster 3) show higher exports (mean 0.6451) and imports (mean 0.1906), reflecting robust international trade and export-driven economies. Underdeveloped countries (Cluster 2) are clustered at lower levels of both exports (mean -0.4375) and imports (mean -0.1892), indicating limited trade activity. Moderately developed countries (Cluster 1) exhibit near-neutral averages for exports (mean -0.0317) and imports (mean 0.0242), suggesting balanced but less dynamic trade activity compared to highly developed nations.

![impexp](https://github.com/user-attachments/assets/05d51469-599c-4663-918d-57279f115ed5)


  -	GDP Per Capita (gdpp) vs. Inflation: The scatter plot below examines the relationship between GDP per capita (gdpp) and inflation across development clusters. Highly developed countries (Cluster 3) show high GDP per capita (mean 1.6160) and low inflation (mean -0.4849), indicative of stable and prosperous economies. Underdeveloped countries (Cluster 2) have lower GDP per capita (mean -0.6042) and higher inflation (mean 0.4021), reflecting economic instability and challenges. Moderately developed countries (Cluster 1) fall between these extremes, with moderate GDP per capita (mean -0.3545) and near-neutral inflation (mean -0.0172).

![gdp](https://github.com/user-attachments/assets/6ea0e025-c571-47e6-a598-5519ecd45c51)


  -	Total Fertility Rate (total_fer) vs. Life Expectancy: The scatter plot illustrates the relationship between total fertility rate (total_fer) and life expectancy (life_expec) by development cluster. Highly developed countries (Cluster 3) show low fertility rates (mean -0.7919) and high life expectancy (mean 1.0796), reflecting a focus on healthcare and quality of life. Underdeveloped countries (Cluster 2) have higher fertility rates (mean 1.3649) and lower life expectancy (mean -1.2822), which can be attributed to higher child mortality and limited healthcare resources. Moderately developed countries (Cluster 1) exhibit moderate fertility rates (mean -0.4243) and slightly higher life expectancy (mean 0.2547), reflecting ongoing improvements in health and living conditions.

![neww](https://github.com/user-attachments/assets/716ddfd5-1f1e-4666-95b3-a4b30b61f5af)


  -	Health vs. Income: The scatter plot illustrates the relationship between income and health across development clusters. Highly developed countries (Cluster 3) exhibit a strong positive correlation with high income (mean 1.4842) and better health outcomes (mean 0.7274), reflecting better healthcare infrastructure and higher standards of living. Underdeveloped countries (Cluster 2) demonstrate lower income levels (mean -0.6869) and moderate health outcomes (mean -0.1560), indicating that economic challenges hinder improvements in health. Moderately developed countries (Cluster 1) show a moderate positive relationship between income (mean -0.2518) and health (mean -0.2245), suggesting that while income levels are improving, there are still significant health challenges to overcome.


![in](https://github.com/user-attachments/assets/7cae5732-8b1c-4ac4-b72f-ccc156cbe452)


--- 
### 6. Conclusion - Data Filtering and Clustering Analysis of the Chosen Cluster (Cluster 2 - underdeveloped countries with low economic and health indicators)

- Filtering and Displaying the Chosen Cluster
  -	Filtered the dataset to isolate and display only the countries that belong to Cluster 2 (underdeveloped countries) for focused analysis.
  -	Used the display() function to present the filtered data in a clear format for review.

![final](https://github.com/user-attachments/assets/72d80c23-b79b-40c8-a14c-e119f3460902)
![final2](https://github.com/user-attachments/assets/bc73138e-20d4-484c-b8c0-1f90ed640ec5)

---

### 7. Outcome

![download (1)](https://github.com/user-attachments/assets/abbbed1a-9ebe-473c-a1af-ad00a1b68f38)


Identifying Countries in Direst Need:
- Cluster 2 (Red dots) represents underdeveloped countries. These countries exhibit low socio-economic and health indicators, making them the most vulnerable and in urgent need of support.
- By identifying these countries, HELP International can focus its resources on regions where the impact of aid will be the greatest.

Strategic Allocation of Resources:
- With a limited budget of $10 million, resources can be distributed effectively by prioritizing countries in Cluster 2, ensuring that aid directly targets the areas with the most significant gaps in basic amenities, healthcare, and poverty relief.

​Clustering Justification with Data:
​- Cluster 2’s tight grouping on the left of the chart (PC1 = -3 to 0) demonstrates consistently poor socio-economic and health indicators, with low PC1 and PC2 values.
- These countries are likely struggling with severe poverty, limited access to healthcare, and poor living conditions, aligning perfectly with HELP International’s mission.

​Explanation of PC1 and PC2:
- ​PC1 (X-Axis):
  - Captures the most variance in the data.
  - Higher values represent wealthier, more developed countries (e.g., income, GDP, life expectancy).
  - Lower values represent poorer, underdeveloped countries (e.g., high child mortality, low income).
- PC2 (Y-Axis):
  - Captures the second most variance, orthogonal to PC1.
  - Higher values indicate stronger trade (exports/imports) and better life expectancy.
  - Lower values suggest poorer health outcomes and limited economic integration.

​Clusters:
- Cluster 2 (Red): Low PC1 and PC2 values, underdeveloped countries.
- Cluster 3 (Green): High PC1, moderate-high PC2, highly developed countries.
- Cluster 1 (Yellow): Moderately developed countries, variability in both components.

---

### 8. Dashboard Insights for Humanitarian Aid Allocation: Analyzing Development Across Clusters and Highlighting Underdeveloped Countries

- After accomplishing the clustering analysis and identifying underdeveloped countries (Cluster 2) as the most vulnerable, I recognized the importance of creating visualizations to effectively communicate these findings. To achieve this, I developed two dashboards:
  - Comprehensive Cluster Dashboard: This dashboard visualizes the socio-economic and health disparities across all three clusters, providing a holistic view of global development patterns.
  - Focused Underdeveloped Countries Dashboard: This dashboard highlights Cluster 2 (Underdeveloped Countries), presenting key metrics such as fertility rates, health expenditures, and inflation. It provides actionable insights to prioritize aid to regions where HELP International's resources can have the greatest impact. Additionally, it enables a detailed analysis to determine which countries within this cluster should receive aid first, ensuring the most effective allocation of resources.
- By combining analytical rigor with impactful visualizations, I demonstrated how data-driven insights, when presented effectively, can guide strategic decision-making and amplify the impact of humanitarian aid.

### Comprehensive Cluster Dashboard:
![main](https://github.com/user-attachments/assets/92716aaf-9931-4ed9-a7f1-637a7b2381e5)

### Focused Underdeveloped Countries Dashboard:
![underdeveloped](https://github.com/user-attachments/assets/9593ae34-b580-4d08-b740-0bfb5e8ccec3)
