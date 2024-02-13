# Japan_earthquake
A sudden, intense shaking of the ground brought on by the movement of tectonic plates beneath the surface of the earth is known as an earthquake. The shaking experienced at the surface is caused by seismic waves created by this movement and their propagation through the Earth.

Causes of Earthquake

An earthquake is caused by plates moving beneath the earth; these plate movements are caused by stress and force along the faultlines where the plates meet. A fault is a fracture or zone of fractures between two blocks of rock. When there is sudden movement or slippage within this fault zone, an earthquake may occur. An earthquake may also occur at the subduction zone. A subduction zone occurs at the convergent plate boundary when a plate is forced beneath another plate, and the pressure can lead to an earthquake. Other causes of earthquakes are: volcanic activity, collapse of underwater caves, meteorite impacts, etc.

Japan Earthquake: Every year, Japan experiences about 1,500 earthquakes, the majority of which are too small to be felt. The Pacific Plate off the east coast of Japan moves beneath another plate, resulting in the majority of the country’s significant earthquakes. The numerous earthquakes experienced by Japan are a result of its unique geological and tectonic setting. Japan is situated at the convergence of several plate boundaries, and these plates interact along the subduction zone, transform faults and collision zones.

Japan earthquake data analysis

i. Data Collection: To analyze earthquake data in Japan, we scraped earthquake data from worlddata.info using Selenium, a web scraping tool. The dataset includes information such as the date, region, depth, magnitude, deaths, and total damage for each earthquake event.

A total of 171 earthquake events were recorded in the dataset, spanning from 1952 to 2024. The dataset was then stored as a CSV file.

I examined the data types of each column using the .dtypes attribute to understand the format of the data.
Data Preprocessing

I converted the ‘Date’ column to datetime format using the pd.to_datetime() function to ensure consistency and enable date-based analysis.
The ‘Magnitude’ column was converted to numeric format using the pd.to_numeric() function with the errors='coerce' parameter to handle non-numeric values gracefully.
The ‘Depth’ column was processed to extract the numerical depth values and converted to float format by removing the ‘km’ suffix and using the astype(float) method.
I dropped the ‘Unnamed: 0’ column, which appeared to be an unnecessary index column, using the .drop() method with the axis=1 parameter.
Missing values in the ‘Total damage’ column were filled with the mean value of the column using the .fillna() method to ensure data completeness.
Descriptive statistics such as count, mean, standard deviation, minimum, maximum, and quartiles were calculated for numerical columns using the .describe() method to gain insights into the distribution of data.
I computed the correlation matrix using the .corr() method to explore the relationships between numerical variables (magnitude, deaths, and depth). There was no substantial correlation between the columns.
Visualization





Model
Data Preparation:

The earthquake dataset for Japan was prepared by converting categorical variables to numerical values using label encoding and scaling numerical features using StandardScaler. The dataset was then split into training and testing sets for modelling.
Model Selection:

Five different regression models were selected for earthquake magnitude prediction: linear regression, decision tree regression, random forest regression, KNN regression, and support vector regression (SVR).
Model Training and Evaluation:

Each regression model was trained on the training data and evaluated using several metrics:
Mean Absolute Error (MAE): Average of the absolute differences between predicted and actual magnitudes.
Mean Squared Error (MSE): Average of the squared differences between predicted and actual magnitudes.
Root Mean Squared Error (RMSE): The square root of the MSE provides a measure of the average magnitude of errors.
R-squared (R²) Score: measure of the proportion of variance in the dependent variable (magnitude) that is predictable from the independent variables.
Model Performance:

Linear Regression: showed poor performance with a negative R² score, indicating that the model did not fit the data well.
Decision Tree Regression: Improved over Linear Regression but still exhibited limited predictive power.
Random Forest Regression: Outperformed other models with the lowest MAE, MSE, and RMSE and the highest R² score, indicating better predictive accuracy and model fit.
KNN Regression: Performed relatively poorly compared to other models, especially in terms of RMSE and R² score.
SVR: showed moderate performance, with comparable results to decision tree regression but worse than random forest regression.
Residual Analysis:

Residual analysis for Random Forest Regression showed a relatively random distribution of residuals, indicating that the model’s errors were unbiased and evenly distributed.

Actual vs. Predicted Magnitudes:


Inferences and Observations:

Random Forest Regression emerged as the best-performing model for earthquake magnitude prediction, followed by SVR and Decision Tree Regression.
Linear regression and KNN regression showed comparatively weaker performance, suggesting that the linear relationship assumption might not hold well for the data and that the KNN approach might not be suitable for this type of data.
The results indicate that ensemble methods like Random Forest can effectively model the complex relationships between earthquake features and magnitude, outperforming simpler regression techniques.




