# Practical-Application-2
# What drives the price of a Car?

# Overview
This is a practical application problem to identify factors that help drive the price of a used car. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure the speed of processing. Goal is to understand what factors make a car more or less expensive. As a result of analysis, clear recommendations are provided to used car dealerships with insights to what consumers value in a used car.

To analyze the factors that influence car prices and provide recommendations to a used car dealership, we'll follow the CRISP-DM (Cross-Industry Standard Process for Data Mining) framework. This approach will help us systematically address the problem and derive valuable insights.

# Business Understanding
The primary objective of this "Price of a car" practical application is to identify the factors that make a car more or less expensive in the used car market, and develop a model to help car dealers understand what factors consumers value in a used car. This understanding will help the dealership make informed decisions about inventory acquisition and pricing strategies.

# Executive Summary & Recommendations
Based on the analysis, below are the key findings will help dealership make informed decisions about inventory acquisition and pricing strategies

- Stock vehicles in the $5,000 - $25,000 range to match customer demand. Most competitive price range 
- Prioritize low-mileage cars (<100K miles), as they retain higher value.
- Focus on popular manufacturers (Toyota, Audi, Ford) for better resale value.
- Offer SUVs & pickup trucks, as they have strong resale value.
- Consider more hybrid & electric models, given their premium pricing.
- On the higher end, luxury models or rare vehicles can significantly raise the maximum price to $100,000+. Good idea to plan a couple of luxury car sales each quarter targeting the luxury market for increased profitability and try being a new entrant to the luxury market.
- Key features that drive price (+vely/-vely) of an used car are manufacturer, fuel type, title_status, type, condition. These features make car more or less expensive in the used car market
- Positive price impact
Manufacturer (Ferrari, Tesla, Ashton Martin, Porsche), fuel type (Diesel), title (Lien), type (pickup), condition (like new)
- Negative price impact
Manufacturer (Fiat, Mitsubishi, Kia, Nissan, Chrysler), fuel type (Electric), title (parts only), type (bus, hatchback), condition (no/low maintenance)

# Next Steps & Recommendations

As an immediate next step as a car dealer, you can use the above Executive summary, key insights to make informed decisions about inventory acquisition and pricing strategies. Moving futher, we can look at improving the model performance (from current 61%) to higher predictions (80-90%) for used car pricing.

**Note: **
- Typical ML models for car price prediction achieve 60%-90%
- 100% → Perfect Model (which IMO, is not attainable due to price variability nature of used car prices, market nuances, data limitations, ML model constraints)
- 0% → Model performs no better than predicting the mean price

We can improve the model performance using the following for better predictions

- Perform discovery of additional vehicles data set and identify new features (market trends, seller type, accident history, maintenance records, recalls etc)
- Gather additional vehicle data (size and volume), including location/demography based, consumer behavior while selecting used cars
- Use of dynamic pricing data from real-time market listings from used car market (carmax, carvana, edmunds)
- Encode categorical variables more effectively (One Hot Encoding)
- Feature scaling - Normalize odometer and price using MinMaxScaler or StandardScaler for models like Linear Regression
- Try to use gradient boosting technique for increased price prediction of used cars
- Use of hyperparameters and hyperparameters tuning using GridSearchCV

# Data Preparation
Analyzed the dataset to understand its structure and key features. Then, cleaned and prepared the data, performed exploratory data analysis (EDA), and identified factors influencing used car prices.

# Steps: Data Cleaning and Preparation
- Reviewed vehicles information (id, region, price, year, model, cyliners, odometer etc)
- Checked the summary statistics of price, year, and odometer. Identified unique and missing values.
- Collected descriptive statistics of categorical variables (cylinders, fuel, title_status, transmisson, VIN, drive, size, type, paint_color_state)
- Cleaned the data (handling missing values, removing duplicates)
- Removed ID, VIN
- Removed regio, model, state categorical columns with large unique values
- Removed size as it had large amount of missing data
- Dropped duplicate rows 
- Converted data type of cyliner to a numerical value
- Removed outliers (price, odometer, year) colums

# Key findings
* The `price, odometer and year` columns have a wide range of data. There is a vehicle with a `price max of 3 billion`, and odometer readings of `1M`. Both the odometer reading of 1M miles and 3Billion price for an individual car (even antique) looks unreasonable and an outlier. For the purposes of this analysis we will need to `treat outliers` (odometer readings about 500k and prices above 100k)

### * Categorical variables: The columns `region`, `manufacturer`, `model`, and `state` have a large number of unique values, requiring an appropriate strategy for treatment.
* VIN numbers: There are only 265838 unique VIN numbers in a dataset of 426880 observations, indicating possible duplicate entries.
* Missing values: The columns `condition`, `cylinders`, `VIN`, `drive`, `size`, `type`, and `paint_color` have more than 25% missing values.
* The `price, odometer and year` columns have a wide range of data. There is a vehicle with a `price max of 3 billion`, and odometer readings of `1M`. Both the odometer reading of 1M miles and 3Billion price for an individual car (even antique) looks unreasonable and an outlier. For the purposes of this analysis we will need to `treat outliers` (odometer readings about 500k and prices above 100k)

# Exploratory Data Analysis (EDA) - Process & Key Insights
Below section lists the EDA process executed (on the vehicles.csv dataset) and key findings. The plots are attached in the separate document attached.

- Right-skewed distribution with most prices concentrated between $5,000 and $25,000 - Used car prices typically follow a right-skewed distribution, meaning most cars are priced on the lower end, while a few high-end models drive up the maximum price range. The median price is often much lower than the mean due to expensive outliers.

- Identified outliers (extremely cheap listings, luxury vehicles). Some listings have extremely low prices (e.g., $0, $1, or a few hundred dollars) to max $3B. Required outlier treatment

- Found median price significantly lower than the mean, indicating a few high-priced vehicles impact the average.

- Key factors influencing price
  - Year - Newer cars tend to be more expensive, with a steep price drop for cars over 10 years old.
  - Mileage (Odometer) - Higher mileage correlates with lower price, especially beyond 150K miles.
  - Condition - Excellent and Like New cars command high prices 
  
  - Correlation of price wrt odometer, year and cylinders
  - Price and Odometer are negatively correlated (-0.41). Higher the odometer reading, lower the price
  - Price and years are positively correlated (0.29). Current or recent year cars are priced higher than old cars
  - Positive correlation between price and cylinders (0.25). Cars with higher number of cyclinders attracts more price. Condition also plays a vital role in price. Like new condition attracts high price

  - Condition/maintenance of the vehicle has a positive impact on price. Well maintained vehicles attract better price when compared to similar cars with same/similar odometer reading.
 
  - Comparing average vehicle price by title status, transmission an type. We observe cars with lien title status, transmissions other than manual, automatic (Other) and pickup trucks have higher price on average.







