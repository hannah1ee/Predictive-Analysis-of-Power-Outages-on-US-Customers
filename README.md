# Step 1 | Introduction

### Project Focus

The question I focus on in this project is: Can we predict the total number of customers affected by a power outage based on outage durations, climate categories, and geographical regions?

### Dataset Overview

| OBS | YEAR | MONTH | U.S.\_STATE | POSTAL.CODE | NERC.REGION | CLIMATE.REGION     | ANOMALY.LEVEL | CLIMATE.CATEGORY | OUTAGE.START.DATE         | OUTAGE.START.TIME | OUTAGE.RESTORATION.DATE    | OUTAGE.RESTORATION.TIME | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL | HURRICANE.NAMES | OUTAGE.DURATION | DEMAND.LOSS.MW | CUSTOMERS.AFFECTED | RES.PRICE | COM.PRICE | IND.PRICE | TOTAL.PRICE |   RES.SALES |   COM.SALES |   IND.SALES | TOTAL.SALES | RES.PERCEN | COM.PERCEN | IND.PERCEN | RES.CUSTOMERS | COM.CUSTOMERS | IND.CUSTOMERS | TOTAL.CUSTOMERS | RES.CUST.PCT | COM.CUST.PCT | IND.CUST.PCT | PC.REALGSP.STATE | PC.REALGSP.USA | PC.REALGSP.REL | PC.REALGSP.CHANGE | UTIL.REALGSP | TOTAL.REALGSP | UTIL.CONTRI | PI.UTIL.OFUSA | POPULATION | POPPCT_URBAN | POPPCT_UC | POPDEN_URBAN | POPDEN_UC | POPDEN_RURAL | AREAPCT_URBAN | AREAPCT_UC | PCT_LAND | PCT_WATER_TOT | PCT_WATER_INLAND |
| --: | ---: | ----: | :---------- | :---------- | :---------- | :----------------- | ------------: | :--------------- | :------------------------ | :---------------- | :------------------------- | :---------------------- | :----------------- | :-------------------- | --------------: | --------------: | -------------: | -----------------: | --------: | --------: | --------: | ----------: | ----------: | ----------: | ----------: | ----------: | ---------: | ---------: | ---------: | ------------: | ------------: | ------------: | --------------: | -----------: | -----------: | -----------: | ---------------: | -------------: | -------------: | ----------------: | -----------: | ------------: | ----------: | ------------: | ---------: | -----------: | --------: | -----------: | --------: | -----------: | ------------: | ---------: | -------: | ------------: | ---------------: |
|   1 | 2011 |     7 | Minnesota   | MN          | MRO         | East North Central |          -0.3 | normal           | Friday, July 01, 2011     | 5:00:00 PM        | Sunday, July 03, 2011      | 8:00:00 PM              | severe weather     | nan                   |             nan |            3060 |            nan |              70000 |      11.6 |      9.18 |      6.81 |        9.28 | 2.33292e+06 | 2.11477e+06 | 2.11329e+06 | 6.56252e+06 |    35.5491 |     32.225 |    32.2024 |       2308736 |        276286 |         10673 |         2595696 |      88.9448 |       10.644 |       0.4112 |            51268 |          47586 |        1.07738 |               1.6 |         4802 |        274182 |     1.75139 |           2.2 |    5348119 |        73.27 |     15.28 |         2279 |    1700.5 |         18.2 |          2.14 |        0.6 |  91.5927 |       8.40733 |          5.47874 |
|   2 | 2014 |     5 | Minnesota   | MN          | MRO         | East North Central |          -0.1 | normal           | Sunday, May 11, 2014      | 6:38:00 PM        | Sunday, May 11, 2014       | 6:39:00 PM              | intentional attack | vandalism             |             nan |               1 |            nan |                nan |     12.12 |      9.71 |      6.49 |        9.28 | 1.58699e+06 | 1.80776e+06 | 1.88793e+06 | 5.28423e+06 |    30.0325 |    34.2104 |    35.7276 |       2345860 |        284978 |          9898 |         2640737 |      88.8335 |      10.7916 |       0.3748 |            53499 |          49091 |        1.08979 |               1.9 |         5226 |        291955 |        1.79 |           2.2 |    5457125 |        73.27 |     15.28 |         2279 |    1700.5 |         18.2 |          2.14 |        0.6 |  91.5927 |       8.40733 |          5.47874 |
|   3 | 2010 |    10 | Minnesota   | MN          | MRO         | East North Central |          -1.5 | cold             | Tuesday, October 26, 2010 | 8:00:00 PM        | Thursday, October 28, 2010 | 10:00:00 PM             | severe weather     | heavy wind            |             nan |            3000 |            nan |              70000 |     10.87 |      8.19 |      6.07 |        8.15 | 1.46729e+06 | 1.80168e+06 |  1.9513e+06 | 5.22212e+06 |    28.0977 |     34.501 |     37.366 |       2300291 |        276463 |         10150 |         2586905 |      88.9206 |       10.687 |       0.3924 |            50447 |          47287 |        1.06683 |               2.7 |         4571 |        267895 |     1.70627 |           2.1 |    5310903 |        73.27 |     15.28 |         2279 |    1700.5 |         18.2 |          2.14 |        0.6 |  91.5927 |       8.40733 |          5.47874 |
|   4 | 2012 |     6 | Minnesota   | MN          | MRO         | East North Central |          -0.1 | normal           | Tuesday, June 19, 2012    | 4:30:00 AM        | Wednesday, June 20, 2012   | 11:00:00 PM             | severe weather     | thunderstorm          |             nan |            2550 |            nan |              68200 |     11.79 |      9.25 |      6.71 |        9.19 | 1.85152e+06 | 1.94117e+06 | 1.99303e+06 | 5.78706e+06 |    31.9941 |    33.5433 |    34.4393 |       2317336 |        278466 |         11010 |         2606813 |      88.8954 |      10.6822 |       0.4224 |            51598 |          48156 |        1.07148 |               0.6 |         5364 |        277627 |     1.93209 |           2.2 |    5380443 |        73.27 |     15.28 |         2279 |    1700.5 |         18.2 |          2.14 |        0.6 |  91.5927 |       8.40733 |          5.47874 |
|   5 | 2015 |     7 | Minnesota   | MN          | MRO         | East North Central |           1.2 | warm             | Saturday, July 18, 2015   | 2:00:00 AM        | Sunday, July 19, 2015      | 7:00:00 AM              | severe weather     | nan                   |             nan |            1740 |            250 |             250000 |     13.07 |     10.16 |      7.74 |       10.43 | 2.02888e+06 | 2.16161e+06 | 1.77794e+06 | 5.97034e+06 |    33.9826 |    36.2059 |    29.7795 |       2374674 |        289044 |          9812 |         2673531 |      88.8216 |      10.8113 |        0.367 |            54431 |          49844 |        1.09203 |               1.7 |         4873 |        292023 |      1.6687 |           2.2 |    5489594 |        73.27 |     15.28 |         2279 |    1700.5 |         18.2 |          2.14 |        0.6 |  91.5927 |       8.40733 |          5.47874 |

This dataset provides insight into the frequency, causes, and impacts of major power outages across different regions and climates in the US from January 2000 to July 2016. It has 56 columns, and 1534 total rows. The columns that are relevant to my question specifically are  `CLIMATE.REGION`, `CLIMATE.CATEGORY`, `OUTAGE.START.DATE`, `OUTAGE.START.TIME`, `OUTAGE.RESTORATION.DATE`, `OUTAGE.RESTORATION.TIME`, `CAUSE.CATEGORY`, `OUTAGE.DURATION`, `CUSTOMERS.AFFECTED`, `TOTAL.SALES`, `U.S._STATE`, and `TOTAL.CUSTOMERS`.

### Relevance

Readers of this website should care about the dataset and the specific question about predicting total number of customers affected by power outage because of the impact of power outages on individuals and businesses. Power outages can disrupt daily life and affect business operations leading to significant economic and social consequence. 

Have you ever had delicious leftovers in your fridge or a week's full of groceries but had to throw them out because the power went out for a couple hours? Understanding the patterns and causes of power outages can provide valuable insights to not have that happen again.


# Step 2 | Data Cleaning and Exploratory Data Analysis

### Cleaned DataFrame

| outage_start        | outage_restored     |   outage_duration | outage_season   | outage_month   | cause_category     | us_state   | climate_region     | climate_category   | customers_affected   |   total_customers |   total_sales |
|:--------------------|:--------------------|------------------:|:----------------|:---------------|:-------------------|:-----------|:-------------------|:-------------------|:---------------------|------------------:|--------------:|
| 2011-07-01 17:00:00 | 2011-07-03 20:00:00 |              3060 | Summer          | July           | severe weather     | Minnesota  | East North Central | normal             | 70000                |           2595696 |       6562520 |
| 2014-05-11 18:38:00 | 2014-05-11 18:39:00 |                 1 | Spring          | May            | intentional attack | Minnesota  | East North Central | normal             | <NA>                 |           2640737 |       5284231 |
| 2010-10-26 20:00:00 | 2010-10-28 22:00:00 |              3000 | Autumn          | October        | severe weather     | Minnesota  | East North Central | cold               | 70000                |           2586905 |       5222116 |
| 2012-06-19 04:30:00 | 2012-06-20 23:00:00 |              2550 | Summer          | June           | severe weather     | Minnesota  | East North Central | normal             | 68200                |           2606813 |       5787064 |
| 2015-07-18 02:00:00 | 2015-07-19 07:00:00 |              1740 | Summer          | July           | severe weather     | Minnesota  | East North Central | warm               | 250000               |           2673531 |       5970339 |

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

Because my observed statistic lies outside the distribution of the permuted statistics, this suggests that there is a low probability that the observed missingness pattern could have occurred if the missingness was indeed random with respect to the `cause_category`. Therefore, the missingness could be NMAR (Not Missing at Random), meaning that the probability of missingness is related to the data itself, possibly affected by the `cause_category`. The low p-value, 0, also suggests that the observed data, the pattern of missingness in `customers_affected` relative to `cause_category`) is highly unlikely under the null hypothesis. With respect to my question, the results of the missingness permutation tests also suggest that we may be able to predict the total number of customers affected by a power outage based on outage causes. 

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
# Step 7 | Final Model
# Step 8 | Fairness Analysis
