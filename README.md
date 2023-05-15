# Car Sourcing with Data-Driven Segmentation
#### Revolutionize Car Sourcing with Data-Driven Segmentation: Maximize Your Investment with the Right Cars for the Right Markets.

1. [Project Overview](#ProjectOverview)
2. [Project Environment Info](#ProjectEnvironmentInfo)
3. [Python Libraries](#PythonLibraries)
4. [Dataset Information](#DatasetInformation)
5. [Data Exploration](#data)
6. [Implementation](#model)
7. [Results](#results)

### Project Overview <a name="ProjectOverview"></a> 
This project represents my hackathon solution for [Microsoft Code Without Barriers Hackathon 2023](https://cwb2023.devpost.com/). My chosen problem statement for this hacathon is [Carsome Problem Statement](https://cwb2023.devpost.com/forum_topics/37295-carsome) 2: Data-driven Sourcing Strategy. Check out my [Hackathon Submission](https://devpost.com/software/car-dealers-segmentation?ref_content=my-projects-tab&ref_feature=my_projects).   

[Carsome](https://www.carsome.my/) is a leading online used car marketplace that streamlines the buying and selling process for individuals through its innovative platform. With a finite amount of sourcing budget, Carsome needs to optimize their sourcing strategy and identify the most valuable cars to purchase within their budget.   

Therefore, the **goal** of this project is to **create a robust cluster model** that can **effectively segment cars based on shared characteristics**.   

By leveraging data-driven insights, Carsome can make informed decisions on which cars to source and list, rather than relying on a generic approach.

### Project Environment Info <a name="ProjectEnvironmentInfo"></a>
- Kernel used: Python 3.8 AzureML   
- Compute Instance used: 2 Cores, 16 GB (RAM), 20 GB (Disk), $0.13/hr 

### Python Libraries <a name="PythonLibraries"></a>
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

### Dataset Information <a name="DatasetInformation"></a>
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

### Methodology <a name="PythonLibraries"></a>
1. **Business understanding**:     
To understand the business problem that needs to be solved, which was to segment cars based on their features to better understand their value and demand in the market.

2. **Data understanding**:
Exploratory Data Analysis

3. **Data preparation**: 
   removing duplicate rows, dealing with missing values. deriving features, selecting relevant features, and scaling numerical data for model input

4. **Modeling**: k-prototype was selected as our cluster model. Elbow Plot and KneeLocator was used in finding the optimal number of clusters

5. **Model evaluation**: Cluster Profilling

### Results

