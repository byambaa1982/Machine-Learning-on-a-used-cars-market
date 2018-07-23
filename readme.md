# Machine Learning on a Used Car Market
### 1. Problem

Shopping for a used vehicle is quite tricky, because there are following questions: Is the price reasonable? Or, why does this car seem cheaper [or more expensive]? This question is often difficult to answer due to the fact that it's hard to keep track of all the vehicles of interest currently available on the market.

### 2. Solution

This project's objective was to build a model that determines if the asking price for a particular car is reasonable given the information provided in the listing. 

### 3. Data Collection and Cleaning

Data source and obtaining method:
+ http://www.cars.com -scraped using Selenium
+ https://vpic.nhtsa.dot.gov/api/vehicles/DecodeVINValuesBatch/ -accessed API
+ https://Fueleconomy.gov -downloaded in .csv format

### Data  limitations:

+ Only looked at used cars. According to Ward’s Automotive Yearbook 2013, about 42 million used cars ($380 billion in total revenues) were sold in the U.S. in 2012. By comparison, about 15 million new cars ($300 billion in total revenue) were sold in the U.S. in the same year.
+ Vehicles located within 75 miles of Chicago, IL, because of local consumers’ preferences.
Minimum aksing price of $5,000.
After obtaining and filtering the data, the final dataset contained:
+ 4,235 unique listings
+ 54 makes
+ 485 models
+ 34 unique years

### 4. Feature Selection

The target variable was price. For feature selection, I took three different approaches. 
+ Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model) and text extraction using NLP. 
+ Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model) and build feature(popular cars).
+ Combination of numerical (year, mileage, price ), categorical(drivetrain, fuel type, transmission, make, model),  build features(popular cars) and keywords features(navigation, audio, camera, etc.)

### Exploratory Data Analysis 

### Figure 4.1 Number of Listings Per Model Year. Most of the listings are contained in model years 2015 and  2016.

![alt text](/images/num_list "Logo Title Text 1")

### Figure 4.2 Price Distribution per Model Year. This plot is limited to a maximum price of $150,000. As expected, there is a general trend of prices increasing as the age of the vehicles decreases. However, there is a wide range of prices within each year.

![alt text](/images/price_dist_pmy "Logo Title Text 1")

### Figure 4.3 Mile Distribution  over all listings.

![alt text](/images/dist_mile_pmy "Logo Title Text 1")


### 5. Modeling

The cleaned data set was divided into training and test subsets--the training set was 66%, and the test set was 33% of the total dataset. 
Several regressors were used to predict the price of cars. XG Boost was the superior model. Its model accuracy was 0.89 on the training set and 0.81 on the test set.

### Figure 5.1 Result!.

![alt text](/images/result "Logo Title Text 1")

### Figure 5.2 Results in general!.

![alt text](/images/with_exotic "Logo Title Text 1")

### Conclusion
+ My scraped data was very messy and missing many entries, especially exterior color, interior color and plant country. I had to drop these, even though those are very important features.  While the details provided in the downloaded listings are quite comprehensive, I was only able to include a small number of the features. And some features, especially text feature, were very unreliable. Many of the them had multiple variations of the same name, or different names with the same meaning, such as 'radio!, fm/am radio, radio!!!'. I was not able to develop a code capable of cleaning up the discrepancies between the various names, and I suspect this had a negative impact on the regression. 
+ My model shows different regression (Fig 3.5) on expensive cars (i.e. more than $150000), because exotic cars have very different features, various interests and are very different from one another. 

### Future Steps

+ Obtaining data and cleaning it took most of my time in completing this project. I will collect more data and make it publicly available (i.e kaggle dataset) after some EDA to help fellow data scientists. 
+ According to the paper “Invest in Information or Wing It? A Model of Dynamic Pricing with Seller Learning” https://www.hbs.edu/faculty/Publication%20Files/16-027_1e5317c9-b364-4b55-a90d-fd32fbee167b.pdf, the distribution of the initial prices and the total price changes due to the adjustments of the seller’s belief is a very important feature. If I had scraped Carmax.com instead Cars.com, i would have obtained this kind of information, because they have listing duration by days. 
+ Finish my recommendation engine. 

