# Tanzanian Water Pump Analysis
## Abstract
The focus of this project is to analyze and predict the functionality of water pumps in Tanzania. Various data mining techniques have been employed on the provided dataset and then multiple  machine learning algorithms were used to train and evaluate the models. By analyzing the various features of the water points, the models were able to pinpoint the factors that contribute towards the operational status of the water pumps with a reasonable level of accuracy. Random Forest, XGBoost, CatBoost, GradientBoost and TabNet algorithms were implemented along with a stack classifier to predict the accuracy of the model. An accuracy of 80.68 was achieved after comparing the models.
## Introduction
The data that was analyzed was obtained from an online data mining competition (https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/). The data has been derived from  the Taarifa waterpoints dashboard, a Tanzanian innovation initiative that compiles data from the ministry of water there. The collection comprises 40 variables, such as waterpoint type, water quality, and water amount, and information on more than 59,400 water points. The goal of this dataset is to predict the functional status of a water point, which can be classiffied as ”functional”, ”functional but needs repair”, or ”non functional”. Based on the data analysis the research question on focus is, how does geographic factors such as geographic location, extraction type, source of water, management group and population predict the overall performance (functionality, water quality, cost) of waterpoints in Tanzania’s different water basins?
## Data set
The dataset contains both numerical and categorical variables. The summary statistics reveal that the range and mean values differ significantly among the numerical variables. Similarly, the categorical variables have a varying number of unique values, with some columns having only one unique value. Overall, the dataset contains a wide range of information that has to be explored further to gain insights into the water wells in Tanzania. 

![Functional_nofunctional](https://github.com/user-attachments/assets/6f91edc9-5a68-48ee-a25b-df5157bc2d43)

![Summary_stats](https://github.com/user-attachments/assets/9e8ba06a-133b-47a7-a18d-7a23aeea47ed)

## Data Preprocessing 
This stage involved handling missing values, errors and outliers. The information within the 3 data sets were combined into a single dataframe.
- Subvillage: Existing null values were imputed with ”other,” and remaining error values (e.g., data with single letters) were also replaced with ”other.”
-  Amount tsh: Since the data contained numerous zeros, the values were imputed with the log value. However, considering the large number of unusable values, the
 column was ultimately dropped.
- Date recorded: The column was split into year and month, which were later used for calculating the age of the water points.
- Funder/Installer: Similar to the approach taken for subvillage, null values were replaced with ”other.” Clear errors were changed to ”other” as well (e.g., 1, A, M). The top 20 funder and installer categories were considered for modeling, and category entries were replaced as required.
- Longitude/Latitude: There were clear errors in the entries, such as entries with values of 0, were replaced with the mean value.
- GPS height: The same process as for longitude/latitude was applied.
- Region/Region code: These columns were redundant, so the ”region” column was dropped. The district code column was also dropped for the same reason.
- Population: Entries with population as 0 were imputed with the mean population. However, the data still exhibited skewness after analysis. To address this, the logarithm of the population was taken as the final population feature.
- Values like ”pub meeting” and ”permit” were factorized.
- Scheme management/Scheme name: The ”scheme name” column was dropped due to redundancy.
- Construction year: Zeros in the construction year were imputed with the median, as the year cannot be null.
- Extraction type: Null values and errors were replaced with the value ”other.”
- Payment type and payment: These columns were redundant, so the ”payment” column was dropped.
- Water quality/Quantity group/Quantity/Quality group: Quantity group and Quality group, these groups were dropped due to redundancy.
## Feature Engineering
- Age: The approximate age of the water point was calculated using the recorded year and the construction year.
- Season: It was possible to determine the season during which the water points were recorded based on the pertinent months. 

