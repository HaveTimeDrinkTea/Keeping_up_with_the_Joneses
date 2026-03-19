# 🏠😊💷💶 Keeping Up With The Joneses: Wealth, Health and Happiness in the North-South Divide and across the Channel

As an imigrant to the United Kingdom, I have known the "North South Divide" narrative as one of the most enduring narratives in British public life. For generations, it has been framed as a story of economic inequality of London being the star of the South vs the poorer cousins in the North. I wondered if the "Levelling Up" initiatives that politicians in the UK bandy about are not based on the true measures of well-being. Perhaps the North is not necessarily poorer and unhappy. Perhaps it is all a myth.

This project seeks to ask the following questions:
🤔 Is the North really less well off financially than the South?
🤔 Even if that is true, does the level of well-being (chiefly, health and happiness) also suffers from a "North-South Divide"?
🤔 We then ask whether British regional stories can be seen in her Eurpoean neighbours. Crucially, are British keeping up with the Joneses across the Channel?

The result of this analysis is a dashboard that will hopefully challenge the assumptions of "Levelling Up", reveal surprising patterns and invite us to consider the real drivers of happiness.



## 1.0 Project Approach & Project Plan

📌 As the aim of this 5-day capstone project is to showcase a complete data analytics workflow from forming hypotheses, sourcing data, ETL/EDA of the data, testing the hypotheses, model predictions and presenting the findings in an interactive dashboard. It aims to look into the ethical considerations in the use and presentation of the data. This project is managed by the use of the Kanban board.

| Phase | Tasks |
|:---|:---|
| Days 1 -2| Hypothesis formation, data sourcing, ETL and EDA |
| Day 2 - 3 | Hypothesis testings, linear regression modelling Part 1 & Part 2|
| Day 4 | Tableau Dashboard |
| Day 5 | Tableau Dashboard, Bug fixes and Readme documentation|
| Day 6 | Bug fixes, Readme documentation and final submission |

📌 The data is downloaded from the [OECD Regional Well-Being: A Closer Measure of Life](https://oecdregionalwellbeing.org/) as a .xlsx file with multiple sheets. At each of the main stages of data preparation, a .csv file is created and stored in the [../data/processed](data/processed) directory for further analysis or dashboarding work. 


## 2.0 Project Links
* [Github repo](https://github.com/HaveTimeDrinkTea/Keeping_up_with_the_Joneses)
* Interactive Tableau Dashboard on [Tableau Public](https://public.tableau.com/views/keeping_up_with_the_joneses_v3/DashboardKeepingupwiththeJoneses2?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) or via [download the keeping_up_with_the_joneses_v3.twbx.twbx](dashboard/keeping_up_with_the_joneses_v3.twbx)
* [Kanban Board on GitHub](https://github.com/users/HaveTimeDrinkTea/projects/3)

## 3.0 Data Source
📌 The project uses data from: [OECD Regional Well-Being: A Closer Measure of Life](https://oecdregionalwellbeing.org/). It is an excel spreadsheets with the following worksheets:
 * "Home"
   * Provides an introduction to the OECD Regional Well-being initiative and instructions on how to use the data contained within.
 * "Score_Last"
   * Contains the most recent well-being scores for each region acors all eleven themes.
 * "Score_Trend"
   * Tracks how regional well-being scores have changed over time.
 * "Indicator_Last"
   * This worksheet holds the underlying data used for this project.
 * "Source"
   * Details the original sources for all the data.
 * "Reference_Year"
   * Lists the specific reference year for each indicator and region. Noting that data may be sourced from different collection periods.

## 4.0 Business and Learning Requirements    
### 4.1 Business Requirements
📌 There are four main business requirements from the perspectives of a policymaker and a researcher:

1. To attempt to quantify and understand the age old narrative of "North-South Divide" in the UK in terms of wealth, health and happiness. This is done via hypotheses 1, 2 and 3.

2. To attempt to benchmark UK with selected European peers so as to understand if the UK situation is unique or just part of a broader pattern.

3. To identify the key drivers of happiness.

4. To provide an interactive tool for communicating analysis findings and for interested parties to dynamically explore these relationships of key drivers on happiness.

#### The rationale to map the business requirements to the Data Visualisations
📌 Each business requirement is addressed through dedicated visualisation(s) in the Jyputer Notebooks or summarised in the Dashboard.
* Requirement 1 is visualised through box plots showing distribution of income, life expectancy and life satisfaction across Northern and Southern Regions.
* Requirement 2 is achieved through the interactive tree maps and scatter pots comparing UK to one or more of the selected European nations. A correlation table also places the UK regions in the context with her European peers.
* Requirements 3 is visualised through the "Everything but the Kitchen Sink" predictive model's Bullet chart allowing users to see which factors drives happiness in the six nations.


### 4.2 Capstone Project Learning Requirements:
📌 The folowing are teh learning outcomes required of this third captstone project. [Ethical practice and communication in data Assessment Handbook](https://code-institute-org.github.io/5P-Assessments-Handbook/da-ai-bootcamp-unit3.html)

* L01: Ethics, Privacy, and governance: This has been adderesed in each Juypter Notebook, in the Dashboard and in this README.md

* L02: Clarify and Present Complex Data Insights: The Dashboard communicates a clear story of "Keeping up with the Joneses" in 2 layers. First, is the UK layer with the analysis on the North-South divide. Second, is the "keeping up with" the UK's European neighbours narrative.

* L03: Review and Revise data analytics project plans: This will be detailed in this README.md


## 3.0 Hypothesis Formulaton, Validation and Conclusion

📌 From those primary questions listed in the introductory paragraph, I have derived the hypotheses listed in this section. 

The workings can be found in [02_Hypothesis_Testing.ipynb](jupyter_notebooks/02_Hypothesis_Testing.ipynb) where I rigorously tested these hypothesis using pingouin for statistical outputs complemented by visualisations using matplotlib.

This project has made some [key assumptions](#60-key-assumptions) in its treatment of the data.


### 3.1 Hypothesis 1 `(MVP)` _**"The North-outh Wealth Gap"**_
📌 Hypothesis 1 examines whether there is a significant difference in disposable income per capita between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean disposable income per capita (US$ PPP) of Northern UK regions is equal to the mean disposable income per capita (US$ PPP) of Southern UK regions.
> 

Using the Shapiro-Wilk test for normality, it was discovered that 
* Disposable Income per Capita for UK as a whole does not follow a normal distribution
* But when we separate the income into the north and southern regional groupings, each of these region grouping's income are deemed to be normally distribution.

As such, however, the diffence in standard deviations between North and South regional incomes (US$1,475 and US$6,980 respectively) is quite large. This therefore puts the suitability of the t-test into question as it assumes equal variance and normal distribution. I tested the difference of the means of income using both the t-test and the Welch's t-test (which does not assume equal variance) and received contradictory results. 

With a small observations of 6 in each region, it was decided that the non-parametric Mann-Whitney's U test is more suitable as it does not assume normal distribution nor does it assume equal variance.

| Test | p-val | Conclusion at ⍺ = 0.05|
|---|---|---|
| t-test | 0.039423 | Reject H<sub>0</sub> |
| Welch's t-test | 0.059962 | Do Not Reject H<sub>0</sub> |
| Mann-Whitney's U test | 0.015152  | Reject H<sub>0</sub> |

‼️📝 As the number of observation is inevitablity small at the TL2 regions, Mann-Whitney U's test will be used without having to test the normality of the underlying data.


#### Results & Findings  
📌  The descriptive statistics suggest that Southern region do have higger disposable income with a mean incomde of US$3,4,987 compared to the North's US$28,090. It is to be noted that Northern regions are quite homogeneous in their income level swhereas the Southern are not.  

📌 With a `p-val` of 0.015152 which is less than the 5% significance level (⍺ = 0.05), _**we can reject H<sub>0</sub> and conclude that there is a statistically significant difference in disposable income per capita (US$ PPP) between the north and the south of UK**_.

The Common Langauge Effect Size (`CLES`) reveals that if one were to compare a randomly chosen Northern Region and a Southern region, there is a 91.7% chance that the southern will have a higher income and bby extention, more wealthy.


### 3.2 Hypothesis 2 `MVP` _**"The North-South Happiness Gap"**_
📌 Hypothesis 2 examines whether there is a significant difference in life satisfaction between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean life satisfaction of Northern UK regions is equal to the mean life satisfaction of Southern UK regions.
> 

#### Results & Findings  
📌 Consistent with the approach for Hypothesis 1, Hypothesis 2 was tested using the Mann-Whitney's U test which returns a `p-val` of 1.0. As such, _**we cannot reject H<sub>0</sub> and conclude that there is absolutely no evidence of a difference in life satisfaction index between the north and the south**_. With a `CLES` of 0.486, the test says that there is 50% chance of a northern region having higher happiness than the south which is essentially as random as a coin flip.

📌  The descriptive statistics confirms this finding. Northern regions have a mean life satisfaction of 6.83 while the Southern regions average at 6.85.  This difference of just 0.02 on a scale of 0 to 10 is small. The Northern region saw a greater variation in their life satifaction index (Standard deviation of 0.15) where both the highest and lowest index for the whole of UK is in the North. The South, however, is more homogeneous in this respect (Standard deviation of 0.0.08). 

### 3.3 Hypothesis 3 `MVP` _**"The North-South Health Gap"**_
 * Hypothesis 3 attempts to look at whether there is a significant difference in life expectancy between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean life expectancy of Northern UK regions is equal to the mean life expectancy of Southern UK regions.
> 

#### Results & Findings  
📌 Consistent with the approach for Hypothesese 1 and 2, Hypothesis 3 was tested using the Mann-Whitney's U test which returns a `p-val` of 0.008. The `CLES` of 0.972 means that if one were to compare a randomly chosen Northern Region and a Southern region, there is a 97.2% chance that the southern will have a higher life expectancy and by extension, better health. As such, at 5% significance level, _**we can reject H<sub>0</sub> and conclude that there is a statistically significant difference in life expectancy between the north and the south of UK**_.

📌 The descriptive statistics paints a similar image. The southern region has a mean life expectancy of 81.2 years as compared to the northern cousins of 79.7 years. The differce is pronounced so that the healthiest Northern region (80.4) is still beow the Southern average of 81.2 years. 


#### Summary Conclusion for Hypotheses 1, 2 and 3
| Hypothesis | Finding | CLES for South|
|:---|:---|:---|
| H1 Wealth | North is poorer (p=0.015) | 91.2 %|
| H2 Happiness | No Difference (p=1.0) | 48.6 %|
| H3 Health | North is less healthy (p=0.008) | 97.2 %|


### 3.4 Hypothesis 4 `MVP` _**"Keeping Up with the Joneses" Richer but Happier and Healthier?"**_
* Hypothesis 4 asks whether the relationships between income, life expectancy and life satisfaction in the UK are different compared to the selected five nations. 

>
> H<sub>0</sub>: The correlations between income, life expectancy and life satisfaction are the same for the UK and the selected five European nations.
> 


📌  This hypothesis is to be tested and resulted interpreted using 
* Pearson's r (correlation coefficient) which assesses the strength and direction of a linear relationship between 2 continuous variables and 
* then use Cohen's guideline (threshold of 0.2) for interpreting correlation strengths of these relationships between the UK and Europe.

Specifically, we will look at 3 separate sets of relationships (all continuous variables) and will compute the Peason's r for each relationship for the UK and for the European five.
1. Income vs Life Satisfaction
2. Income vs Life Expectancy
3. Life Satisfaction vs Life Expectancy

We then compare the Peason's r correlataion coefficent for each relationship between the UK and Europe. 

#### Results & Findings  
| Relationship | UK-R | EU-R | Absolute Difference (A) | A vs 0.2 threshold? | Conclusion |
|---|---|---|---|---|---|
| Wealth vs Happiness | 0.179	| 0.385	| 0.206	| > 0.2 | UK & EU are Different |
| Wealth vs Health | 0.659 | -0.078 | 0.737 | > 0.2 | UK & EU are Different |
| Happiness vs Health | -0.118 | -0.344 | 0.226 | > 0.2 | UK & EU are Different |

📌 `Wealth vs Happiness`: The UK has a weak positive relationship as opposed to Europe's moderately strong positive relationship. This suggest that wealth and happiness goes _**more**_ hand in hand in Europe then in UK. In Hypotheses 1 and 2, we already seen that whilst the North is poorer, is it just as happy as the South.

📌 `Wealth vs Health`: This appears to be the most striking find. The UK showed a strong positive relationship but the European neighbours showed a slightly negative relationship. This appear to suggest that unlike in the Europe, wealth and health appears to be more bundled together. That is in the UK, the poorer regions tend to be less healthy too.  

📌 `Happiness vs Health`: Both the UK and Europe, showed negative relation with Europe's more moderately negatively then the UK. This seemingly counterintuitive finding seems to suggesting the regions who lived longer are less happy. This relationship appears to persist across the 6 nations. This will require further investivation.

As all three sets of relationships are different between the UK and the European five, we can reject H<sub>0</sub> and conclude that the UK regions are indeed different to their regional European counterparts.

It is interesting to note that, the UK stands out in its unusually strong link between `Wealth vs Health`. 



## 4.0 Predictive Modellings and Results:
📌 In [03_Predictive_Modelling.ipynb](jupyter_notebooks/03_Predictive_Modelling.ipynb), I created 2 main models for predicting Happiness.

The full dataset contains 91 observations across six nations. 

As variables income (in '000s) and health (in years) are of different scales, we apply a standardisation to allow the direct comparison of the coefficients. 

The models in this section used Lasso regression with a very small penalty (alpha=0.01) to select predictors that are important. This small penalty will only remove predictors that are truly useless. In other words, we aim to keep as many predictors as possible in our models.


### 4.1 Predictive Model 1: "The Usual Suspects" Wealth, Health and Happiness
📌 Model 1 tests a straightforward question which is whether one can "buy" happiness with wealth and health through the use of a mutliple linear regression model with `life_satisfaction_index` as the dependent variable and `disposable_income_pc` and `life_expectancy` as predictors.

The expected model is: 
> 
> Happiness = β₀ + β₁(Wealth) + β₂(Health) + ε
>


#### Training Approach 
📌 The data was first split into Train and Test set on a 80/20 split to train and test the model. Model 1 achieved a  R<sup>2</sup> of 0.254 which means that Model 1 (wealth and health) can only explain 25.4% of th variations in happiness. 

Upon reflection, I have decided to use all 91 observations in the to train the model. The resulting Model 1A did not fare any better.

| Coefficient | Model 1 (Train Only) | Model 1a (Full Dataset) |
|:---|:---|:---|
| **Income** | +0.173 | +0.146 |
| **Health (Life Expectancy)** | -0.123 | -0.140 |

#### Results 

| Metric | Model 1 (Train) | Model 1 (Test) | Model 1a (Full Dataset) |
|:---|:---|:---|:---|
| **R² Score** | 0.254 | -0.006 | 0.236 |
| **Mean Absolute Error (MAE)** | 0.288 | 0.242 | 0.281 |
| **Mean Squared Error (MSE)** | 0.143 | 0.110 | 0.136 |
| **Root Mean Squared Error (RMSE)** | 0.379 | 0.332 | 0.368 |
| **Sample Size** | 73 | 18 | 91 |


* With the Test set R<sup>2</sup> of -0.006, it is clear that Model 1 suffers from overfitting.


#### Model 1/1A Interpretations
📌 Looking only at Model 1A (full dataset used to train the model), we can see that it can only account for roughly a quarter or 23.6% of variations in the happiness index. 

* The income coefficient of +0.146 is relatively small which suggests that wealthier regions tend to be (slightly) happier. Such that 1 standard deviation increase in wealth can only increase 0.146 standard deviation in happiness on a scale of 0-10.
* The life expectancy coefficient is surprisingly negative (-0.14). This seemingly counterintuitive finding suggests that across all six nations, living to an older age does not equate to having more happiness. Howeever, I think we need to understand that perhaps there are many factors at play. 




### 4.2 Predictive Model 2: "Everything but the Kitchen Sink"
📌 Since Model 1/1A can only explain about 25% of happiness with the ususal suspects of wealth and health, the project changed its direction to look at all 14 social well-being indicators in the OECD regional well-being data as grouped below: 
* Material conditions:
  * `disposable_income_pc`
  * `employment_rate`
  * `unemployment_rate`
  * `rooms_per_capita` 
  * `housing_affordability_pct` 
* Health
  * `life_expectancy`
  * `mortality_rate` 
* Safety
  * `homicide_rate`
* Education
    * `secondary_education_pct` 
* Environment
  * `air_quality_pm25` 
* Digital Access
  * `broadband_access_pct` 
  * `internet_speed_deviation` 
* Civic engagements and Social Connections:
  * `voter_turnout_pct` 
  * `social_network_support_index`

📌 Having created a moderately performing Model 2, this project proceed to add a variable to Model 2 to see if being in the UK has an impact on the prediction of happiness. 
  * This Model 3 is named as "Kitchen Sink and the UK Effect".

#### Training Approach 
📌 The data was split into Train and Test set on a 80/20 split to train and test the model. 


#### Model 2 & 3: Kitchen Sink with and without UK Effect Indicator


| Dimension | Indicator | Model 2 Coefficient | Rank | Model 3 Coefficient | Rank |
|:---|:---|:---|:---|:---|:---|
| **Material Conditions** | `disposable_income_pc` | <div style="text-align: right">0.060</div> | <div style="text-align: center">8</div> | <div style="text-align: right">0.059</div> | <div style="text-align: center">8</div> |
| | `employment_rate` | <div style="text-align: right">-0.056</div> | <div style="text-align: center">10</div> | <div style="text-align: right">-0.056</div> | <div style="text-align: center">10</div> |
| | `unemployment_rate` | <div style="text-align: right">-0.100</div> | <div style="text-align: center">5</div> | <div style="text-align: right">-0.100</div> | <div style="text-align: center">5</div> |
| | `rooms_per_capita` | <div style="text-align: right">-0.044</div> | <div style="text-align: center">11</div> | <div style="text-align: right">-0.044</div> | <div style="text-align: center">11</div> |
| | `housing_affordability_pct` | <div style="text-align: right">-0.059</div> | <div style="text-align: center">9</div> | <div style="text-align: right">-0.059</div> | <div style="text-align: center">9</div> |
| **Health** | `life_expectancy` | <div style="text-align: right">-0.254</div> | <div style="text-align: center">2<sup>nd</sup></div> | <div style="text-align: right">-0.253</div> | <div style="text-align: center">2<sup>nd</sup></div> |
| | `mortality_rate` | <div style="text-align: right">-0.276</div> | <div style="text-align: center">1<sup>st</sup></div> | <div style="text-align: right">-0.275</div> | <div style="text-align: center">1<sup>st</sup></div> |
| **Safety** | `homicide_rate` | <div style="text-align: right">0.067</div> | <div style="text-align: center">7</div> | <div style="text-align: right">0.067</div> | <div style="text-align: center">7</div> |
| **Education** | `secondary_education_pct` | <div style="text-align: right">0.038</div> | <div style="text-align: center">12</div> | <div style="text-align: right">0.038</div> | <div style="text-align: center">12</div> |
| **Environment** | `air_quality_pm25` | <div style="text-align: right">*discarded by Lasso*</div> | <div style="text-align: center">n.a.</div> | <div style="text-align: right">*discarded by Lasso*</div> | <div style="text-align: center">n.a.</div> |
| **Digital Access** | `broadband_access_pct` | <div style="text-align: right">0.024</div> | <div style="text-align: center">13</div> | <div style="text-align: right">0.024</div> | <div style="text-align: center">13</div> |
| | `internet_speed_deviation` | <div style="text-align: right">-0.087</div> | <div style="text-align: center">6</div> | <div style="text-align: right">-0.087</div> | <div style="text-align: center">6</div> |
| **Civic Engagement & Social Connections** | `voter_turnout_pct` | <div style="text-align: right">0.238</div> | <div style="text-align: center">3<sup>rd</sup></div> | <div style="text-align: right">0.237</div> | <div style="text-align: center">3<sup>rd</sup></div> |
| | `social_network_support_index` | <div style="text-align: right">0.117</div> | <div style="text-align: center">4</div> | <div style="text-align: right">0.116</div> | <div style="text-align: center">4</div> |
| **UK Effect** | `uk_dummy` | – | – | <div style="text-align: right">*discarded by Lasso*</div> | <div style="text-align: center">n.a.</div> |



#### Results 

| Metric | Model 2 (Train) | Model 2 (Test) | Model 3 |
|:---|:---|:---|
| **R²** | 0.633 | 0.572 | 0.631 |
| **MAE** | 0.195 | 0.185 | 0.196 |
| **MSE** | 0.071 | 0.047 | 0.072 |
| **RMSE** | 0.266 | 0.216 | 0.267 |


📌 The "Everything but the Kitchen Sink" model is a dramatic improvement over Model 1/1A with the R<sup>2</sup> increased to 0.633. This indicates that happiness is far more predictable with we look at a fuller range of well-being indicator. 

📌 The Lasso dropped the UK indicator in Model 3. This means that there is no UK effect in the prediction of happiness. This renders Model 3 as redundant.


### Model Interpretations


📌 Model 2 "Everything but the Kitchen Sink" included all 14 indicators covering material conditions, health, safety, education, environment, digital access and civic engagements and social interactions aspect of social well-being. This model performed substantially better than Model 1 by achieving a modest R<sup>2</sup> of 0.63 and 0.57 on the Train and Test sets respectively. The coefficients revealed that health and civic engagements and social interactions indications are in the top 4 predictors of happiness. The only possible counterintuitive indicator in the top four is  `Life_expectancy` which appears to suggest that living longer does not equate to more happiness.

| Dimension | Rank | Indicator | Coefficient | 
|:---|:---|:---|:---|
| **Health** | <div style="text-align: center">1<sup>st</sup></div> | `mortality_rate` | <div style="text-align: right">-0.276</div> 
| | <div style="text-align: center">2<sup>nd</sup></div> | `life_expectancy` | <div style="text-align: right">-0.254</div> | 
| **Civic Engagement & Social Connections** | <div style="text-align: center">3<sup>rd</sup></div> | `voter_turnout_pct` | <div style="text-align: right">0.238</div> | 
| | <div style="text-align: center">4<sup>th</sup></div> | `social_network_support_index` | <div style="text-align: right">0.117</div> | 

📌 Model 3 "Kitchen Sink with the UK Effect" added a UK indicator into the Model 2 to see whether the UK regions differs systemativally from their European counterparts after accounting for all other indicators. However, the Lasso algorithm dropped this UK indicator entirely. This leads to a clear conclusion that being in the UK has no independent effect on regional happiness.  The UK regions are exactly as happy as their European neighbours with the same profile on these indicators.


### 4.3 Limitations
📌 Small Dataset: there are only 91 observtions across the 6 nations. The small sample size leads to risk of overfitting as we see in Model 1. It may also limit the complexity of models that can be reliably fitted as we see in Models 2 and 3.
  * The sample size is small as we aggregated to TL2 levels to respect privacy concerns.

📌 Regional Aggregations: all the indicators are agregated at the TL2 level invariably masks substantiations witin regions. Findings about regions do not necesarily apply to all individuals within those regions. 

📌 Coefficent of `life_expectancy` in the models: The persistantly negative relation of `life_expectancy` with `life_satisfaction_index` in our models remains counterintuitive and difficult to reason. It may reflect cultural differences in survey reponses on the subjective `life_satisfaction_index` or that the influence on other unmeasured factors such as (and not exhaustively) diet, lifestyle, cultural outlook that can affect longevity and happiness in different ways.

📌 As with all regression models, these results demonstrates correlation and not causation. The relationships depicted here do not imply that changing income or health would directly cause changes in happiness.



## 5.0 Dashboard Design
📌 The "Keeping up with the Joneses" dashboard in a single page interaction interface designed to guide users through the project narrative from the UK North-South divide to a European comparison. The dashboard has the following sections:
* North-South Divide:
  * Three static box plots showing the UK regional disparities in wealth, health and happiness.  
  * With hover tooltips showing exact values
  * Each plot displays the statistical results of the respective hypotheses
* UK Comparing European 
  * interactive heatmaps with the three metrics of wealth, health and happiness and bubble plots
  * users are invited to none or all of the selected five European counterparts to compare with the UK
  * Legends also changes based on user's choice of countries
  * Correlation table showing how UK differs from Europe on 3 key relationships of wealth vs happiness, wealth vs health and happiness vs health.
* A Bullet plot showing the predictors' coefficient from the "Everything but the Kitchen Sink" happiness prediction model.
  * positive indicators are shown in blue on the right
  * negative indicators are shown in red on the left  
* Ethical considerations and Limitations

The dashboard aims to be friendly to both technical and non-technical audience alike with
* statistical results diplayed directly on the charts
* clear visual patterns, intuitive filters and hover tooltips guide the exploration of the analysis. 
* the dashboard follows a top-down logical "what, so what and why" flow by first establising the UK North South Divide, then placing it in European contect and then revealing what truly drives happiness. 

### 5.1 Dashboard Presentation
📌 An interactive dashboard

* Interactive Tableau Dashboard on ["Keeping up with the Joneses" Dashboard on Tableau Public](https://public.tableau.com/app/profile/pei.wang1891/viz/keeping_up_with_the_joneses_v3/DashboardKeepingupwiththeJoneses2) or via [download the keeping_up_with_the_joneses_v3.twbx](dashboard/keeping_up_with_the_joneses_v3.twbx)  

![Screenshot of Dashboard](docs/images/??.png) 


## 6.0 Key Assumptions
📌 The [Ethical Considerations](#70-ethical-considerations) section will discuss the implication of such assumptions

### 📋 UK North-South classification
| Region Grouping | Region |
|---|---|
| North | North East England 
| | North West England |
| | Yorkshire and The Humber |
| | Scotland |
| | Northern Ireland |
| | Wales |
| South | East Midlands |
| | West Midlands |
| | East of England |
| | Greater London |
| | South East England |
| | South West England|

### 📋 Choice of the five European nations:
* Germany
* France
* Italy
* Spain
* the Netherlands

The choice is a deliberate one based loosely on: 
* physical proximity
* size of economy
* size of the population
* to the north and south of the UK
* physical shape of the country (Italy has a long North-South shape)
* equitable and well-balance nature

For more details see section 1.5 of [01_ETL_EDA_WellBeing_Data.ipynb](jupyter_notebooks/01_ETL_EDA_WellBeing_Data.ipynb).

### 📋 Wealth, Health and Happiness
* This project uses the following OECD's social well-being indicators as proxies for `Wealth`, `Health` and `Happiness` respectively
  * Disposable income per Capita (US$, PPP)
  * Life Expectancy (in years)
  * Life Satisfaction Index (0 - 10, self-reported)


## 7.0 Ethical considerations
📌 Data Privacy
* All the data used in this project is aggregated at the TL2 regional level. Each value represents the averages of thousands of individuals. No personally identifiable information is used. 
* The OECD applies strict disclosure controls to smaller regions TL3 and below to prevent identification.
* By working at TL2 level, this project inherently respects those privacy concerns.


📌 Terminology and Simplication
* Terms such as "wealth", "health" and "happiness" are used as convenient shorthand and for a more creative narrative for specific indicators `disposable_income_pc`, `life_expectancy` and `life_satisfaction_index`. 
* These terms are also used as proxies for the underlying indicators. This project acknowledges that it is by no means implying that having a high `disposable_income_pc` means that one is "wealthy" or that having a high `life_satisfaction_index` implies the one is "happy".


📌 Econological Fallacy
* All the findings apply to regions only. For example, a wealth region can have people of limited financial means nor does a region with a high level of life satisfaction contains everyone at the same level of "happiness".


📌 Bias and Fairness
* The project is careful in wording as neutrally as possible to reduce the risk stigmatising areas with unfavourable scores. 


📌 North-South Groupings and Country Selection Bias 
* The project acknowledges that the grouping of UK regions into convenient groups of 6 is inherentlly an over-simplification. For example, the placement of both the midlands regions in the South is purely an analytical choice.
* The choice of the five European nations (France, Germany, Italy, Spain and the Netherlands)


📌 Missing Values 
* Some French and Spanish overseas territories have been excluded because
  * they are geographically located far from European mainland
  * they have missing values.


📌 Causation vs Correlation
* All models demonstrate association not causation.
  * For example, the strong relationship between voter turnout and happiness simply means that happier region vote more. It does not imply that voting more leads to higher happiness.


📌 Transparency and Reproducibility
* All data sources, preparation steps, analytical code and modelling choice are documented in the accompanying Juypter notebook and Github repo. 




## 8.0 Limitations

📌 Sample Size



## ?.0 Retrospective Project Plan
📌 As the

## ?.0 Analysis techniques used
* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques. Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?

## ?.0 Reflections on Challenges
📌 As the
* Tableau's geocoding issues for UK. overcame by using manual coodinates, changing to treemap 
* creating data table and use of csv
* use of parameters, and set actions 
* finding solutions only to realise that it is not for Tableau Public

## 9.0 Unfixed Bugs
* Please mention unfixed bugs and why they were not fixed. This section should include shortcomings of the frameworks or technologies used. Although time can be a significant variable to consider, paucity of time and difficulty understanding implementation are not valid reasons to leave bugs unfixed.
* Did you recognise gaps in your knowledge, and how did you address them?
* If applicable, include evidence of feedback received (from peers or instructors) and how it improved your approach or understanding.

## 10.0 Development Roadmap
* What challenges did you face, and what strategies were used to overcome these challenges?
* What new skills or tools do you plan to learn next based on your project experience? 



# Tech Stack & Libraries
* Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.
* ![Python](https://img.shields.io/badge/python-3.13%2B-blue)
* Libraries:
  * [![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=fff)](#)
  * [![NumPy](https://img.shields.io/badge/NumPy-4DABCF?logo=numpy&logoColor=fff)](#)
  * ![Matplotlib](https://custom-icon-badges.demolab.com/badge/Matplotlib-71D291?logo=matplotlib&logoColor=fff) 
  * ![seaborn](https://img.shields.io/badge/-Seaborn-3776AB?style=flat&logo=python&logoColor=white&size=40x40)
  * ![Scikit-learn](https://img.shields.io/badge/-scikit--learn-%23F7931E?logo=scikit-learn&logoColor=white)
  * [![Pingouin](https://img.shields.io/badge/Pingouin-stats%3Fcolor%3Dfedcba)](https://pingouin-stats.org/)
  * ![SciPy](https://img.shields.io/badge/SciPy-654FF0?style=flat&logo=scipy&logoColor=white)
* ![Tableau](https://custom-icon-badges.demolab.com/badge/Tableau-0176D3?logo=tableau&logoColor=fff)
* ![Git workflow](https://img.shields.io/badge/Github%20Actions-282a2e?style=for-the-badge&logo=githubactions&logoColor=367cfe)




# How to Reproduce This Project
* (Recommended) Create a virtual environment.
* Clone the repository
> git clone https://github.com/HaveTimeDrinkTea/global_tea_trade_analysis.git
* Install dependencies: 
> pip install -r requirements.txt
* Open the Jupyter notebooks (e.g.):
> jupyter notebook notebooks/notebooks/01_ETL_FAO.ipynb

> jupyter notebook notebooks/notebooks/01_ETL_WorldBank.ipynb


# License
MIT License [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


# Credits and Acknowledgements
* My tutors [Mr. John Anih](https://github.com/JohnAnih), Mr Vasi Pavaloi, [Mr. Mark Briscoe](https://github.com/mbriscoe/)
* eLearning materials of the "Data Analytics with AI" Bootcamp by the Code Institute
* Learnings from Mimo.org (Python e-learning) and Python and the relevant packages' official Websites
* Visualisation guidance:
  * [From Data to Viz](https://www.data-to-viz.com)
  * [The Royal Statistical Society's Best Practices for Data Visualisation](https://royal-statistical-society.github.io/datavisguide/docs/choosing.html)
* Deepseek for
  * Project brainstorming
  * helping me to understand the data that is used for the analysis (e.g. nominal GDP for comparing within years)
  * being my Python and Pandas tutor and for helping to resolve code errors
 

# Contributions
* If you have any query or contribution about this repo, please contact via
  * GitHub [https://github.com/HaveTimeDrinkTea](https://github.com/HaveTimeDrinkTea)