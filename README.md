# Exploratory Data Analysis - Chi-Square 

*Original coursework for D207 – Exploratory Data Analysis, Western Governors University.*

## Part A: The Analysis Question

**A1. Are the Marital status and Internet Service variables correlated with churn?**

**A2. Purpose of Analysis**
In the highly saturated market of the telecommunications industry, customer defection poses a real threat. Given that it costs about ten times the amount to convert a new lead to a customer, reducing customer churn becomes even more important than acquiring new ones. The search and identification of customers who show a high inclination to abandon the company or customer churn prediction is of crucial importance as part of a customer-oriented retention strategy that aims to reduce customer churn (De Caigny et al. 2018). Therefore, identifying what independent variables are correlated to churn will help identify customers who are at high risk of leaving and potentially build a high risk of churn customer profile.

**A3. Variables used in Analysis**
The variables from the churn dataset we will be focusing on our analysis on are Churn, Marital, and Internet Service. All of which are nominal variables, churn tells us whether the customer discontinued their service within the last month using Yes or No values. The marital status is held in the Marital column and Internet Service shows what type of internet service the customer has if any.

## Part B

**B1.** See `chi_square_analysis.ipynb` file.

**B2. Output**
Looking at the outputs from my code, the Chi-Square value for the independent test of the Marital and Churn variables is 5.566, the p value is 0.234, and the degrees of freedom equal 4. As for the chi-square independent test conducted on the Internet Service and Churn variables, the chi-square value is 87.462. The p value is 1.018e-19 and the degrees of freedom equal 2.

**B3. Chi-Square test for independence justification**
When examining the relationship between variables, considering the variable types is key to determining what kind of test is best to assess the relationship. If all variables are nominal, like in our analysis using the Churn, Marital, and Internet Service variables, the Chi-Square independence test is best prescribed. Chi-Square is performed using the scipy package and requires no normality test like in the t-test and ANOVA methods which means it does not make assumptions about the population distribution. It instead examines the proportions of discrete categories which is exactly what we need to test a categorical dependent variable. The key assumptions associated with this test are that we are dealing with a random sample from the population and each subject cannot be in more than 1 group in any variable. Both assumptions are met by our nominal variables from the churn dataset. Therefore, I chose to work with the Chi-Square test to determine if the Marital status and Internet Service variables are correlated with customer Churn.

## Part C: Distributions of variables using univariate statistics

**C1. Continuous and Categorical variables**
The continuous variables described in this univariate analysis are Income and Tenure. The categorical variables described are Area and Contract. The mean Income value is 39806.93 and the Income standard deviation is 28199.92, while the mean Tenure was 34.526 months with a standard deviation of 26.443 months. The minimum Income is 348.67, first quartile is 19224.43, second quartile is 33170.61, third quartile is 53247.11, and lastly the maximum Income was 104166.7. The minimum Tenure is 1, first quartile is 7.92, second quartile is 35.43, third quartile is 61.48, and lastly the maximum Tenure was ~72 months.

The relative frequencies for the variable Area is 3346/10000 for Suburban areas which is about 0.335, whereas both the Rural and Urban areas have a relative frequency of 3327/10000, or about 0.333. As for the Contract variable, Month-to-month had the greatest relative frequency with 5456/10000 or about 0.546, Two year was 2442/10000 or 0.244, with One year closely behind 2102/10000 or roughly 0.210.

<table>
<tr><td><img src="/income_boxplot.png" width="420"/></td><td><img src="/tenure_boxplot.png" width="420"/></td></tr>
<tr><td><img src="/income_histogram.png" width="420"/></td><td><img src="/tenure_histogram.png" width="420"/></td></tr>
<tr><td><img src="/area_barchart.png" width="420"/></td><td><img src="/contract_barchart.png" width="420"/></td></tr>
</table>

## Part D: Distributions of variables using bivariate statistics

**D1. Continuous and Categorical variables**
The continuous variables described in this bivariate analysis are Tenure and Outage_sec_perweek, and their Pearson's correlation coefficient is ~0.003. 

The categorical variables described are Churn and Internet Service that have a Cramer's V value of 0.094.

<table>
<tr><td><img src="/tenure_outage_scatter.png" width="420"/></td><td><img src="/churn_by_internetservice.png" width="420"/></td></tr>
</table>

## Part E: Summary of Data Analysis

**E1. Results of Hypothesis Test**
The purpose of this analysis was to answer the question of "Are the Marital status and Internet Service variables correlated with churn?" Given that our dependent and independent variables are categorical the Chi-Square test for independence was used to answer the analysis question. Our test yielded that the p value for the Marital variable was 0.234 which is greater than the alpha value of 0.05 and that our Chi-Square value is 5.566, with the degrees of freedom equal to 4. Looking at the Chi-Square value table for alpha = 0.05 and degrees of freedom equaling 4 we get a Chi-Square value of 9.488. This means that our Chi-Square value is far too small to be statistically significant and therefore we must accept the null hypothesis that Marital status does not correlate with churn. Contrary to this result our Chi-Square test for independence for Internet Service and Churn rejected the null hypothesis. Our Chi-Square value for this test is 87.462 with a p value of 1.018e-19 which means that we can safely accept the alternative hypothesis that there is a significant relationship between customer churn and the Internet Service they have.

**E2. Limitations of Analysis**
As mentioned in the class materials, correlation does not imply causality. Therefore, we cannot assume that a customer churns solely based on their Internet Service, only confirm there is a relationship between the two variables using the Chi-Square test. Lastly, if we want to draw meaningful conclusions from the analysis the number of samples in each test needs to be sufficiently large, which may not be the case.

**E3. Recommendations**
Now that we have concluded our analysis and found that indeed there is a correlation between churn and the internet services variables we can focus on our bivariate distribution of the two variables. When looking at the distribution graph the customers who had no internet service or Fiber Optic showed less of an inclination to churn whereas those who had DSL service had a higher percentage of churn. This points to a potential service level gap, reviewing DSL customer satisfaction and feedback could shed light on why customers with DSL have a higher rate of churning than those with no internet or Fiber Optic. My recommendation to stakeholders is to review the DSL customer feedback and compare it to that of those with Fiber Optic.

## Third-Party Code References

Chi2_contingency#. chi2_contingency - SciPy v1.14.1 Manual. (n.d.). https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.chi2_contingency.html

Zhang, D. (2020, August 13). Chi-square test for independence in python with examples from the IBM HR Analytics Dataset. Medium. https://towardsdatascience.com/chi-square-test-for-independence-in-python-with-examples-from-the-ibm-hr-analytics-dataset-97b9ec9bb80a#3750

## References

De Caigny, A., Coussement, K., & De Bock, K. W. (2018). A new hybrid classification algorithm for customer churn prediction based on logistic regression and decision trees. *European Journal of Operational Research, 269*(2), 760–772. https://doi.org/10.1016/j.ejor.2018.02.009

Zhang, D. (2020, August 13). Chi-square test for independence in python with examples from the IBM HR Analytics Dataset. Medium. https://towardsdatascience.com/chi-square-test-for-independence-in-python-with-examples-from-the-ibm-hr-analytics-dataset-97b9ec9bb80a#3750

