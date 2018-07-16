# H1 Machine Learning on a Used Car Market
Problem
Shopping for a used vehicle is quite tricky, because there are following questions: Is this price reasonable? or  Why is this car seem cheaper or more expensive? This question is often difficult to answer due to the fact that it's hard to keep track of all the vehicles of interest currently available on the market.
2. Solution
This project is to build a model that determines if the asking price for a particular car is reasonable given the information provided in the listing. 
Data Collection and Cleaning
Data source obtaining method:
http://www.cars.com , scrape using Selenium
https://vpic.nhtsa.dot.gov/api/vehicles/DecodeVINValuesBatch/ scrape using API
Fueleconomy.gov download csv format
The data  limitations:
Only used cars. According to Ward’s Automotive Yearbook 2013, about 42 million used cars ($380 billion in total revenues) were sold in the U.S. in 2012. In comparison, about 15 million new cars ($300 billion in total revenue) were sold in the U.S. in the same year.
Vehicles located within 75 miles of Chicago, IL, because of local consumers’ preferences.
Minimum price $5000
After obtaining and filtering the data, the final dataset contains:
4235 unique listings
54 Makes
485 Models
34 unique years
Feature Selection
My target is price. For feature selection, I did three different approach. 
Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model) and text extraction using NLP. 
Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model) and built_feature(popular cars).
 Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model),  built_feature(popular cars) and keywords_feature(navigation, audio, camera, etc)
Exploratory Data Analysis 
Figure 3.1 Number of Listings Per Model Y. Most of the listing are contained in model years 2015 and  2016.


.

Figure 3.2 Price Distribution per Model Year. This plot is limited to a maximum price of $150,000. As expected, there is a general trend of prices increasing as the age of the vehicles decreases. However, there is a wide spread of prices within each year.

Figure 3.3 Price Distribution  over all listing.


Modeling

The cleaned data set was divided into training and test subsets--the training set is 66%, and the test set is 33%. 
RandomForest regressor was used to predict price of cars. Other modeling techniques, such as xgboost forest, produced similar accuracy scores, but over-predicted renewal. Randomforest model accuracy was 0.86 on the training set and 0.72 on the test set.

Conclusion
My scraped data was very dirty and missing many entries, especially, exterior color, interior color, “plantcountry”. I had to drop them, even those are very important features.  While the details provided in the downloaded listings are quite comprehensive, I was only able to include a small number of the features. And some features, especially text_blobs, were very unreliable. Many of the them had multiple variations of the same name, or different names to same meaning  'radio!, fm/am radio, radio!!!'. I was not able to develop code capable of cleaning up the discrepancies between the various names, and I suspect this had a negative impact on both the regression and recommendation calculations.
Future Steps
According to the paper “Invest in Information or Wing It? A Model of Dynamic Pricing with Seller Learning”, the distribution of the initial prices and the total price changes due to the adjustments of the seller’s belief is very important feature. If I would scrape Carmax.com instead cars.com, i would obtain those kind of information, because they have listing duration by days. 


