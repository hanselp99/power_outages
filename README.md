# Regional Effects on Power Outages

This is a project for DSC 80 at UCSD

By Hansel Puthenparambil

## Introduction

In this project, I set on to examine a dataset on major power outages in the United States from January 2000 to July 2016. This dataset is taken from the Purdue University's Laboratory for Advancing Sustainable Critical Infrastructure. From this dataset, there are about 1534 rows to look through along with 56 columns. Within this dataset, it retains several bounds of information including the regions the outages occurred from, the general duration and occurrence, general population information per area and the effects on customers and industries. 

The main aspect of this dataset I wish to find out is how climate can be predicted from this measure and how these sparks of. The reason for its importance is because climates can have an unique effect on the infrastructure in which windy areas can cause power shutdowns and potential warm seasons can lead to dangers in fire. By looking into this deeper, we can see a potential connection within climate and power outages which can be detrimental in predicting on whether you should be prepared for power outages given the climate of your area.

The main columns I will be focusing will be: 

| Column  | Description |
| ------------- | ------------- |
| Year  | Year when Power outage occurred  |
| Month  | Month when power outage occurred  |
| US State  | US State when power outage occurred  |
| NERC Region  | NERC region when power outage occurred  |
| Climate Region  | Climate region when power outage occurred  |
| Anomaly Level  | Oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season   |
| Climate Category  | Represents the climate episodes  |
| Outage Start Date  | Date the outage started  |
| Outage Start Time  | Time the outage started  |
| Outage Restoration Date  | Date the outage restored  |
| Outage Restoration Time  | Time the outage restored  |
| Cause Category  | Cause of the outage  |
| Cause Category Detail  | Detailed cause of the outage  |
| Outage Duration  | The total time of the power outage  |
| Population  | Number of people living in the area  |

## Data Cleaning and Exploratory Data Analysis

### Cleaning

For cleaning I decided to first drop the columns I was not interested in and focus on the columns I had. This left me with the following columns: 'YEAR', 'MONTH', 'U.S._STATE', 'NERC.REGION', 'CLIMATE.REGION','ANOMALY.LEVEL', 'CLIMATE.CATEGORY', 'OUTAGE.START.DATE', 'OUTAGE.START.TIME', 'OUTAGE.RESTORATION.DATE', 'OUTAGE.RESTORATION.TIME', 'CAUSE.CATEGORY', 'CAUSE.CATEGORY.DETAIL', 'OUTAGE.DURATION', 'POPULATION'.

After this process, there were still some unnecessary columns that were relevant, but needed to be edited. For instance, for OUTAGE_START.TIME and OUTAGE_START.DATE I decided to combine them into a pd.Timestamp object type in order to make the values much more easier and useful. I did the same thing with OUTAGE.RESTORATION.DATE and OUTAGE.RESTORATION.TIME

### Exploratory Data Analysis

#### Univariate Analysis

<iframe
  src="assets/climate_region_count_fig.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/NERC_region_avg_fig.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Bivariate Analysis

<iframe
  src="assets/bivar_climate_cat_years_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/bivar_climate_year_outage.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Grouping and Aggregation

## Assessment of Missingness
### NMAR Analysis
Within this dataset, there are a few values that are missing within this dataframe. For instance, 9 values from Month and Climate Region are missing which is likely due to certain regions. This is due to an NERC regoin, ASCC which lacks most relevant data points in the dataset along with WSCC which lacks its Month and Outage Restoration. Due to this, these values have been imputed or deleted in order to maintain relevant information. Primarily very few values have been missing on these columns which likely induces that it is not dependent on another column.

### Missing Dependency
However, one key factor that I would like to take a look at is OUTAGE.DURATION due to the several missing values it seems to have and its potential dependence on other columns.

Here I would like to test for its Missingness by comparing it to two columns: Climate Category and Year.

#### Climate Category

<iframe
  src="assets/climate_category_missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/tvds_missing1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Year

<iframe
  src="assets/year_missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/yeartvds.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Hypothesis Testing

<iframe
  src="assets/hyp1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/hyp2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Framing a Prediction Problem
### Problem Identification
My model will try to predict when the climate category is either warm, cold, or normal. Due to the number of 

I decided to use F1 score to evaluate my model because In addition, due to the balance provided by the f1 score on both precision and recall, it can help lower the class imbalance within my model in which there are far more counts of normal compared to warm and cold.
## Baseline Model
My baseline model was a decision tree classifier model using the features Climate Region, Year, and Outage Duration. I believe my current model is good because it doesn't

My baseline model included Climate Region, Year, and Outage Duration


## Final Model



## Fairness Analysis
For my fairness analysis, I decided to make my groups to be between the more extreme seasons (Summer and Winter) versus the less extreme seasons (Fall and Spring). I decided on these group because, the seasons will have a huge impact on depe

**Null Hypothesis:** The model is fair, in which the F1 scores for extreme and moderate seasons are roughly the same.

**Alternate Hypothesis:** The model is not fair, in whic the F1 scores for extreme seasons are significantly greater than the F1 scores for the moderate seasons.
