# House Price Prediction: Kaggle


The Ames Housing dataset was compiled by Dean De Cock for use in data science education. It's an incredible alternative for data scientists looking for a modernized and expanded version of the often cited Boston Housing dataset.

The broad aims of this Machine Learning Project are to understand the dataset and to build a ML pripeline that can predict SalePrice of Houses using various techniques.



The dataset and documentation can be found in these links:
[1. Kaggle](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
[2. Feature documentation by Dean de Cock](https://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

## Some insights that I've gleaned from studying Instructor's notes about the ['Ames, Iowa: Alternative to the Boston Housing Data as an End of Semester Regression Project'](https://jse.amstat.org/v19n3/decock.pdf) by Dean De Cock, Truman State University


1.  The dataset contains 2930 observations and a set of 80 explanatory variables (23 nominal, 23 ordinal, 14 discrete, and 20 continuous) involved in assessing home values.

2. **20 continuous variables** relate to various area dimensions for each observation.

3. The **14 discrete variables** typically quantify the number of items occurring within the house. Most are specifically focused on the number of kitchens, bedrooms, and bathrooms, etc.

4. There are a large number of **categorical variables (23 nominal, 23 ordinal)** associated with this data set. They range from 2 to 28 classes with the smallest being STREET (gravel or paved) and the largest being NEIGHBORHOOD (areas within the Ames city limits). The nominal variables typically identify various types of dwellings, garages, materials, and environmental conditions while the ordinal variables typically rate various items within the property.

4. **Outliers**, bad datapoints: 5 observations to be removed from the data (**a plot of SALE PRICE versus GR LIV AREA** will quickly indicate these points). Three of them are true outliers (Partial Sales that likely don’t represent actual market values) and two of them are simply unusual sales (very large houses priced relatively appropriately). Any houses with more than 4000 square feet from the data set (which eliminates these five unusual observations).

6. **Recommended:** **Incorporating the neighborhood variable** into the model by converting it to a set of dummy variables. Coefficients for the continuous variables tend to have values with more realistic interpretations when used in conjunction with the neighborhood variable.

> Regression Analysis: SalePrice versus Lot Area, Total Bsmt SF, ...

> The regression equation is
SalePrice = 7851 + 1.72 Lot Area + 41.2 Total Bsmt SF + 40.8 Gr Liv Area + 20952 Garage Cars + 8379 FireYN

7. The simple plot of the **total area of a house (basement area + first and second floor area) and the type of sale (Sale Condition)** summarizes much of the variation in sale price. One can see that larger houses cost more with a bonus being paid for “Partial” sales (new homes only partially complete at last assessment) and a discount being paid for “Abnormal” sales (short sales & foreclosures).

8. As a group, the **23 ordinal variables** present special difficulties. Almost all of these variables are quality related, with the expectation that higher categories should yield a coefficient at or above the previous category. In some of my initial modeling, I found that the estimated coefficients for a number of these categories did not follow this rule, likely due to interrelations with other variables within the model. While not incorrect, this situation leads to confusing interpretations (lower quality is better?). I found that some of these anomalies could be remedied by collapsing some of the larger five and ten point quality scales into fewer categories.

9. Closely related to this issue are the **14 discrete variables** which are typically quantifying **various types of rooms or items within a house.** When treated categorically many of these items exhibit the same inconsistency as the ordinal variables (a fourth bathroom actually detracts from the value of a house?). Potentially these inconsistencies can be relieved by treating the variables as covariates which results in equal increases per item (I found this worked well with number of bathrooms) or by once again collapsing the number of categories (which worked well with number of cars per garage).

10. **80% of the variation** in residential sales price can be explained by the neighborhood and total square footage **(TOTAL BSMT SF + GR LIV AREA)** of the dwelling. On the other extreme, I have constructed a model with 36 variables (some of my own creation through recoding and interactions), all significant at the .05 level, which explains 92% of the variation in sales. While I would consider this model overly complicated, it yielded intuitively appealing coefficients where positive attributes (such as being near a park) added to the value of the home and negative attributes (such as being adjacent to a railroad) subtracted from the value.


=====================

Ames dataset: House Price prediction for Kaggle competition (advanced regression, supervised ML)

https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/overview
