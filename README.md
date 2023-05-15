# Car Sourcing with Data-Driven Segmentation
#### Revolutionize Car Sourcing with Data-Driven Segmentation: Maximize Your Investment with the Right Cars for the Right Markets.

1. [Project Overview](#ProjectOverview)
2. [Project Environment Info](#ProjectEnvironmentInfo)
3. [Python Libraries](#PythonLibraries)
4. [Dataset Information](#DatasetInformation)
5. [Methodology](#Methodology)
6. [Model](#model)
7. [Results](#results)

## Project Overview <a name="ProjectOverview"></a> 
This project represents my hackathon solution for [Microsoft Code Without Barriers Hackathon 2023](https://cwb2023.devpost.com/). My chosen problem statement for this hacathon is [Carsome Problem Statement](https://cwb2023.devpost.com/forum_topics/37295-carsome) 2: Data-driven Sourcing Strategy. Check out my [Hackathon Submission](https://devpost.com/software/car-dealers-segmentation?ref_content=my-projects-tab&ref_feature=my_projects).   

[Carsome](https://www.carsome.my/) is a leading online used car marketplace that streamlines the buying and selling process for individuals through its innovative platform. With a finite amount of sourcing budget, Carsome needs to optimize their sourcing strategy and identify the most valuable cars to purchase within their budget.   

Therefore, the **goal** of this project is to **create a robust cluster model** that can **effectively segment cars based on shared characteristics**.   

By leveraging data-driven insights, Carsome can make informed decisions on which cars to source and list, rather than relying on a generic approach.

## Project Environment Info <a name="ProjectEnvironmentInfo"></a>
- Kernel used: Python 3.8 AzureML   
- Compute Instance used: 2 Cores, 16 GB (RAM), 20 GB (Disk), $0.13/hr 

## Python Libraries <a name="PythonLibraries"></a>
- numpy
- pandas
- matplotlib
- seaborn
- sklearn
- kmodes.kprototypes
- kneed
- lightgbm
- shap
- tqdm

## Dataset Information <a name="DatasetInformation"></a>
[Dataset](https://github.com/Alicia2203/CarsomeCarsSegmentation/blob/main/Brand_Model_CarType.csv)

-   **`lead_id`**   
	- unique identifier for sellers who opt to sell their car. 
	- In other words, the car that dealers are bidding for in the auction 
-   **`marketplace_id`**    
	- unique identifier for the auction session 
-   **`marketplace_car_id`**    
	- the unique identifier for a car that goes to a auction session.   
	- Eg. if the same lead goes to 3 auctions maybe because they weren't able to sell the car in the previous auctions, there will be 3 of the same lead_id but different marketplace_car_id. 
-   **`dealer_id`**    
	- unique identifiers for individual dealers bidding for the car 
-   **`used_dealer_company_id`**    
	- unique identified for the company the dealer is tied to? Eg, 3 dealers can be from 1 company (have the sample dealer_id). 
-   **`car_brand`**  
	- The brand of the car (e.g. Honda, Suzuki)
-   **`car_model`**
	- The model of the car (e.g. Freed, City, Ertiga)
-   **`car_variant`**
	-  The variant of the car(e.g. S, GL, VTEC)
-   **`car_engine`**
	- The size of the car's engine (e.g. 1.5, 1.4)
-   **`car_year`**
	- The year the car was manufactured
-   **`car_transmission`**   
	- The type of transmission the car has (e.g. Auto, Manual)
-   **`reserveprice`**   
	- the starting bid price of the car in an auction   
	- The reserve price for the car listing (i.e. the minimum amount the seller is willing to accept)

## Methodology <a name="Methodology"></a>
1. **Business understanding**:     
To understand the business problem that needs to be solved, which was to segment cars based on their features to better understand their value and demand in the market.

2. **Data understanding**:   
Exploratory Data Analysis

3. **Data preparation**:    
removing duplicate rows, dealing with missing values. deriving features, selecting relevant features, and scaling numerical data for model input

4. **Modeling**:    
k-prototype was selected as our cluster model. Elbow Plot and KneeLocator was used in finding the optimal number of clusters

5. **Model evaluation**:    
Cluster Profilling

## Model <a name="model"></a>
**K-prototype**    
K-prototype is a clustering algorithm that combines the K-means algorithm for numerical data and the K-modes algorithm for categorical data. It is particularly suitable for this project as our dataset contains numerical and categorical data types.

Elbow Plot and KneeLocator was used in finding the optimal number of clusters. 

Both plot shows that 4 is the optimal cluster number


## Results <a name="Methodology"></a>
### Cluster Distribution
![Cluster Distribution](https://github.com/Alicia2203/CarsomeCarsSegmentation/blob/main/cluster%20dist.png)

- Cluster 0 - 14217 (46.8%)  
- Cluster 2 - 6670 (22%)
- Cluster 1 - 6409 (21.1%)
- Cluster 3 - 3085 (10.2%)

![clusterprofile](https://github.com/Alicia2203/CarsomeCarsSegmentation/blob/main/Cluster%20Profile.png)

### Cluster Profilling
#### **Cluster 0 - Newer Cheaper Cars**:   
This cluster comprises the largest percentage of cars (46.8%) where represented cars are predominantly SUVs, followed by MPVs and hatchbacks, and with automatic transmission and a medium price tier. The median reserve price is 119,500,000, which is lower than the median reserve prices of Clusters 2 and 3. The median age of the cars is 6 years, and ranging from 2 to 12 years. This cluster also has the lowest median car engine size at 1.5. 

**_Recommendation_**: Carsome could consider targeting this cluster for buyers who are looking for low-to-mid, relatively new, SUVs and MPVs. 

#### **Cluster 1 - Older Cheapest Cars**:   
This cluster has the second-highest number of cars, and the majority of them are MPVs, followed by sedans and hatchbacks, with both automatic and manual transmission options. The median reserve price is 65,000,000, which (like Cluster 0) is significantly lower than the median reserve prices of Clusters 2 and 3. The median car age is 12 years, which is the highest among all clusters. The median age of the cars in this cluster is 12 years, and the engine size is 1.5. This cluster has a relatively balanced distribution of transmission types, with slightly more automatic cars. 

**_Recommendation_**: Carsome could consider targeting this cluster for buyers who are looking for more budget-friendly cars, regardless of car age, car engine, car type and car transmission. 

#### **Cluster 2 -  Powerful Mixed Cars**:   
This cluster represents cars that are predominantly SUVs and MPVs, with automatic transmission and a medium to high price tier. The median reserve price is 140,000,000, which is the highest among all clusters. The median age of the cars in this cluster is 11 years, which is higher than Cluster 0 but lower than Cluster 1. This cluster also has the largest median car engine size at 2.4. 

**_Recommendation_**: Carsome could consider targeting this cluster for customers who prefer SUVs, MPVs and other more powerful cars with automatic transmission, larger engines and are willing to pay a higher price for a relatively newer car.

#### **Cluster 3 - Newer High End Cars**:   
This cluster has the lowest number of cars. It represents cars that are predominantly MPVs and SUVs, with automatic transmission and a high price tier. The median reserve price is 370,000,000, which is significantly higher than the median reserve prices of Clusters 0 and 1. The median car age is 5 years, which is the lowest among all clusters. This cluster also has a high proportion of automatic cars and luxurious brands. 

**_Recommendation_**: Carsome could consider targeting this cluster for buyers who are looking for high-end, relatively new MPVs and SUVs from luxurious brands.

### SHAP Plot
- To understand which features are contributing the most to the separation of the clusters.
![SHAP](https://github.com/Alicia2203/CarsomeCarsSegmentation/blob/main/shap.png)

-   Cluster 0 (Class 0) is primarily characterized by cars with smaller engines and younger ages. This suggests that customers who are looking for more affordable cars may be drawn to this cluster.
-   Cluster 1 (Class 1) is characterized by older cars, regardless of engine size or car type. This suggests that customers who are looking for cheaper, more budget-friendly options may be drawn to this cluster.
-   Cluster 2 (Class 2) is primarily characterized by cars with larger engines, with a mix of car types. This suggests that customers who are looking for more powerful cars or specific car types may be drawn to this cluster.
-   Cluster 3 (Class 3) is characterized by high reserve prices, which suggests that these cars are more expensive and may appeal to customers who are looking for luxurious or high-end vehicles.

## Notebook
[Code in Notebook](https://github.com/Alicia2203/CarsomeCarsSegmentation/blob/main/CWB%20-%20Carsome-Problem%202%20-%20Cars%20Segmentation.ipynb)
