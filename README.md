1) Which are the most decisive factors, forming the price of a car?

1. Age (alder) — the strongest negative factor. The older the car, the lower the price. This was confirmed by the correlation matrix and the cluster analysis where Cluster 0 (newest, avg 2 years) had the highest average price of 204,179 DKK.
2. Mileage — the second strongest negative factor. Higher mileage indicates more wear and directly reduces price. The scatter plot of price vs mileage clearly showed this downward trend.
3. Engine size (ccm2) — larger engines generally mean higher prices, as they are associated with more powerful and premium vehicles.
4. Brand (make) — Volvo consistently commanded higher prices than Ford and Toyota across all segments, confirming that brand is a significant price driver.
5. Car type — certain models like XC60 and Mustang were priced significantly higher than everyday models like Aygo or Ka, showing that the specific model strongly influences price.


2) Which make and model of a car is most popular, according this data source? Which are its
technical characteristics?

Most Popular Make: Ford with 1,538 listings out of 2,759 total cars.
Most Popular Model: Ford Fiesta — the most frequently listed model in the dataset.
Average Technical Characteristics of the Ford Fiesta:
FeatureValueFuel efficiency22.4 mpgMileage81,964 kmEngine size1,052 ccmAge5.3 yearsPrice129,935 DKK
The Ford Fiesta is a compact, fuel efficient car with a small engine, moderate mileage and a mid-range price. Its popularity in the dataset reflects its status as one of the most common everyday cars in the Danish used car market.

3) Is there any obvious tendency in the preference of the car models during the past 5-10 years?

Tendency in Car Model Preferences (Past 5-10 Years)
The graph shows the number of listings per brand grouped by car age. Several clear tendencies are visible:
Ford has dominated the market consistently across all age groups, maintaining the highest number of listings from newer cars (0-2 years) through to older ones (10+ years). This confirms Ford as the most popular brand overall.
Toyota shows a notable spike at around 7 years old, suggesting a particularly strong sales period roughly 7 years ago. Toyota's presence drops significantly for newer cars (0-3 years), indicating a possible decline in recent popularity or market share.
Volvo remains consistently low across all age groups, reflecting its smaller but stable market presence as a premium brand.
Overall tendency — both Ford and Toyota show a clear decline in listings for very recent cars (0-2 years), which could reflect the broader industry shift towards electric vehicles, as neither brand is represented in the EV segment in this dataset. The used car market for traditional combustion engines appears strongest in the 3-10 year age range.


4) Do people in Denmark prefer big or small cars? How reliable is your answer of this question?

The data clearly suggests a strong preference for small cars. Over 1,400 out of 2,443 cars have a 1,000 ccm engine — the smallest available in the dataset. The median engine size is also 1,000 ccm, meaning more than half of all cars have the smallest possible engine. Additionally, 5-door body styles dominate with 2,232 listings, which are typically compact hatchbacks like the Ford Fiesta, Ford Focus and Toyota Yaris — all small to medium sized cars.

The reliability is moderate for several reasons:

The dataset only contains 3 brands — Ford, Toyota and Volvo — which are all known for producing smaller cars. Larger car brands like BMW, Mercedes or Audi are not represented, which skews the results towards smaller engines.
The data was scraped from a single source on a single date, so it may not represent the full Danish car market.


5) Are there any locations in Denmark, where the expensive cars are preferred choice by the
owners?

Yes, the data shows clear regional differences in car prices. Vestjylland has the highest average car price at 160,909 DKK, followed closely by Syd- og Sønderjylland at 155,258 DKK and Nordsjælland at 140,955 DKK. København comes in fourth at 140,177 DKK, which is slightly surprising given its status as the capital and wealthiest region.


6) Which machine learning methods did you choose to apply in the solution and why?

Linear Regression
Linear Regression was chosen to predict car prices because price is a continuous numeric variable, making it a classic regression problem. It is interpretable, computationally efficient and works well when there is a linear relationship between features and the target variable. The model achieved an R² of 0.87, confirming that the linear relationships between age, mileage, engine size and price are strong enough for this approach.


K-Means Clustering
K-Means was chosen for vehicle segmentation because it is an unsupervised algorithm that groups data points by similarity without requiring predefined labels. Since no price segments existed in the original data, K-Means was ideal for discovering natural groupings. The Elbow Method was used to objectively determine the optimal number of clusters, which turned out to be 3, corresponding intuitively to Budget, Mid-range and Premium segments.


Random Forest Classification 
Random Forest was chosen to classify cars into price segments because it is a robust supervised algorithm that handles both numeric and categorical features well. It is resistant to overfitting compared to a single decision tree and provides feature importance scores. The model achieved 97% accuracy, demonstrating that the price segments identified by clustering are well-defined and predictable from the available features.


7) How accurate are your solutions of prediction? Explain the meaning and the difference between
the various quality measures

Regression — R² = 0.87, MAE = 20,483 DKK, RMSE = 30,078 DKK
The model explains 87% of price variation, which is a strong result. MAE and RMSE both measure prediction error in DKK — the difference is that RMSE penalizes large errors more heavily than MAE. The fact that RMSE is notably higher than MAE suggests some outlier cars where the model is significantly off.


Clustering — Elbow Method, K=3
Clustering has no traditional accuracy measure since it is unsupervised. Quality was assessed using inertia, which measures cluster compactness. The Elbow Method identified K=3 as optimal, and the cluster means confirmed three meaningful segments: Budget, Mid-range and Premium.


Classification — Accuracy = 97%, F1-score = 0.97
The model correctly classified 97% of cars. Precision measures how many predicted labels were correct, recall measures how many actual cases were caught, and F1-score balances both into a single metric. All three segments scored 0.97 or above, confirming consistent and reliable performance across all price segments.



8) What could be done for further improvement of the accuracy of the models?

 Clustering

Try alternative clustering algorithms such as DBSCAN, which can detect clusters of irregular shapes and handle outliers better than K-Means
Include categorical features like brand and car type in the clustering, not just numeric ones
Experiment with different distance metrics and scaling methods

Classification

The model already achieves 97% accuracy, leaving little room for improvement. However, adding more training data and more diverse brands beyond Ford, Toyota and Volvo could make the model more generalizable
Hyperparameter tuning of the Random Forest (number of trees, max depth) could squeeze out marginal gains

General

The biggest improvement across all models would come from a larger and more diverse dataset covering more brands, regions, fuel types and a longer time period
Including electric vehicles would make the dataset more representative of the current Danish car market
