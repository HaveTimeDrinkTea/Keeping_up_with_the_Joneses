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
|---|---|
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

📌 From those primary questions listed in the introductory paragraph, I have derived the following hypotheses which

### 3.1 Hypothesis 1 `(MVP)` _**"The North-outh Wealth Gap"**_
📌 Hypothesis 1 attempts to look at whether there is a significant difference in disposable income per capita between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean disposable income per capita (US$ PPP) of Northern UK regions is equal to the mean disposable income per capita (US$ PPP) of Southern UK regions.
> 

This is to be validated by:

#### Results & Findings  
📌 In [02_Hypothesis_Testing.ipynb](jupyter_notebooks/02_Hypothesis_Testing.ipynb), I rigorously tested two hypotheses and used pingouin for statistical outputs which is complemented by visualisations using matplotlib.



### 3.2 Hypothesis 2 `MVP` _**"The North-South Happiness Gap"**_
📌 Hypothesis 2 attempts to look at whether there is a significant difference in life satisfaction between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean life satisfaction of Northern UK regions is equal to the mean life satisfaction of Southern UK regions.
> 

This is to be validated by:

#### Results & Findings  
📌 I rigorously tested two hypotheses and used pingouin for statistical outputs which is complemented by visualisations using matplotlib.


### 3.3 Hypothesis 3 `MVP` _**"The North-South Health Gap"**_
 * Hypothesis 3 attempts to look at whether there is a significant difference in life expectancy between the Northern and Southern regions.

>
> H<sub>0</sub>: The mean life expectancy of Northern UK regions is equal to the mean life expectancy of Southern UK regions.
> 

This is to be validated by:

#### Results & Findings  
📌 I rigorously tested two hypotheses and used pingouin for statistical outputs which is complemented by visualisations using matplotlib.


### 3.4 Hypothesis 4 `MVP` _**"Keeping Up with the Joneses" Richer but Happier and Healthier?"**_
* Hypothesis 4 asks where the relationship between income, life expectancy and life satisfaction different in the UK compared to the selected six nations

>
> H<sub>0</sub>: The correlations between income, life expectancy and life satisfaction are the same for the UK and the selected six European nations.
> 


This is to be validated by:

#### Results & Findings  
📌 I rigorously tested two hypotheses and used pingouin for statistical outputs which is complemented by visualisations using matplotlib.



## 4.0 Predictive Modelling Results:
In `??.ipynb`, I created ? models for predicting ...

📌🔍🕵🏻‍♂️ Conclusion: 




## 4.0 Analysis techniques used
* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques. Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?



## 5.0 Dashboard Design
* List all dashboard pages and their content, either blocks of information or widgets, like buttons, checkboxes, images, or any other item that your dashboard library supports.
* Later, during the project development, you may revisit your dashboard plan to update a given feature (for example, at the beginning of the project you were confident you would use a given plot to display an insight but subsequently you used another plot type).
* How were data insights communicated to technical and non-technical audiences?
* Explain how the dashboard was designed to communicate complex data insights to different audiences. 

### 5.1 Dashboard Presentation
📌 An interactive dashboard

* Interactive Tableau Dashboard on [Tableau Public](??) or via [download the Global_Tea_Trade_Dashboard.twb](??)  

![Screenshot of Dashboard](docs/images/??.png) 


## 6.0 Ethical considerations
* Were there any data privacy, bias or fairness issues with the data?
* How did you overcome any legal or societal issues?


# Conclusion 
📌 As the

# Limitations
* This individual capstone project makes



## 7.0 Retrospective Project Plan


## 8.0 Reflections on Challenges
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


# Further Works That May Address Some of These Limitations: 
* To u


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
  * [![wbgapi](https://img.shields.io/badge/wbgapi-blue)](https://pypi.org/project/wbgapi/)
  * [![country-converter](https://img.shields.io/badge/country_converter-red)](https://pypi.org/project/country-converter/)
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