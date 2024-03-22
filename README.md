# Step 1 | Introduction

### Dataset

| climate_region     | climate_category   | outage_start_date         | outage_start_time   | outage_restoration_date    | outage_restoration_time   | cause_category     |   outage_duration |   customers_affected |   total_sales | us_state   |   total_customers |
|:-------------------|:-------------------|:--------------------------|:--------------------|:---------------------------|:--------------------------|:-------------------|------------------:|---------------------:|--------------:|:-----------|------------------:|
| East North Central | normal             | Friday, July 01, 2011     | 5:00:00 PM          | Sunday, July 03, 2011      | 8:00:00 PM                | severe weather     |              3060 |                70000 |   6.56252e+06 | Minnesota  |           2595696 |
| East North Central | normal             | Sunday, May 11, 2014      | 6:38:00 PM          | Sunday, May 11, 2014       | 6:39:00 PM                | intentional attack |                 1 |                  nan |   5.28423e+06 | Minnesota  |           2640737 |
| East North Central | cold               | Tuesday, October 26, 2010 | 8:00:00 PM          | Thursday, October 28, 2010 | 10:00:00 PM               | severe weather     |              3000 |                70000 |   5.22212e+06 | Minnesota  |           2586905 |
| East North Central | normal             | Tuesday, June 19, 2012    | 4:30:00 AM          | Wednesday, June 20, 2012   | 11:00:00 PM               | severe weather     |              2550 |                68200 |   5.78706e+06 | Minnesota  |           2606813 |
| East North Central | warm               | Saturday, July 18, 2015   | 2:00:00 AM          | Sunday, July 19, 2015      | 7:00:00 AM                | severe weather     |              1740 |               250000 |   5.97034e+06 | Minnesota  |           2673531 |

This dataset provides insight into the frequency, causes, and impacts of major power outages across different regions and climates in the US from January 2000 to July 2016.

### Project Focus

The question I focus on in this project is: Can we predict the total number of customers affected by a power outage based on outage durations, climate categories, andd geographical regions?





# Step 2 | Data Cleaning and Exploratory Data Analysis

<iframe
  src="cause_category_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


# Step 3 | Assessment of Missingness
# Step 4 | Hypothesis Testing
# Step 5 | Framing a Prediction Problem
# Step 6 | Baseline Model
# Step 7 | Final Model
# Step 8 | Fairness Analysis
