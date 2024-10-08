# Regression Analysis on SARS-CoV-2 RNA concentrations measured in NYC Wastewater

This project aims to utilize API building to source relevant data, SQL to create a database with tables to store, manipulate, and discover insights about this dataset, Pandas & Matplotlib to create visuals to gain insight into the trends of COVID-19 infection rates over time, & a Linear Regression Model using scikit-learn to predict the trend of future SARS-CoV-2 concentrations in NYC wastewater.

## Dataset

The dataset used in this project is sourced from NYC OpenData and contains the testing dates, locations, SARS-CoV-2 concentrations, annotations, etc., which are important in measuring the trends over time. For a comprehensive description of this dataset, please refer to the documentation source found [here](https://data.cityofnewyork.us/Health/SARS-CoV-2-concentrations-measured-in-NYC-Wastewat/f7dc-2q9f).

## Data Context

The analysis of this project covered the time period of 2020 - 2021. Data is updated monthly. Results of sampling to determine the SARS-CoV-2 N gene levels in NYC DEP Wastewater Resource Recovery Facility (WRRF) influent, disaggregated by the WRRF where the sample was collected, date sample was collected, and date sample was tested. This data contains sampling from multiple locations throughout NYC, and is appropriately labeled.

**Important Note:** Although SARS-CoV-2 is the virus that causes COVID-19 cases, concentrations in wastewater are not the same as COVID-19 Case Rates and should be treated separately. In this project, I explore the commonalities between the infectious cases reported in media and the amount of gene levels prevalent in the wastewater. RT-qPCR was changed to digital PCR in April of 2023, resulting in values that are about 10-20 times higher than those of RT-qPCR. Please refer to the supporting documentation for more technical information.

## Hypothesis

During the height of the COVID-19 pandemic in New York City, we had skyrocketing cases of COVID-19 infections during the winter months, and diminishing cases as we got closer to spring and summertime. While COVID-19 case diagnoses are not the same as SARS-CoV-2 concentrations in wastewater, there is more than likely a correlation between rising cases and the amount of genetic material prevalent in wastewater. As covid cases rose, so would the concentrations of SARS-CoV-2 RNA detected in wastewater.

To test our hypothesis, we will run Data Visualizations across all areas tested & build a Linear Regression Model to predict the trend of subsequent genetic concentrations in wastewater.

## Visualization Insights

From our visualization, we can see that throughout the middle of the periods (from Dec - Feb), the concentrations of the genetic material were at an all-time high relative to the beginning and end months throughout all locations.

## Regression Model

A Stochastic Gradient Descent Regression was used to generate a prediction based on the continuous data points. An n<sup>th</sup> Order Polynomial Regression was then used to compare and provide predictions during peak and subsequent dips and to predict annual SARS-CoV-2 concentration trends. Ridge and Lasso Polynomial Regression were used and subsequently compared to a Random Forests Regression.

## Model Evaluation

Investigating half of our data, our SGD Regressor Model boasted an MSE of **22736025.9454** and an R<sup>2</sup> score of 0.7230. Our Polynomial Regression Modal Improved upon the accuracy, boasting an MSE of **21662835.6459** and an R<sup>2</sup> score of **0.7361**. Our SGD model performed poorly for the full data, with a Mean Squared Error score of **121419306.8589** and an R<sup>2</sup> score of **-0.6690**. 

From our Polynomial Regression model, we were able to predict the entire time period with a Mean Squared Error of **18388011.0064** and an R<sup>2</sup> score of **0.7472**.

Applying our Polynomial Regression to all 14 WFFR sites gave us a diverse application of Regression lines, with an average MSE of **28080748.8819** and an average R<sup>2</sup> score of **0.6238**.

Applying both a pre-trained Polynomial Lasso Regression and a Random Forests Regression, we improved our R<sup>2</sup> scores marginally, boasting an average of **0.6566** and **0.8709**, respectively. However, the latter is much more susceptible to overfitting.

## Conclusion

Our visualization clearly shows that SARS-CoV-2 concentrations rise during the winter months and fall as we move away from the wintertime, which is in tandem with the rise and fall of COVID-19 cases throughout New York City. As our Linear Regression Model shows, SARS-CoV-2 concentrations in the wastewater will continue to rise as winter draws near. Concurrently, we know that the COVID-19 rate has exponentially increased over time, so we need to adjust our model to make an accurate prediction beyond a steady increase.

This modeling method can be applied to all 14 locations where the genetic material for SARS-CoV-2 was measured to create predictions of COVID-19 infection rates throughout NYC. However, as these plots are inherently not linear, linear predictive models will not be the best method of predicting SARS-CoV-2 data points unless we apply an extraordinary amount of SGD best-fit lines similar to how we would when taking derivatives. Our n<sup>th</sup> Order Lasso Polynomial Regression and Random Forests Regression created significantly more accurate representations of wastewater concentrations and could be applied to the fluctuations of SARS-CoV-2 concentrations over a more extended period.
