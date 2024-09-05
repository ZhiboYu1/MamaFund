# MamaFund
**First-prize project in Rice Datathon 2023**

This is a collaboration project with Bruce Wang, Iris Xue, and Grace Yu. 

**Inspiration**

In the United States, roughly one in eight women and thousands of men will develop breast cancer at some point in their lives. Our group is well aware of the uneven distribution of mammography equipment and training throughout the United States. With our extensive population and breast cancer case predictions, our group aims to allocate limited resources to regions with the most pressing needs. We hope our model and analysis can offer more insights for future policy establishment and resource allocation.

**What it does**

This project predicts the population in 2020, calculates different weights that have impacts on cancer rates, analyzes the current mammography facility distribution, and finds an efficient approach for mammography fund distribution in the year of 2020 using a Least Square Regression Model.

**How we built it**

We divide this challenge into 3 subproblems: Demand side: estimate the population size of different age groups in different regions in 2020; calculate the weights of different elements that influence the cancer rate Supply side: find the distribution of medical facilities Fund allocation methods

1(a) We predicted the 2020 population based on the provided dataset from 2010-2019. Initially, we tried three most historically used models, including Malthus, Logistics, and Leslie. All of these were not adopted because they require many more factors (including regional economy, people’s mindsets, etc) than what is available in the provided dataset.

As we furthered our research, we found that Pearson’s correlation coefficient of the population change rates between two respective years is statistically high (around 0.697), which propels us to use the autoregression model. We successfully estimated the 2020 population across different ages and regions at the end.

1(b) To calculate the weight of different variables affecting breast cancer incidence, we imported a new dataset containing breast cancer cases by year, age, and sex groups. When we examined the case counts vs. time graph, we noticed that the trend line approximates a flat increase as time elapses. However, we believe this may result from the overall population growth from 2010-2019. Therefore, we decided to use crude breast cancer rate (breast cancer cases divided by the overall population) instead of the cancer cases to exclude the influence of the general population trend from our weight calculations.

Then we tried the Entropy Weight Method (EWM) to calculate the weights of age and sex to the breast cancer rates. This weighting method measures value dispersion from our dataset. The greater degree of dispersion means greater differentiation so that more information can be derived; hence, more weight should be given to this factor. This model ideally fits our datasets as we only investigate the relative importance of two variables. This method also avoids the interference of human factors on the weight of indicators, therefore enhancing the objectivity of our evaluation results. After this, we took standardized crude rate(S Rate) using the standardization formula to calculate the specific weighted influence of different age and sex groups on cancer rate given statistics from datasets we found.

2(a) For the demand side, we processed the mammography facility dataset. We cleaned the data, fixed the data serial problems, and counted the number of facilities in each state. We then drew a choropleth map based on the facility distribution.

3 We developed three different mathematical models to find the best fund allocation method.

(1) "Inverse Ratio Method". We took the inverse ratio of the facility-demand ratio and then calculated the ratio of each state's respective ratio to the sum ratio of all states to determine the percentage of funds we allocate to each state. However, we realized this is not a very efficient method because the resource allocation is too even, which won't resolve the unfair distribution of medical resources.

(2) "Gap Filling Method". We put funds step by step in the states where the supply-demand ratio is the lowest until the gap is filled. However, this approach is too extreme and biased. Also, since the number of funds is not provided, we cannot calculate the exact fund allocation ratio.

(3) "Least Square Regression Model Method". This is our final allocation solution method. We constructed a least square regression model with the best-fit line passing through the origin point based on the Demand (x-value) and Supply (y-value). We decided to allocate all scarce resources to states whose observed y-value is lower than the expected y-value on the model. For all states below the regression line, we calculate the residual for each state to the sum of the residuals to determine the ratio of funds we allocate to each state. Compared with the previous methods, it focuses on the states with extremely scarce resources (such as California), and covers all the below-average states simultaneously.

**Challenges we ran into**

Find useful models that can fit into the given dataset and meet the objectives of our project.
Learning new mathematical models including different regression models (Linear, AutoRegression, Logistic),
Convert the goals of our project into concrete mathematical formulas that can be processed.

**Accomplishments that we're proud of**

Meaningful findings of connections between variables that are statistically significant in our final fund allocation plans. Eg.1., Females aged 65-80 are statistically more likely to be diagnosed with breast cancer. Eg.2., Compared with males, female breast cancer rates are significantly higher.
Drew graphs that are both aesthetically pleasing and could clearly visualize our findings of variable connections.
We showed continuous improvements through the development of three different approaches to allocating funds. For each approach, we explore its advantages and shortcomings and develop a new approach that eliminates the shortcomings of the previous one to optimize resource allocation.

**What we learned**

How to split a general problem into smaller separate tasks that are easier to approach;
Group Collaboration. In this project, we learned the importance of modularity. Our team members are assigned separate but closely related tasks. Throughout the entire project, we worked simultaneously while still communicating with each other to share ideas and organize our inputs and outputs into the same format, so that our module works can be combined into an entire comprehensive analysis project.
Technical Skills: Data Visualization, Data Cleaning, Mathematical Modelling, Python

**What's next for MaMaFund**

We’ll try to cover more multi-dimensional factors, such as climate, diet, race, culture, etc, and use better models to weigh each variable.
States are too general for us to examine our facility distribution. We may split states down into more separate areas so that I can express our concerns to more minority groups.
In population prediction, we may introduce machine learning to help us find features that could not be easily predicted by humans so that we can better predict future demand distributions.
We may develop more reasonable ways to allocate funds. Currently, we arbitrarily ignore areas that we believe are above average. However, in the real world, our fund distribution should take all regions into our consideration.

**References:**

The dataset of breast cancer cases from 2010-2019: https://wonder.cdc.gov/ Entropy-Weight-Method-Based Integrated Models: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9317321/ Breast Cancer Facts and Statistics: https://www.breastcancer.org/facts-statistics
