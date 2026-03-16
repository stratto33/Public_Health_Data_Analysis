# Public_Health_Data_Analysis

This project analyzes public health survey data from the CDC Behavioral Risk Factor Surveillance System (BRFSS) to explore relationships between demographic characteristics, lifestyle factors, and health outcomes.

## Objectives

- Perform exploratory data analysis on public health survey data
- Identify trends and relationships between demographic and health variables
- Build regression models to predict health outcomes

## Tools & Technologies

- R
- dplyr
- ggplot2
- Statistical modeling

## Dataset

The dataset used in this project comes from the CDC Behavioral Risk Factor Surveillance System (BRFSS).

Due to file size limitations, the full dataset is not included in this repository.

It can be downloaded here:

https://www.cdc.gov/brfss/annual_data/annual_2021.html

## Key Analysis

- Data cleaning and preprocessing
- Exploratory data analysis
- Visualization of health trends
- Regression modeling

## Example Insights

- Engineered variables: HEIGHT_IN, WEIGHT_LB, FRY_DAY, SALAD_DAY
- Used the engineered variables in a linear regression model to predict the participant's weight in pounds.
-  first checked to make sure all of my predictors were significant by looking at each p-value. Every p-value in all models were listed as less than 2 x 10-16. This tells me each predictor is significant because each p-value is less than 0.05. So, each predictor is a valid predictor. Next, I looked at the adjusted R2 value and the AIC value for each model to help assess which model would be the best. The adjusted R2 and AIC values for each model are below:

Model

Predictor(s)

Adjusted R2

AIC

weight_mod1

HEIGHT_IN

0.2343

3,564,682

weight_mod2

HEIGHT_IN, FRY_DAY

0.2357

3,564,024

weight_mod3

HEIGHT_IN, FRY_DAY, SALAD_DAY

0.2387

3,562,626

Since weight_mod3 has the largest adjusted R2 value (barely), my initial thought was that it was the strongest of the three models. To help verify this, I looked at the AIC of each model. weight_mod1 has the largest AIC value, indicating it could be the strongest of the three models. I decided to go with weight_mod3 as the strongest model since it has the higher adjusted R2 value and the AIC values are marginally different. The adjusted R2 value is easier to interpret and it explains the variation in weight by all the predictors in the model. The adjusted R2 is also (generally) the industry standard according to a friend in the data analysis field.

I also looked at the standardized coefficients to compare the predictors to each other. This gives me a way to rank them by importance. Each variable's standardized coefficient is in the table below:

Variable

Standardized Coefficients

HEIGHT_IN

0.4786

FRY_DAY

0.0396

SALAD_DAY

-0.0549

Based on the values of the standardized coefficients, HEIGHT_IN is the strongest predictor of the three variables since it has the largest (in magnitude) value. This also makes sense with the values in the correlation matrix, corr_matrix. Based on the values in the matrix, HEIGHT_IN and WEIGHT_LB have the strongest correlation since their value of r is the largest (in magnitude) at 0.4841.

## Author

Michael Stratton
