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

After this process, there were still some unnecessary columns that were relevant, but needed to be edited. For instance, for OUTAGE_START.TIME and OUTAGE_START.DATE I decided to combine them into a pd.Timestamp object type in order to make the values much more easier and useful. I did the same thing with OUTAGE.RESTORATION.DATE and OUTAGE.RESTORATION.TIME. This dropped the following four colummns off and introduced two new ones: OUTAGE_START and OUTAGE_RESTOR.

Finally, I decided to fill in the null values of CLIMATE.REGION with No Climate Region. The reason for this is that there are still useful values with this value, which is why I wanted to acknowledge it by creating a new attrbiute for them.

### Exploratory Data Analysis

For my exploratory data analysis I want to examine the distribution of univariate and bivariate data. 

#### Univariate Analysis

For my first analysis, I want to observe the count of power outages of the climate region.

<iframe
  src="assets/climate_region_count_fig.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

For my second univariate analysis, I wanted to observe the mean of the NERC average outage_duration. I wanted to know this since I wanted to know if a region has more severe power outage duration.

<iframe
  src="assets/NERC_region_avg_fig.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Bivariate Analysis

For my first bivariate analysis, I wanted to see the time period of four years compared with the counts of power outages within each climate category. The reason for this is to see the likelihood for certain seasons of weather to cause power outages or if its more likely a normal coincedence. However, more often there were normal climates during most power outages more often than warm and cold climates. However, we can see that there was a sudden spike at 2008-2011 for cold climate in which there was a lot more comparatively to the rest.

<iframe
  src="assets/bivar_climate_cat_years_count.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

For my second bivariate analysis, I also wanted to see the time period of power outages compared to each climate region. I chose to make it a 4-year period line graph that compares Northern, Southern, and the other climate regions in order to observe any patterns in power outages over time with these two geographical areas. Surprisingly with the rising usage of electronics, there are shorter power outages overall. In addition, there was strange spike within the 2004-2007 for longer power outages.

<iframe
  src="assets/bivar_climate_year_outage.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Grouping and Aggregation

Finally, I decided to group climate region and year on anomaly level to see the average anomaly level for these actions. The reason for this is to see if certain climate regions in years have a certain climate category during these years. However, this came with many null values due to the fact that some anomaly levels didn't exist in the graph leaving them as 0.

| Column  | Description |
| ------------- | ------------- |

| 2000 | 2001 |  2002 |  2003 |     2004 |       2005 |      2006 |      2007 | 2008 |     2009 |       2010 |      2011 |       2012 |      2013 |      2014 |    2015 |     2016 |
|----------:|-------:|----------:|-----------:|---------:|-----------:|----------:|----------:|----------:|----------:|-----------:|----------:|-----------:|----------:|----------:|--------:|---------:|
| -0.6      |   0    | -0.2      |  0.283333  | 0.4      |  0.52      |  0.233333 | -0.76     | -0.620833 | -0.28     | -0.675     | -0.4975   |  0.0681818 | -0.29375  | -0.268421 | 1.26429 | 0.5      |
|  0        |   0    |  0.1      |  0.12      | 0.4      | -0.07      | -0.25     | -0.255556 | -0.63     |  0.377778 | -1.12308   | -0.517647 | -0.2125    | -0.28     | -0.294444 | 1.475   | 1.3      |
|  0        |   0    |  0        |  0         | 0        |  0         |  0.466667 |  0        | -0.7      |  0        |  0         | -0.4      |  0         |  0        |  0        | 0       | 0        |
| -0.9      |  -0.25 |  1.13333  |  0.208333  | 0.457143 |  0.0666667 | -0.0625   | -0.281818 | -0.628571 |  0.02     | -0.0642857 | -0.718072 |  0.0212121 | -0.280952 | -0.475    | 1.37273 | 1.05     |
|  0        |   0    |  0        |  0.1       | 0.233333 |  0         |  0.627273 | -0.2      | -0.5      | -0.1      | -1.4       | -0.662162 | -0.392     | -0.28     | -0.371429 | 1.325   | 1.00714  |
| -0.833333 |  -0.2  |  0.666667 | -0.0333333 | 0.363636 |  0.0909091 |  0.08     | -0.7125   | -0.4      |  0.126316 | -0.261111  | -0.606061 | -0.217391  | -0.264286 | -0.273333 | 1.39    | 0.466667 |
| -0.95     |  -0.1  |  0.95     |  0.3       | 0.534615 | -0.0333333 |  0.166667 | -0.5      | -0.871429 |  0.04     | -0.428571  | -0.59     | -0.0363636 | -0.269231 | -0.408333 | 0.85    | 0.166667 |
| -0.833333 |   0    |  0.2      |  0.1       | 0.433333 |  0.2       |  0.05     | -0.4      | -1.3      |  0.766667 | -0.65      | -0.617647 | -0.02      | -0.309091 | -0.333333 | 0.87    | 1.37143  |
| -0.7      |  -0.4  |  0.84     |  0.26      | 0.45     | -0.03      |  0.244444 | -0.566667 | -0.76087  |  0.584615 | -0.508     | -0.733333 | -0.0714286 | -0.266667 | -0.2625   | 1.22308 | 1.66     |
|  0        |   0    |  0        |  0         | 0.3      |  0         |  0.9      |  0        | -0.5      |  0.633333 | -1         | -0.766667 |  0         | -0.233333 | -0.4      | 0       | 0        |

## Assessment of Missingness
### NMAR Analysis
Within this dataset, there are a few values that are missing within this dataframe. For instance, 9 values from Month and Climate Region are missing which is likely due to certain regions. This is due to an NERC regoin, ASCC which lacks most relevant data points in the dataset along with WSCC which lacks its Month and Outage Restoration. Due to this, these values have been imputed or deleted in order to maintain relevant information. Primarily very few values have been missing on these columns which likely induces that it is not dependent on another column.

### Missing Dependency
However, one key factor that I would like to take a look at is OUTAGE.DURATION due to the several missing values it seems to have and its potential dependence on other columns.

Here I would like to test for its Missingness by comparing it to two columns: Climate Category and Year.

#### Climate Category

I examined the distribution between Climate Category when Outage Duration was missing and not missing.

**Null Hypothesis:** The distribution between Climate Category when Outage Duration was missing is the same when it was not missing.

**Alternate Hypothesis:** The distribution between Climate Category when Outage Duration was missing is not the same when it was not missing.

<iframe
  src="assets/climate_category_missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

From this bar graph, we can notice that there is a clear difference between warm and normal climates when comparing the missingness. We need to consider this factor throughout my observations. This leads to an observed tvd of 0.318, which ends with a p-value of 0.0. With this I reject the null hypothesis in which the distribution between Cliamte Category when Outage Duration was missing is not the same when it was not missing. They do not retain the same distribution meaning that Outage Duration is dependent to Climate Category

<iframe
  src="assets/tvds_missing1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Year

I examined the distribution between Year when Outage Duration was missing and not missing.

**Null Hypothesis:** The distribution between Year when Outage Duration was missing is the same when it was not missing.

**Alternate Hypothesis:** The distribution between Year when Outage Duration was missing is not the same when it was not missing.

<iframe
  src="assets/year_missing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

From this bar graph, we can notice that there is a clear difference with each year of power outages when comparing the missingness. We can see a considerably higher missing rate towards the start and end of the 16 year period while non-missing data would stay relatively consistent except from 2011-2014 which a slight increase. This leads to an observed tvd of 0.660, which ends with a p-value of 0.0. With this I reject the null hypothesis in which the distribution between Year when Outage Duration was missing is not the same when it was not missing. They do not retain the same distribution meaning that Outage Duration is dependent to Climate Category


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
My baseline model was a decision tree classifier model using the features Climate Region, Year, and Outage Duration. I believe my current model is good because it doesn't require much values, adding much more values tended to lead to an overfitting of the training model (0.93) while the testing data would get a value of 0.66.

My baseline model included Climate Region(nominal variable) since the location of the climate category would be relevant to the climate region. It also include Year (nominal variable) due to certain years having much higher climates compared to others, and Outage Duration (quantitative variable) since the data is throughly based on the data corresponding to it in which extreme values would likely be correlated with extreme climates

I believed that my DecisionTreeClassifier worked very well as my F1-score was 0.718.

## Final Model
My final model was a random forest classifier model using the features Climate Region, Year, Month, and Outage Duration. Although the slight change, based on the other values, there wasn't much to change from the baseline model than the final model. However, some notable improvements occurred especially through the inclusion of transforming Month into season and one hot encoding it. This lead to a tremondous increase on both training and test data predictions.

My final model included Climate Region(nominal variable) since the location of the climate category would be relevant to the climate region. It also include Year (ordinal variable) due to certain years having much higher climates compared to others, and Outage Duration (quantitative variable) since the data is throughly based on the data corresponding to it in which extreme values would likely be correlated with extreme climates. However, the main change that I included was Month (ordinal variable), due to the seasons it has per month allows it to be a major change.

 My RandomForestClassifier model worked very well as my F1-score was 0.883.

## Fairness Analysis
For my fairness analysis, I decided to make my groups to be between the more extreme seasons (Summer and Winter) versus the less extreme seasons (Fall and Spring). I decided on these group because, the seasons will have a huge impact on predictions as it provided a major boost during my final model. 

I will be using F1 score due to the imbalanced seasons especially with the training model in order to incorporate both precision and recall into calculations. I will be using around 10000 trials with perumation tests in order to decipher the results. My significance level will be the standard value of 0.05.

**Null Hypothesis:** The model is fair, in which the F1 scores for extreme and moderate seasons are roughly the same.

**Alternate Hypothesis:** The model is not fair, in whic the F1 scores for extreme seasons are significantly greater than the F1 scores for the moderate seasons.

After the permuatation test, my observed f1 score had a p-value of 0.0 meaning that I would reject the null hypothesis in which that the model is fair for both extreme and moderate season as the values is significantly different.
