# DSA---210-Term-Project
## Final Report: Analyzing Factors Influencing Formula 1 Race Results (2010-2024)

## Findings

### 1. Starting Grid Position vs Final Race Position
This bar chart shows the number of races won from each grid position.


*   Pole position produced the most winners (156 out of 305 races)
*   Grid position 2 follows with 79 wins, showing that the front row has a very high chance of winning.


*   The number of wins drops sharply after the first few positions.

The graph clearly shows that starting in front of the grid gives a significant advantage in Formula 1. This supports the idea that qualifying performance is highly correlated with race success.

![Grid Position of Winner](images/grid%20position%20of%20winner.png)


### 2. Number of Pit Stops vs Final Position
Pit-stop strategies play a crucial role in determining race outcomes in Formula 1. This bar chart shows how many pit stops race winners made in each Grand Prix.


*   The majority of races were won either 1 or 2 pit stops.
*   More than 2 pit stops became less and less common.

Most winning strategies in Formula 1 involve 1 or 2 pit stops, showing a balance between tire management and track position. Too few stops might sacrifice speed. And too many pit stops generally correlate with slightly worse finishing positions by wasting race time.

![Distribution of Pit Stops Among Race Winners](images/distribution%20of%20pit%20stops%20among%20race%20winners.png)


### 3. Driver Age vs Experience
Understanding the relationship between a driver's age or experience and their effectiveness in Formula 1 is crucial for teams when making strategic decisions regarding driver development and recruitment. I am going to focus on how a driver's age and experience correlates with their performance.

This line chart shows how race wins are distributed across different driver ages.


*   Most race wins happen between the ages of 23 and 32, with several sharp peaks. The highest number of wins is observed at ages 26 and 30, showing those as the peak performance ages in this period.
*   Race wins drop off after the early 30s, suggesting performance may decline slightly with age.


*   There are very few wins below age 20 or above age 36, showing that very young or much older drivers rarely win races.

Drivers tend to win the most races in their late 20s and early 30s, suggesting this age range aligns with the peak of both physical ability and racecraft experience.

![Number of Race Wins by Driver Age](images/number%20of%20race%20wins%20by%20driver%20age.png)

This chart shows how many races were won by drivers at each level of experience (measured in years since their Formula 1 debut).


*   Most wins are concentrated around 6 to 10 years of experience, peaking sharply at 8 years.
*   After that, there's a steady decline in the number of wins as drivers become more experienced.


*   Very inexperienced drivers (with 1–2 years) and very experienced ones (15+ years) have significantly fewer wins.

Drivers tend to win races when they've had 6 to 10 years of experience. This supports the idea that both familiarity with the sport and physical sharpness play a role.

![Number of Race Wins by Driver Experience](images/number%20of%20race%20wins%20by%20driver%20experience.png)

This box plot visualizes the starting grid position (y-axis) of race winners based on their years of experience grouped into bins (x-axis).


*   Drivers with 0-3 and 11-15 years of experience seem to qualify slightly better on average than the others.
*   The spread (IQR) and outliers grow slightly with experience, especially in the 7-10 group, suggesting more variability in qualifying among mid-career drivers.

There’s no sharp difference in qualifying performance across experience levels. However, newer and seasoned drivers tend to start higher up the grid, which might suggest strong rookie talent and veteran consistency - while mid-career drivers show more variation.

![Grid Position by Experience](images/grid%20position%20by%20experience.png)

This stacked histogram shows how race winners with different levels of experience are distributed across starting grid positions.


*   The majority of wins happen from the first few grid positions, regardless of experience.
*   Drivers in the 7-10 years of experience range have the most wins overall, especially from grid positions 1 and 2.


*   Interestingly, even newer drivers (0-3 years) are winning from front rows, suggesting rookies are competitive early in their careers.

Grid position strongly influences race outcomes, and mid-experience drivers (4-10 years) tend to dominate the front rows.

![Grid Position by Experience Histogram](images/grid%20position%20by%20experience%20histogram.png)

### 4. Rainy vs Dry Race Outcomes
This bar chart shows how many F1 races between 2010 - 2024 were won in dry vs. rainy weather conditions.


*   Out of 300 total races, more races were won in dry conditions (≈162) than in rainy conditions (≈130).
*   This is expected, as dry races are more frequent overall in F1 seasons.

The graph helps us confirm that weather conditions influence race dynamics, but not to the extent of completely leveling the playing field. Dry-weather races still see more victories overall.

![Race Wins by Weather Condition](images/race%20wins%20by%20weather%20condition.png)


This heatmap visualizes how strongly four numerical factors are related to one another based on data from F1 race winners (2010-2024):


*   Driver Age
*   Experience

*   Grid Position
*   Pit Stops

Values range from -1 (strong negative correlation) to 1 (strong positive correlation), with 0 meaning no correlation.

This heatmap shows how strongly four race-related variables—driver age, experience, starting grid position, and number of pit stops are correlated with each other for Formula 1 winners.

The most noticeable relationship is the very strong positive correlation between driver age and experience. This is expected, since older drivers naturally have more years of racing behind them. Aside from that, the other variables show very weak or no correlation.

For example, starting grid position is not strongly related to experience or age, suggesting that older or more experienced drivers don't necessarily qualify better. Similarly, the number of pit stops doesn’t seem to be connected to any of the other variables, pit strategy appears to be independent of age, experience, and even starting position.

Overall, the heatmap tells us that most of these factors vary independently, and each one should be evaluated on its own when analyzing its impact on race outcomes.

![Correlation Heat Map](images/correlation%20heat%20map.png)


## Hypothesis Tests

### 1. Hypothesis Test: Grid Position of Winners vs Non-Winners
These two plots illustrate the distributions of starting grid positions for winners and non-winners, helping us decide which statistical test is appropriate for comparing the two.

First Plot: Winners

*   The distribution is heavily skewed to the left (toward lower grid positions).
*   Most winners start from the first few grid spots, especially grid position 1.
*   This is a non-normal distribution, clearly right-skewed.

Second Plot: Non-Winners

*   The distribution is more uniform and flat, spreading across many grid positions.
*   Again, the distribution is not normal, and definitely different from that of winners.

Since neither distribution is normal, and the shapes differ a lot, we cannot use a t-test (which assumes normality and similar shape). Instead, we use the Mann-Whitney U test, a non-parametric test that compares medians and distribution ranks.

![Hypothesis 1 Winners](images/hypothesis%201%20winners.png)

![Hypothesis 1 Nonwinners](images/hypothesis%201%20nonwinners.png)

Null Hypothesis (H₀):
There is no difference in the grid positions of winners and non-winners.
(Winners don't actually start ahead of others.)

Alternative Hypothesis (H₁):
Winners tend to start from better (lower) grid positions than non-winners.

U-statistic = 4,016,410.00
This is the test statistic computed by the Mann-Whitney U algorithm. It represents the number of times a value in the winner group precedes a value in the non-winner group in the ranked data.

p-value = 0.0000
This means the probability of observing this result, if the null hypothesis were true, is effectively zero.

Because the p-value is less than 0.05, we reject the null hypothesis.

Conclusion: There is a statistically significant difference between the grid positions of winners and non-winners.

Winners in F1 do tend to start from better grid positions, in other words qualifying near the front significantly increases the chances of winning.

Mann-Whitney U Test — Grid Position (Winners vs Non-Winners)
U-statistic = 4016410.00
p-value     = 0.0000

Result: Statistically significant difference.
Interpretation: Winners tend to start from 'better (lower)' grid positions.

This visualization clearly supports the statistical test results:

Winners tend to start from significantly better (lower) positions.

The median grid position for winners is close to 2, while for non-winners it's around 11.

![Hypothesis 1 Winners vs Nonwinners](images/hypothesis%201%20winners%20vs%20nonwinners.png)

![Hypothesis 1 Violin](images/hypothesis%201%20violin.png)


### 2. Hypothesis Test: Pit Stops of Winners vs Non-Winners
Winner Plot (Left):

*   The distribution is not symmetric.
*   There is a sharp peak at 2 pit stops, and then a long tail towards 3, 4, 5.
*   This is a right-skewed distribution, not normal.

Non-Winner Plot (Right):

*   The values are more spread out with multiple peaks.
*   Still not bell-shaped, not normal.

Since neither group (winners nor non-winners) shows normality, we cannot safely use a t-test which assumes normal distributions.
Instead, we choose the Mann-Whitney U test.

![Hypothesis 2](images/hypothesis%202.png)

Null Hypothesis (H₀):
There is no difference in the number of pit stops between winners and non-winners. (Pit strategy is not significantly related to winning.)

Alternative Hypothesis (H₁):
Winners make a different number of pit stops than non-winners.

U-statistic = 707,750.50

p-value = 0.0654

Because the p-value is greater than 0.05, we fail to reject the null hypothesis.

There is no statistically significant difference in the number of pit stops between winners and non-winners. This suggests that pit stop count alone does not clearly determine race outcomes.

Mann-Whitney U Test — Pit Stops (Winners vs Non-Winners)
U-statistic = 707750.50
p-value     = 0.0654

Result: No statistically significant difference.
Interpretation: There is 'no evidence' that pit stop counts differ between winners and non-winners.

![Hypothesis 2 Winners vs Nonwinners](images/hypothesis%202%20winners%20vs%20nonwinners.png)

![Hypothesis 2 Violin](images/hypothesis%202%20violin.png)


### 3. Hypothesis Test: Driver Experience of Winners vs Non-Winners
Winners (left): A noticeable right-skew, many winners tend to have 10+ years of experience.

Non-Winners (right): Also somewhat skewed but spread out more evenly, with slightly more density around 10-12 years.

Neither distribution appears normal.

Both are skewed, with more mass toward the right for winners.

Because the experience data does not follow a normal distribution and the sample sizes are different, we cannot safely use a t-test.

Instead, we use the Mann-Whitney U test.

![Hypothesis 3](images/hypothesis%203.png)

Null Hypothesis (H₀): There is no difference in experience between winners and non-winners.
(Winners are not more experienced than others.)

Alternative Hypothesis (H₁): Winners tend to be more experienced than non-winners.

U-statistic: 902,030.00

p-value: 0.0000

Since the p-value is less than 0.05, we reject the null hypothesis. There is a statistically significant difference.

Formula 1 winners from 2010 to 2024 tend to be more experienced than non-winners. Experience seems to play a meaningful role in winning races.

This shows that experienced drivers tend to win more races, showing the value of their knowledge and familiarity with the sport. Experience likely contributes to better race strategies, decision-making under pressure and consistent performance.

Mann-Whitney U Test — Experience (Winners vs Non-Winners)
U-statistic = 902030.00
p-value     = 0.0000

Result: Statistically significant difference.
Interpretation: Winners tend to be 'more experienced' than non-winners.

![Hypothesis 3 Winners vs Nonwinners](images/hypothesis%203%20winners%20vs%20nonwinners.png)


### 4. Hypothesis Test: Driver Age of Winners vs Non-Winners
Winners (left): Most winners tend to fall between ages 25 and 32, with a visible peak around 26-30.

Non-Winners (right): Ages are more spread out, and the distribution is a bit more symmetric with a longer tail after age 30.

Although both distributions are not extremely skewed, they are not perfectly normal either, especially the winners’ group, which shows a slight right skew and a visible multi-modal shape.

This visual check tells us that we should not assume a normal distribution.

Since the distributions are not normal and sample sizes may vary, Mann-Whitney U is more appropriate than a t-test.

![Hypothesis 4](images/hypothesis%204.png)

Null Hypothesis (H₀):
There is no difference in the driver ages of winners and non-winners.
(In other words, age does not affect race outcomes.)

Alternative Hypothesis (H₁):
There is a difference in the driver ages of winners and non-winners.
(Driver age does influence who wins races.)

U-statistic = 1,068,181.00

p-value = 0.0000

Because the p-value is less than 0.05, we reject the null hypothesis. There is a statistically significant difference in driver ages between winners and non-winners.

Mann-Whitney U Test — Driver Age (Winners vs Non-Winners)
U-statistic = 1068181.00
p-value     = 0.0000

Result: Statistically significant difference.
Interpretation: Driver 'age' is significantly different between winners and non-winners.

![Hypothesis 4 Winners vs Nonwinners](images/hypothesis%204%20winners%20vs%20nonwinners.png)


### 5. Hypothesis Test: Experience vs Starting Grid Position
Pearson correlation assumes a linear relationship and normally distributed variables.

But grid positions and experience may not be linearly related and may have outliers.

So we use Spearman, which checks for a monotonic trend

Null Hypothesis (H₀):
There is no correlation between driver experience and grid position. (ρ = 0)

Alternative Hypothesis (H₁):
There is a correlation between driver experience and grid position. (ρ ≠ 0)

Spearman r = 0.05

p-value = 0.3396

Since the p-value is greater than 0.05, we fail to reject the null hypothesis.

There is no statistically significant relationship between driver experience and grid position.

Even though we might expect experienced drivers to qualify better, this analysis shows that experience alone doesn’t predict grid position in a meaningful way. There may be other factors (like team performance, car upgrades, track characteristics) that play a much larger role in determining grid position.

Spearman Correlation — Experience vs Grid Position
Spearman r = 0.05
p-value    = 0.3396

Result: No statistically significant correlation.
Interpretation: There is 'no clear relationship' between experience and grid position.

This plot helps us visualize the relationship between a driver's experience and their starting grid position.

*   Each blue dot represents a race winner, showing their experience (x-axis) and starting grid position (y-axis).
*   The orange regression line tries to fit a linear trend through the data.

The scatter is very wide, and the orange line is nearly flat.

This matches the Spearman correlation result:
-> Spearman r = 0.05, p = 0.3396 (not significant)

![Hypothesis 5](images/hypothesis%205.png)


### 6. Hypothesis Test: Weather vs Winning
Because both weather and race outcome are categorical variables, we use a Chi-Square test of independence.

Null Hypothesis (H₀): Weather condition and race outcome are independent (rain has no effect on whether someone wins).

Alternative Hypothesis (H₁): Weather condition and race outcome are dependent (rain does affect winning chances).

Chi² = 0.04

p-value = 0.9809 Very high

Degrees of freedom = 2

Since the p-value (0.9809) is way above 0.05, we fail to reject the null hypothesis.

Conclusion: There is no statistically significant relationship between weather condition and race outcome.
In other words, drivers are equally likely to win in dry or rainy races, based on this data, rain does not impact the chance of winning.

Chi-Square Test — Weather vs Race Outcome
Chi² = 0.04
p-value = 0.9809
Degrees of freedom = 2

Contingency Table:
win_status  Non-Winner  Winner
rainy                         
0.0               3269     162
1.0               2634     131
unknown            228      12

Result: No statistically significant relationship.
Interpretation: There's 'no evidence' that weather impacts race winning probability.


## Machine Learning Techniques

### Data Loading and Filtering (2010–2024)

In earlier stages of this project, I had worked with a cleaned DataFrame that included only the race winners. While this version was suitable for simple descriptive analysis, it wasn’t sufficient for building a predictive machine learning model.

To accurately model and predict finishing positions, it was essential to include all drivers who participated in each race, not just the winners. Limiting the data to winners would have created a dataset where the target variable (finishing position) was always 1, which makes supervised learning impossible due to the lack of variability.

For this reason, I constructed a new dataset by merging raw tables (results, races, drivers, pit_stops, weather) to capture the full outcome of each race, including:

* Each driver’s starting grid position

* Their final position (positionOrder)

* Pit stop count, weather conditions, driver age and experience

This allowed me to train meaningful regression models that learn from differences in driver performance across a wide range of conditions and finishing outcomes.

### Feature Engineering and Data Integration

To prepare the dataset for machine learning, I merged multiple data sources to extract and engineer relevant features that influence race outcomes.


The final machine learning dataset (ml_df) included the following columns:

* positionOrder: target variable (finishing position)

* grid: starting grid position

* pit_stop_count

* driver_age

* driver_experience

* rainy: weather condition (categorical)

* nationality: driver’s nationality (categorical)

Categorical columns were explicitly converted to string type to ensure compatibility with encoders used during model training.

### Model Preparation and Training

To predict the finishing position of Formula 1 drivers based on race-specific and driver-specific features, I applied supervised regression models. The machine learning pipeline included both data preprocessing and model training, ensuring the models were trained on clean, transformed input.

**1. Preprocessing**

Before training, I prepared the features with the following transformations:

* Numerical Features
(grid, pit_stop_count, driver_age, driver_experience)

* Categorical Features
(rainy, nationality)

**2. Train-Test Split**

The dataset was split into 80% training and 20% testing subsets using train_test_split with a fixed random seed for reproducibility. This allowed for unbiased evaluation of model performance on unseen data.

**3. Model Training**

I firstly trained and compared two regression models:

* Linear Regression:
A simple, interpretable baseline model that fits a linear relationship between features and finishing position. It helps assess whether linearity is sufficient to capture the patterns in the data.

* Random Forest Regressor:
An ensemble model that builds multiple decision trees and averages their predictions. It handles non-linearities and feature interactions well and typically outperforms simpler models on complex structured datasets like this one.


Each model was trained using a Pipeline that included the preprocessing steps, making the entire process modular and easy to manage.


**Model Evaluation and Comparison**

After training both the Linear Regression and Random Forest models, I evaluated their performance using three common regression metrics on the test set:

Evaluation Metrics Used:
* MAE (Mean Absolute Error): The average of the absolute differences between predicted and actual finishing positions. Lower values indicate more accurate predictions.
* RMSE (Root Mean Squared Error): Similar to MAE, but gives more weight to large errors. It is sensitive to outliers, making it useful for detecting occasional big mistakes.
* R² (R-squared Score): Represents the proportion of variance in the actual data explained by the model. Values range from 0 (no explanatory power) to 1 (perfect predictions).

Linear Regression Performance
MAE : 3.87
RMSE: 4.88
R²  : 0.39

Random Forest Performance
MAE : 0.45
RMSE: 1.46
R²  : 0.95

**Interpretation:**

Linear Regression produced relatively high error rates, with an MAE of nearly 4 positions and R² of only 0.39. This means the model explained only 39% of the variation in finishing positions. While it served as a simple baseline, it lacked the complexity to capture non-linear relationships between input features and race outcomes.

Random Forest, on the other hand, achieved outstanding performance. With an MAE of just 0.45, it predicted finishing positions with remarkable precision — on average, within half a position of the true result. The RMSE was also much lower, indicating fewer large prediction errors. Most notably, the R² score of 0.95 shows that 95% of the variance in finishing positions was successfully captured by the model.


Linear Regression Performance
MAE : 3.87
RMSE: 4.88
R²  : 0.39

Random Forest Performance
MAE : 0.45
RMSE: 1.46
R²  : 0.95


**Additional Model: XGBoost Regressor**

To further evaluate model options, I also implemented an XGBoost Regressor, a powerful tree-based ensemble algorithm known for its performance on structured/tabular data. XGBoost improves upon standard decision trees by optimizing the model through gradient boosting, allowing it to capture complex patterns more effectively than linear models.

XGBoost Regressor Performance
MAE : 2.66
RMSE: 3.61
R²  : 0.67

The XGBoost model performed significantly better than Linear Regression:

It reduced the average prediction error from nearly 4 positions (in the linear model) to 2.66.

It explained 67% of the variance in finishing position (R² = 0.67), a substantial improvement over the linear model's 39%.


However, when compared to the Random Forest Regressor, XGBoost did not outperform it:

The Random Forest model achieved much lower error (MAE = 0.45) and a far higher R² score (0.95).

This suggests that Random Forest was better able to model the patterns in the dataset, possibly due to how it handles randomness and averaging across many decision paths.

XGBoost Regressor Performance
MAE : 2.66
RMSE: 3.61
R²  : 0.67


**Conclusion:**

These results demonstrate that Random Forest is a highly effective model for this task, significantly outperforming the linear baseline. It handles the complexity of Formula 1 data — such as interactions between grid position, pit strategy, driver experience, and weather — in a way that linear models cannot. Therefore, I selected Random Forest as the final model for making predictions.

**Scatter Plot:**

To visualize the performance of the Random Forest model, I created a scatter plot comparing the actual finishing positions (X-axis) to the model's predicted positions (Y-axis). Each point represents one driver’s race outcome, with turquoise dots for better clarity.

A red dashed diagonal line represents perfect prediction, where the predicted finishing position exactly equals the actual result.

**Interpretation:**

Most of the turquoise points are closely aligned with the red diagonal, indicating that the model’s predictions are very accurate for the majority of races.

The tight clustering around the diagonal highlights the model’s low average error (MAE ≈ 0.45), showing it often predicts finishing positions within less than one place.

A few minor deviations can be seen, but they are limited in magnitude — further supporting the model’s robustness.

This plot visually confirms what the numeric evaluation metrics indicated: the Random Forest model is highly effective at predicting race outcomes.

![Random Forest Scatter Plot](images/random%20forest%20scatter%20plot.png)


Histogram of Prediction Errors (Random Forest)

Each bar in the histogram shows how frequently a specific range of errors occurred

* The histogram is centered around 0, meaning that most predictions are very close to the actual finishing positions.

* The majority of errors fall between -1 and +1, which supports the model’s exceptionally low Mean Absolute Error (MAE ≈ 0.45).

* Very few large errors exist, confirming the model’s consistency and reliability.

![Random Forest Histogram](images/random%20forest%20histogram.png)


**Correlation Heatmap: Features vs Finishing Position**

The heatmap visualizes Pearson correlation coefficients, with values ranging from:

+1.00 (strong positive correlation)

0.00 (no linear correlation)

–1.00 (strong negative correlation)

* grid (starting position) shows a strong positive correlation with positionOrder. This confirms that starting closer to the front generally leads to better race finishes — a key insight for predictive modeling.

* driver_experience and driver_age show moderate to weak negative correlations, suggesting that more experienced or older drivers tend to perform slightly better, but the effect is less dominant than grid position.

* pit_stop_count has a small positive correlation with finishing position, indicating that more pit stops are slightly associated with worse outcomes — likely due to lost time unless offset by strategy advantages.

This heatmap was helpful in understanding which features are most informative for predicting race results and validating domain intuition about how races unfold.

![ML Heat Map](images/ml%20heat%20map.png)


**Model Comparison: MAE, RMSE, and R²**

To visually compare the performance of all three models — Linear Regression, Random Forest, and XGBoost — I created a grouped bar chart showing three evaluation metrics:

MAE (Mean Absolute Error): Lower is better

RMSE (Root Mean Squared Error): Lower is better

R² (R-squared Score): Higher is better

**Interpretation:**

* Random Forest clearly outperforms the other models on all three metrics:

Lowest MAE and RMSE → Most accurate predictions

Highest R² (≈ 0.95) → Explains almost all variation in finishing positions

* XGBoost performed better than Linear Regression, but still lagged behind Random Forest in every category.

* Linear Regression, while easy to interpret, was too simplistic for this problem — reflected by its higher errors and low R² (≈ 0.39).

This visual comparison makes the case clear: Random Forest is the most effective and reliable model for predicting F1 race outcomes in this project.

![Model Comparison](images/model%20comparison.png)


## Conclusion

This project demonstrated that Formula 1 finishing positions can be accurately predicted using structured race and driver data. Among the models tested, Random Forest Regressor delivered the highest accuracy, achieving an R² of 0.95 and an MAE below 0.5.

Key insights:
- Starting grid position was the most important predictor of final results.
- Driver experience and pit stop count contributed moderately.
- Weather had some impact but was not as dominant.

These results align with real-world race dynamics and show that machine learning can be a useful tool for strategy prediction and performance analysis in motorsport.


## Limitations and Future Work

- The model does not account for team constructor performance, car upgrades, or penalties — factors that can significantly affect race outcomes.
- Weather data was limited to a binary rainy/not rainy field and may benefit from more detailed metrics (temperature, intensity).
- The analysis focuses on historical data; live prediction would require real-time integration.

**Future improvements:**
- Incorporate team-level features (constructor standings, engine performance).
- Add race track metadata (like overtaking difficulty, pit lane time loss).




