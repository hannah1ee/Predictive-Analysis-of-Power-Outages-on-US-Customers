# Step 1 | Introduction

### Project Focus

The question I focus on in this project is: Can we predict the total number of customers affected by a power outage based on outage durations, climate categories, and geographical regions?

### Dataset Overview

| outage_start        | outage_restored     | outage_duration | outage_season | outage_month | cause_category     | us_state  | climate_region     | climate_category | customers_affected | total_customers | total_sales |
| :------------------ | :------------------ | --------------: | :------------ | :----------- | :----------------- | :-------- | :----------------- | :--------------- | :----------------- | --------------: | ----------: |
| 2011-07-01 17:00:00 | 2011-07-03 20:00:00 |            3060 | Summer        | July         | severe weather     | Minnesota | East North Central | normal           | 70000              |         2595696 |     6562520 |
| 2014-05-11 18:38:00 | 2014-05-11 18:39:00 |               1 | Spring        | May          | intentional attack | Minnesota | East North Central | normal           | <NA>               |         2640737 |     5284231 |
| 2010-10-26 20:00:00 | 2010-10-28 22:00:00 |            3000 | Autumn        | October      | severe weather     | Minnesota | East North Central | cold             | 70000              |         2586905 |     5222116 |
| 2012-06-19 04:30:00 | 2012-06-20 23:00:00 |            2550 | Summer        | June         | severe weather     | Minnesota | East North Central | normal           | 68200              |         2606813 |     5787064 |
| 2015-07-18 02:00:00 | 2015-07-19 07:00:00 |            1740 | Summer        | July         | severe weather     | Minnesota | East North Central | warm             | 250000             |         2673531 |     5970339 |


This dataset provides insight into the frequency, causes, and impacts of major power outages across different regions and climates in the US from January 2000 to July 2016. It has 56 columns, and 1534 total rows. The columns that are relevant to my question specifically are:
- `CLIMATE.REGION`: Specifies the climate consistent regions where the outage occured.
- `CLIMATE.CATEGORY`: Specifies the climate conditionn (warm, cold, or normal) for the year that the outage occured, which can have influenced the severity or duration of the outage
- `OUTAGE.START.DATE`: The exact start date of the outgage, which would be important for understanding if the outage occured at the same day as others for the same reasons
- `OUTAGE.START.TIME`: The exact start time of the outgage, which would be helpful in determinining if the outgage occured during peak usage times
- `OUTAGE.RESTORATION.DATE`: The exact restoration date of the outgage, which could be helpful in determining the severity of the outgage
- `OUTAGE.RESTORATION.TIME`: The exact time the outgage was restored. 
- `CAUSE.CATEGORY`: This column details the cause of the outgage, which can then be possibly linked to the number of customers affected by the power outgage as well as the duration of the restoration
- `OUTAGE.DURATION`: The total time of the power outgage, which is a critical factor in determining how many customers are affected because the longer it goes the higher chance a customer is being impacted. 
- `CUSTOMERS.AFFECTED`: The total number of customers that are impacted by teh outgage. This is also my response / target variable, which I aim to predict thorugh this project
- `TOTAL.SALES`: The total number of electricity sales measured in megawatts-hour. This could be helpful in relating the number of customers affected during an outgage
- `U.S._STATE: The geographic location of the outgage, which influences the number of customers affected due to the difference in population density.
- `TOTAL.CUSTOMERS`: The total number of customers served in a region, which can offer a direct measure of how mnay people could potentially be affected by an outgage because they are the ones vulnerable.

### Relevance

Readers of this website should care about the dataset and the specific question about predicting total number of customers affected by power outage because of the impact of power outages on individuals and businesses. Power outages can disrupt daily life and affect business operations leading to significant economic and social consequence. 

Have you ever had delicious leftovers in your fridge or a week's full of groceries but had to throw them out because the power went out for a couple hours? Understanding the patterns and causes of power outages can provide valuable insights to not have that happen again.


# Step 2 | Data Cleaning and Exploratory Data Analysis

### Cleaned DataFrame

| outage_start        | outage_restored     | outage_duration | outage_season | outage_month | cause_category     | us_state  | climate_region     | climate_category | customers_affected | total_customers | total_sales |
| :------------------ | :------------------ | --------------: | :------------ | :----------- | :----------------- | :-------- | :----------------- | :--------------- | :----------------- | --------------: | ----------: |
| 2011-07-01 17:00:00 | 2011-07-03 20:00:00 |            3060 | Summer        | July         | severe weather     | Minnesota | East North Central | normal           | 70000              |         2595696 |     6562520 |
| 2014-05-11 18:38:00 | 2014-05-11 18:39:00 |               1 | Spring        | May          | intentional attack | Minnesota | East North Central | normal           | <NA>               |         2640737 |     5284231 |
| 2010-10-26 20:00:00 | 2010-10-28 22:00:00 |            3000 | Autumn        | October      | severe weather     | Minnesota | East North Central | cold             | 70000              |         2586905 |     5222116 |
| 2012-06-19 04:30:00 | 2012-06-20 23:00:00 |            2550 | Summer        | June         | severe weather     | Minnesota | East North Central | normal           | 68200              |         2606813 |     5787064 |
| 2015-07-18 02:00:00 | 2015-07-19 07:00:00 |            1740 | Summer        | July         | severe weather     | Minnesota | East North Central | warm             | 250000             |         2673531 |     5970339 |

## Data Cleaning Steps

### 1. Combining Date and Time Columns for Power Outage Start and Restoration

The first step in my data cleaning process involved combining separate date and time columns representing the start and restoration of power outages into single datetime columns. This step was crucial for consistency and improved usability of the data for subsequent analyses.

The code checked if all necessary date and time columns existed in the dataset before proceeding with the combination. Additionally, any errors during conversion were coerced to NaT (Not a Time) values where necessary, ensuring data integrity. Finally, the original date and time columns were dropped from the dataset to avoid redundancy and streamline further analyses. Overall, this cleaning step enhanced the dataset's usability by providing a unified representation of outage start and restoration times.

### 2. Adding Season and Month Names

The second step in my data cleaning process involved adding two new columns to the dataset, `outage_season` and `outage_month`, which provided information about the season and month when each power outage occurred, respectively.

For `outage_season`, I created a custom function `get_season` which is defined to map each month (represented as an integer from 1 to 12) to its corresponding season (Spring, Summer, Autumn, or Winter). This function is then applied to the `outage_start` datetime column to create the new `outage_season` column.

Similarly, for `outage_month`, the `outage_start` datetime column is utilized. The `dt.strftime('%B')` function extracts the full name of the month (e.g., January, February, etc.) and assigns it to the new `outage_month` column.

### 3. Reorders Columns of DataFrame `outageand` and converts numerical columns to numeric type

The third step involved reordering the columns of the DataFrame `outage` and converting certain columns to numeric type. Reordering the columns was primarily for organizational purposes, ensuring that related columns were grouped together logically. This reordering didn't affect the content of the data but improved readability and facilitatedd analysis.

The conversion of columns to numeric type was crucial for ensuring that numerical operations could be performed on these columns accurately. Specifically, the columns `outage_duration`, `total_sales`, and `customers_affected` were converted to numeric type using the `pd.to_numeric` function. This conversion ensured that any entries in these columns that were not numerical (such as non-numeric characters or missing values) were coerced to `NaN` (Not a Number), and then the data type was converted to the nullable integer type `Int64`. This ensured consistency in data representation and allowed for proper numerical analysis without errors due to incompatible data types. 

### 4. Generating Summary Statistics for Quantitative Columns to Remove Outliers

The last last step involved generating summary statistics for quantitative columns (`outage_duration`, `customers_affected`, `total_customers`, `total_sales`) to identify and subsequently remove outliers. The summary statistics were calculated using the `describe()` method, providing key statistical measures such as mean, median, standard deviation, minimum, and maximum values. After obtaining the summary statistics, the function `remove_outliers` was applied to the DataFrame outage using these statistics.

Within the `remove_outliers` function, the Interquartile Range (IQR) method was utilized to determine the bounds for outliers. These bounds were calculated using the first quartile (Q1) and third quartile (Q3) values obtained from the summary statistics. Rows with values falling outside the bounds (determined by multiplying the IQR by 1.5) were removed, except for missing values (NaN). This step ensured that outliers were effectively identified and removed from the dataset while preserving missing data.

Overall, this data cleaning process helped to improve the quality and reliability of the dataset by removing extreme values that could potentially skew the analyses and models later on. Additionally, it facilitated more accurate statistical analyses and modeling by ensuring that the data remained within reasonable ranges.

## Univariate Analysis

### Distribution of a Single Column `cause_category`.

<iframe
  src="cause_category_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The bar chart depicts various causes of power outages, categorized and tallied. The most frequent cause is severe weather, with a count approaching 800 incidents, indicating a most common significant impact. Intentional attacks are also a notable cause, though significantly less frequent than weather-related incidents. Other categories such as islanding, fuel supply emergencies, and equipment failures are represented as well but with fewer occurrences, suggesting they are less common causes of observed power outages.

### Pivot table

|                                |   counts |   proportion |
|:-------------------------------|---------:|-------------:|
| ('climate_category', 'cold')   |      404 |         0.32 |
| ('climate_category', 'normal') |      631 |         0.49 |
| ('climate_category', 'warm')   |      246 |         0.19 |

The pivot table shows distribution of `climate_category`: cold, normal, and warm. The data gives an insight into the distribution of climate categories within areas that had significant power outages. . It shows how climate conditions are skewed towards 'normal', with significant but lesser occurrences of 'cold' and 'warm' climates. Understanding the distribution of these climate categories can help utilities and disaster management agencies anticipate and mitigate power outage risks by adapting infrastructure, planning for demand fluctuations, and implementing more resilient power systems tailored to the predominant climate challenges.

This information can also be applied to knowinng who is most at risk of being affected when power goes out. For example, when it is really cold it would be more risky for the power to go out and for a family living in somewhere with cold climate to not be able to have heating. 


## Bivariate Analysis

<iframe
  src="scatter_plot_outage.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The plot shows a scatter plot of outage duration in minutes on the x-axis versus the number of customers affected on the y-axis. There is a wide distribution of points indicating that there isn't a clear correlation between the duration of an outage and the number of customers affected. There are outages of varying durations that affect a large number of customers, as well as long-duration outages that affect fewer customers, and vice versa.

# Step 3 | Assessment of Missingness

## NMAR Analysis

I believe that the `customers_affected` column is Not Missing at Random (NMAR). NMAR implies that the missingness of the data is related to the reason it is missing, which can lead to biases if not properly addressed. For instance, if data on `customers_affected` is more likely to be missing during major catastrophic events because data collection becomes more challenging, then the missingness is related to the magnitude of the event itself.

To better explain the missingness of `customers_affected` and potentially move the classification from NMAR to Missing at Random (MAR), I could implement a permutation test on other columns to investigate any potential dependencies. Specifically, I would look for patterns of missingness associated with other variables, like the duration or location of outages. By identifying such patterns, I might be able to attribute the missingness to observable data, thereby reclassifying it as MAR. This process would not only enhance the robustness of statistical analysis but also the reliability of any predictive models developed from the dataset.

## Missingness Dependency

<iframe
  src="missingness.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The plot provided illustrates the empirical distribution of a test statistic used in a permutation test to evaluate the missingness of 'customers_affected' based on 'cause_category'. It indicates the frequency of the sum of absolute differences in the proportion of missing 'customers_affected' data across different permutations of the 'cause_category'. 

The red vertical line represents the observed statistic from the original data. The data on the x-axis represent the sum of absolute differences across permutations, and the counts on the y-axis represent how often each sum occurred during the permutation test. 

Because my observed statistic lies outside the distribution of the permuted statistics, this suggests that there is a low probability that the observed missingness pattern could have occurred if the missingness was indeed random with respect to the `cause_category`. Therefore, the missingness could be NMAR (Not Missing at Random), meaning that the probability of missingness is related to the data itself, possibly affected by the `cause_category`. 

A P-value of 0.0 suggests that the observed data, the pattern of missingness in `customers_affected` relative to `cause_category`, is highly unlikely under the null hypothesis. The null hypothesis is this case would be that there is no association or effect between the missingness of `customers_affected` in dependence of `cause_category`. Because the p-value is 0.0, I am lead to reject this null hypothesis, concluding that there is some sort of statistical evidence of a non-random dependence of the missingness of `customers_affected` on `cause_category`, which would lead me to think that the missingness type of customers_affected is NMAR

With respect to my question, the results of the missingness permutation tests also suggest that we may be able to predict the total number of customers affected by a power outage based on outage causes. 

<iframe
  src="not-dependent.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This plot provided illustrates the empirical distribution of a test statistic used in a permutation test to evaluate the missingness of 'customers_affected' based on 'climate_category'. Similar to the graph above, it indicates the frequency of the sum of absolute differences in the proportion of missing 'customers_affected' data across different permutations of the 'climate_category'. 

However, because in this plot my observed statistic lies within the distribution of the permuted statistics, this suggests that there is a high probability that the observed missingness pattern could have occurred if the missingness was indeed not random with respect to the `climate_category`. Therefore, the missingness could be MAR (Missing at Random), meaning that the probability of missingness is related to the data itself. 

A P-value of 0.47 suggests that the observed data, the pattern of missingness in `customers_affected` relative to 'climate_category', is not statistically that unlikely under the null hypothesis. The null hypothesis is this case would be that there is no association or effect between the missingness of `customers_affected` in dependence of 'climate_category'. Because the p-value is 0.47, I am unable to reject this null hypothesis, which would lead me to think that the missingness type of `customers_affected` could be MAR

With respect to my question, the results of the missingness permutation tests also suggest that we may not be able to predict the total number of customers affected by a power outage based on climate categories. 


# Step 4 | Hypothesis Testing

**Null hypothesis (H0)**: The mean number of customers affected by power outages in warm climate regions is equal to that in cold climate regions.

**Alternative hypothesis (H1)**: The mean number of customers affected by power outages in warm climate regions is different from that in cold climate regions.

**Test Statistic**: absolute difference in means between the two climate categories. 

**Significance Level:** The significance level (α) will be set to 0.05.

**Resulting P-Value:** 0.739. This p-value is substantially higher than my significance level (α) of 0.05, which means that there is a high probability of observing the data, or something more extreme, if my null hypothesis was true. In other words, the data does not provide sufficiennt evidence to reject the null hypothesis. 

**Conclusion:** Therefore, I conclude that, based on my sample data, there is likely no statistically significant difference in the mean number of customers affected by power outages between warm and cold climate regions. The high p-value suggests that any observed difference in means has a good change of being due to random chance rather than a true effect of climate on the number of customers affected.

**Significance:** These choices are good choices for answering the question I am trying to answer, Can we predict the total number of customers affected by a power outage based on outage durations, climate categories, and geographical regions?, because it lets me know that there is likely not a strong correlation between power outages in varying climate regions and the mean number of customers affected by power outages. I can likely not train on this feature because there is not a strong absolute difference in means. 

# Step 5 | Framing a Prediction Problem

My prediction problem is: **Predict the total number of customers affected by a power outage based on various features such as outage duration, climate category, and geographical region**

The type of prediction problem is: **regression**. Predicting the total number of customers affected by a power outage using predictors like outage duration, climate category, and geographical region is inherently a regression problem because the response variable—total number of customers affected—is a continuous variable. 

The response variable I've chosen for my predictive model is the **total number of customers affected by power outages**. I selected this variable because it directly reflects the impact of an outage event and is a critical factor for utility companies when allocating resources for emergency response and restoration.

For evaluating my model, I've chosen to use the **Root Mean Squared Error (RMSE)** as my metric. I chose RMSE because it express the average prediction error in the same units as the response variable itself, making it very intuitive. I can very easily see a clear indication of the average distance between the predicted and actual values. This is particularly helpful and important in my analysis, as it gives a straightforward interpretation of the model's performance. 

RMSE was chosen over other metrics because of its sensitivity to the magnitude of errors. While Mean Absolute Error (MAE) is a viable alternative that also provides errors in appropriate units, RMSE gives a more weighted assessment by squaring the errors before averaging, which tends to highlight and penalize larger errors more substantially. This characteristic of RMSE is especially useful, where larger errors are more detrimental and thus should be given more attention in the model evaluation process.

In selecting features for the model, I recognize the importance of ensuring that they would be available at the time of prediction. I decided that using outage duration is appropriate as it refers the actual duration, which would be known if I am predicting total number of customers affected by a power outage after it has happened. Similarly, climate category and geographical region are predefined and known ahead of time, making them suitable predictors that would be known when the prediction needs to be made.

# Step 6 | Baseline Model

For my baseline model, I developed a Linear Regression model to predict the total number of customers affected by a power outage, informed by 1 quantitative and discrete feature `total_customers` and 1 qualitative and 1 nominal feature `climate_region`. I encoded `climate_region` using OneHotEncoder to transform this categorical column into a format that I can provide to the model for training. 

To prepare my model, I used a ColumnTransformer to handle both numerical and categorical data appropriately, ensuring that my model could handle the different feature types. I used a simple linear regression as the regressor within a Pipeline that includes the preprocessing and regression steps. This approach maintains the flow of data transformation and model application coherently, making the process easier to manage and replicate.

After training the model and making predictions on the test set, I evaluated its performance using the Root Mean Squared Error (RMSE), which is the standard deviation of the residuals (prediction errors). I decided to use RMSE for my regression problem as it gave me a clear indication of how far off my predictions were from the actual numbers in the same units as the target variable. 

The RMSE I got from my baseline model was 72948, which I decided was "decent" because it was a little lower than the standard deviation of the data of the response variable, `customers_affected` in my model, which was 76309. Standard deviation is the spread of all of my response variable, and so it tells me, on average, how far each data point is from the mean. RMSE on the other hand measures the spread of all the prediction errors from the actual outcomes. Both are better to be lower because they mean that the points/predictions are closer to the mean/actual outcome. Because my RMSE is close and a little lower than the standard deviation of the data, I believe that my current model is at least a little "okay" because it is a bit smaller than the standard deviation. 

# Step 7 | Final Model

The features I addded to my Final Model and my reasoning:
1. **PolynomialFeatures** for **`outage_duration`.** I thought it'd be good to add the polynomial features for `outage_duration` because when I performed the Bivariate Analysis on the relationship between `outage_duration` and `customers_affected` I saw that there was a big of a non-linear relationship. Because the relationship was more complex than linear, I thought that it would be good to include polynomial terms so that the model can capture non-linear patterns in the data.
2. **StandardScaler** for **`total_sales**`. I thought that it'd be good to add this because I saw that higher sales correlated with higher population densities and so therefor potentially more complex infrastructures, impacting the total number of customers affected.
3. For **`total_customers`** I decided to pass through without any transformation because given that the feature I am lookinng for is total number of customers affected, it seemed reasonable to have a direct relationship with `customers_affected` as they are the ones that aregling to be affected directly. I decided that a passthrough feature would be good here to preserve the scale and distribution of the raw data.
4. I **One-Hot-Encoded** categorical the nominal features **`cause_category`, `us_state`,** and **`outage_season`** to treat each category as a separate feature without any intrinsic order. I believe that one-hot-encoding these columns improved my model because it best to allowed the model to learn the unique imapact of each category and its variables on the number of customers without being impacted by any of the other categories or their variables. I also chose the categorical features `cause_category`, `us_state`, and `outage_season` because when I performed my missingness permutation tests, I saw that there was likely to be some kind of relationship between `cause_category`, `us_state`, and `outage_season` and the missingness of `customers_affected` given many p-values close to 0 and less than a significance level of 0.05.
 
 I also chose these features because as stated in Step 5. Framing a Prediction Problem, I knew it would and is very important for the festures I chose to be available at the time of prediction or after a major power outage. `outage_duration`, `total_customers`, `total_sales`, `cause_category`, `us_state`, and `outage_season` are all features that can be found at the end of a power outage.

I chose the **`RandomForestRegressor`** model due to its flexibility and robustness in handling non-linear relationships and interactions among features. It operates by constructing a multitude of decision trees during training and outputting the average prediction of the individual trees, which tends to provide a more accurate and stable prediction than a single decision tree would. I thought that this model would be the best model to be able to capitalize on its ability to manage the complexity inherent in the relationships between features and the target variable, which I saw through various plots, is not the most linear. The non-linear relationships and interactions, especially after introducing polynomial features for outage_duration, are best handled by an algorithm that is complex enough to capture the varieties of the fitting without being prone to overfitting.

Through **`GridSearchCV`**, the best hyperparameters—specifically the number of estimators and the maximum depth of the trees—were identified. This was done through cross-validation to ensure that the chosen hyperparameters generalize well to unseen data by evaluating model performance across different subsets of the training data. The hyperparameters that ended up performing the best were max_depth = 100 and n_estimators = 150. 

I used GridSearchCV to conduct hyperparameter optimization in the most structured and efficient manner I knew. GridSearchCV works by evaluating combinations of parameters, in this case, the number of estimators (n_estimators) and the maximum depth of each tree (max_depth). Cross-validation was crucial in this process, as it split the training data into multiple subsets, allowing the model to be trained and validated against different segments of the dataset. I believe that this approach was good because it allowed me to limit the risk of overfitting and ensures that the performance of the model is not a result that is dependent on one particular set of data.

The final model's performance, as quantified by the RMSE of 56001, was an improvement over the baseline model's performance of an RMSE of 72948. A lower RMSE indicates that my final model's predictions were on average closer to the actual number of customers affected than my baseline's model. This improvement tells me that my final model, after engineering more features and optimizing its hyperparameters, is better able to capture the underlying patterns in the data more effectively than the baseline model, which in turn results in more accurate predictions of total number of customers affected by a pwoer outage.


# Step 8 | Fairness Analysis

**Group X:** Customers in regions categorized under a `warm` climate.
**Group Y:** Customers in regions categorized under a `cold` climate.

**Evaluation Metric:** RMSE will be used to measure the performance of the model for each group. I decided that RMSE is a good evualtion metric because it is sensitive to the magnitude of errors, making it a good indicator of fairness when comparing average performance of models across different groups.

**Null Hypothesis (H0):** The RMSE for 'warm' climate predictions is equal to the RMSE for 'cold' climate predictions.
**Alternative Hypothesis (H1):** The RMSE for 'warm' climate predictions is not equal to the RMSE for 'cold' climate predictions.

**Test Statistic:** I chose to use the absolute difference in RMSE between the two groups (|RMSE_warm - RMSE_cold|). This was because I knew that a larger value would suggest a that there is something not fair in model performance across the two climate categories.

**Significance Level (α):** The significance level (α) was set to 0.05. 

**P-Value:**: 0.51. The p-value of 0.51 means that there's a 51% chance of observing the absolute difference in RMSE that we did (or larger) due to random variation alone, assuming there's no actual difference in the model's performance for 'warm' versus 'cold' climates.

**Conclusion:** Because my p-value (0.51) is much higher than the significance level (0.05), I fail to reject the null hypothesis. This means there is not enough statistical evidence for me to conclude that there is a significant difference in model performance between 'warm' and 'cold' climate categories. From my permutation test, the model appears to perform with fairness across these two climate categories in terms of prediction errors as measured by RMSE. 


