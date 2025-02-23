# Car Price Optimization 

# 1.Introduction
## Research Background
Understanding key factors influencing car pricing is critical for manufacturers to target
distinct market segments. Pricing categories (Low, Mid, and High) depend on various
vehicle features, and identifying patterns can lead to improved market strategies. The
goal of this project is to uncover relationships between these factors and pricing.

## Data Description

![image](https://github.com/user-attachments/assets/13618461-9917-4ccf-b6c2-e68e25c05cb3)

The dataset includes information on 11,000 cars produced from 1990 to 2017. The
dataset used for this analysis includes detailed car specifications such as MSRP (price),
engine performance, fuel efficiency, and so on. The response variable is MSRP,
categorized into three groups using 33% and 67% quantile thresholds to define the
categories.


### Challenges
1. Skewed Distribution: The MSRP and several numerical features exhibit significant
skewness, making the data less uniform and potentially challenging for analysis.
2. Outliers: The dataset includes extreme luxury vehicles with high MSRP and
horsepower values and electric vehicles with zero cylinders and high MPG, requiring
careful preprocessing.
3. Feature Relationships: Strong correlations, such as Year and MSRP (r = 0.7),
Highway MPG and City MPG (r = 0.93), and Engine Cylinders and MPG (r = -0.7),
highlight key trends that require careful interpretation.

![image](https://github.com/user-attachments/assets/ea6d2bea-03c8-4582-b727-f92af948da51)

These factors require careful preprocessing to ensure the accuracy and reliability of
analysis.

# 2. Methods and Results & Interpretation
## A. Data Preprocessing
The original dataset contained 105 missing values, which were removed during
preprocessing. Outliers associated with electric vehicles, such as 0 cylinders and high
MPG, were retained for analysis. However, extreme luxury car outliers, characterized by
high horsepower (HP) and high MSRP , were excluded using the Interquartile Range
(IQR) method. To address skewed distributions, a log transformation was applied to
both the MSRP and other skewed numerical features. Scaling and standardization were
then performed to ensure consistency across all numerical variables, enhancing the
performance of predictive models. Finally, the dataset was reduced to 3,000 samples to
optimize computational efficiency while preserving representativeness for analysis.

## B. MANOVA

![image](https://github.com/user-attachments/assets/158848a3-e657-4190-908d-7993ef404a4f)

To assess the suitability of the dataset for MANOVA and LDA, key assumptions were
evaluated. Normality was examined using Q-Q plots and the Anderson-Darling test,
which revealed significant deviations from univariate and multivariate normality.

![image](https://github.com/user-attachments/assets/fca004ea-b143-431e-b379-48a741c07e50)

Homogeneity of covariance matrices was tested using Box's M test, where the small p-
value indicated a violation of this assumption. Despite these issues, MANOVA was
conducted, showing an extremely small p-value (<2.2e-16), which led to rejecting the
null hypothesis and concluding significant differences in the mean vectors across MSRP
groups (Low, Mid, High). However, due to non-normality and unequal covariance, the
robustness of MANOVA and LDA results is limited.

## C. PCA

![image](https://github.com/user-attachments/assets/1a1caf27-75c9-41de-9be2-992c24798be0)
![image](https://github.com/user-attachments/assets/192f29a1-0cf1-4eba-9a4c-f2f735f92ed1)

The Principal Component Analysis (PCA) was conducted to reduce the dimensionality
of the dataset while retaining most of the variance. The first three principal components
(PC1, PC2, and PC3) were selected based on the eigenvalues greater than 1 and the
scree plot, explaining 81% of the total variance.
PC1 (41.14% variance) represents vehicle price and performance characteristics such
as MSRP, engine horsepower, and year. PC2 (27.61% variance) highlights efficiency-
related features like city and highway MPG, while PC3 captures additional minor
variances. The biplot further illustrates the variable contributions to these components,
with longer arrows indicating stronger influences on the principal components. These
results provide a compact yet comprehensive representation of the original dataset,
facilitating further analysis.

## D. Factor Analysis

![Screenshot 2025-02-22 at 11 28 00 PM](https://github.com/user-attachments/assets/dd94e410-6f52-45a6-abb9-aaa20eac33e2)

Factor analysis determined that four factors were sufficient to explain 81% of the
variance in the dataset. The number of factors was decided based on cumulative
variance exceeding 80% and the elbow point observed in the scree plot, where
additional factors contributed minimal variance.

![image](https://github.com/user-attachments/assets/c79a4878-7bad-4e0e-af5f-9d81098e515d)

The identified factors were interpreted as follows: Factor 1 represents fuel efficiency,
with high MPG and low engine cylinders indicating better efficiency. Factor 2 reflects
power and price, capturing high engine horsepower and MSRP associated with
performance-focused vehicles. Factor 3 highlights market popularity, where cars with
higher popularity scores are widely favored. Lastly, Factor 4 describes basic
specifications, linked to newer models with more doors scoring higher on this factor.

## E. Cluster Analysis
The optimal number of clusters was determined to be 3, as identified by the elbow point
in the within-cluster sum of squares (WCSS) plot. The addition of the third cluster
significantly improved the model by reducing WCSS substantially, indicating well-
defined group separations.

![image](https://github.com/user-attachments/assets/5826b18e-d83f-481a-8e87-5b83d07ce4c0)

Each cluster, represented by unique visualizations like faces and stars, highlights
distinct traits influenced by variables such as engine horsepower, year, MPG, and
popularity. The K-Means and cluster plots visually reinforce this separation, displaying
three well-defined clusters, accounting for 68.7% of the variance in the dataset. This
dimensional reduction ensures effective analysis while retaining critical distinctions
across the groups.

## Conclusion
In this analysis, we provided clear insights into clusters and pricing patterns that
manufacturers can utilize to target distinct market segments. PCA revealed that the first
three components explained 81% of the variance, capturing vehicle pricing,
performance, and efficiency traits, while Factor Analysis identified four meaningful
dimensions influencing vehicle attributes. K-Means clustering effectively grouped
vehicles into three distinct clusters based on their shared characteristics, explaining
68.7% of the variance. However, traditional methods like MANOVA and LDA were less
effective due to unmet assumptions of normality and homogeneity. Despite these
limitations, the analysis highlights valuable segmentation and feature trends, offering
actionable guidance for automotive market strategies.
