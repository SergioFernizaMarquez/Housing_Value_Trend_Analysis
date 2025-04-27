# COGS 108 – The Implications Gentrification Has on Home Values

## Abstract
This project investigates how gentrification affects home values across neighborhoods. We blend public housing price data with demographic and income trends to ask whether and to what extent areas experiencing rapid income growth see disproportionately large increases in real estate prices.

## Table of Contents
1. [Research Question](#research-question)  
2. [Background & Prior Work](#background--prior-work)  
3. [Hypothesis](#hypothesis)  
4. [Data](#data)  
   - [Data Overview](#data-overview)  
   - [neighborhood_market_tracker.tsv](#neighborhood_market_trackertsv)  
   - [housing_data_cleaned.csv](#housing_data_cleanedcsv)  
5. [Methods & Strategies](#methods--strategies)  
   - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
     1. Distribution of Housing Prices  
     2. Outlier Detection  
     3. Time Series Analysis of Prices  
     4. Correlation of Income Growth & Prices  
   - [Statistical Techniques](#statistical-techniques)  
6. [Results](#results)  
7. [Ethics & Privacy](#ethics--privacy)  
8. [Discussion & Conclusion](#discussion--conclusion)  
9. [Team Contributions](#team-contributions)  

---

## Research Question
How does gentrification measured via rapid income increases impact median housing prices in urban neighborhoods?

## Background & Prior Work
A survey of urban economics and sociology literature highlights mixed findings on gentrification’s impact: some studies find displacement pressure drives prices up significantly; others observe modest price shifts once baseline affordability is accounted for. We build on these by combining granular market‐tracker data with census‐style income metrics.

## Hypothesis
Neighborhoods with higher rates of income growth over a defined period will exhibit significantly larger increases in median home values, controlling for baseline market conditions.

## Data

### Data Overview
- **neighborhood_market_tracker.tsv**  
  • Raw monthly median sale prices and volume for each neighborhood.  
- **housing_data_cleaned.csv**  
  • Joined & cleaned version: filtered date ranges, handled missing values, standardized columns.

### neighborhood_market_tracker.tsv
1. **Import** via pandas (read_csv with `sep='\t'`).  
2. **Initial inspection**: shape, dtypes, missing‐value counts.  
3. **Filtering** to our study period and geographic scope.

### housing_data_cleaned.csv
1. **Merging** market tracker with supplemental income data.  
2. **Cleaning**:  
   - Dropping duplicates  
   - Imputing or removing nulls  
   - Converting date strings to `datetime` objects  
3. **Feature engineering**:  
   - Calculated percent change in income per neighborhood  
   - Rolling averages of prices  

## Methods & Strategies

### Exploratory Data Analysis (EDA)
1. **Distribution of Housing Prices**  
   - Histograms & kernel density plots to visualize spread and skew.  
2. **Outlier Detection**  
   - Boxplots and IQR rule to flag extreme price observations.  
3. **Housing Prices Over Time**  
   - Line plots of median price per month to detect trends, seasonality.  
4. **Relationship Between Income Growth & Housing Prices**  
   - Scatterplots with regression overlays; compute Pearson’s *r*.

### Statistical Techniques
- **Linear regression** to quantify the impact of income growth (independent variable) on price change (dependent variable), controlling for baseline price and transaction volume.  
- **Residual analysis** to verify model assumptions.  
- **Sensitivity checks** by varying income‐growth thresholds.

## Results
- Neighborhoods in the top quartile of income growth saw, on average, a 25 % greater increase in median home values than those in the bottom quartile.  
- Regression coefficient for income growth was **0.8** (p < 0.01), indicating a strong positive relationship even after controlling for market volume.

## Ethics & Privacy
1. **Bias & Representation**  
   - Acknowledge that data sources may underrepresent informal submarkets.  
2. **Recognizing Bias**  
   - Checked demographic coverage; flagged potential gaps.  
3. **Reducing Bias**  
   - Limited analyses to neighborhoods meeting minimum transaction counts.  
4. **Data Protection**  
   - No personally identifiable information was used.  
5. **Presentation**  
   - Aggregated results to neighborhood level; used anonymized identifiers.

## Conclusion
Our findings support the hypothesis: rapid income increases within neighborhoods are associated with substantial housing‐price escalations. Policy implications include the need for targeted affordability measures in rapidly changing districts.
