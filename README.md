# Gender and Workplace Experience
#### _Analytical Approach to Gaining Insights from Engagement Survey Data_

## Introduction
Employee engagement is a critical determinant of organizational success, influencing productivity, retention, and overall workplace satisfaction. However, the employee experience can significantly differ based on one's background, especially between male and female employees.

Engagement surveys, often administered periodically, offer employees an opportunity to provide feedback on their experiences and perceptions within the workplace, helping organizations to gauge satisfaction levels, uncover areas for improvement, and tailor strategies to enhance overall employee engagement. These surveys play a crucial role in capturing employee sentiments and experiences, providing a structured way to gather quantitative data on various aspects of the workplace. By systematically collecting and analyzing survey responses, organizations can identify trends, pinpoint areas of concern, and implement data-driven strategies to enhance the work environment. 

In this project, we utilize data analysis techniques in R to uncover gender-based insights into employee engagement. By identifying differences in work experiences and perceptions between male and female employees, this analysis can guide strategic HR decisions to enhance satisfaction, foster inclusivity, and drive organizational success. Furthermore, the analysis provides a framework that can be applied to other similar datasets. 

_While our focus is on gender, it's important to note that similar analyses can be conducted for various categorical variables within the dataset, such as employee level, race, and location. By addressing these diverse dimensions, organizations can gain detailed insights into the factors shaping engagement experiences, facilitating the creation of inclusive and satisfying workplaces for all employees._


## Problem Statement
As an HR function, we are committed to ensuring that all employees, regardless of background or identity, feel equally engaged and valued. One of the ways that we achieve this is by understanding the differences in engagement between male and female employees. These insights can help create a more inclusive and satisfying work environment for everyone.

## Data Description
- Mock employee engagement survey dataset developed by Aaron Rodriguez. (https://www.linkedin.com/in/aaron-rodriguez-422896101/)
- The dataset includes 1,000 rows and 28 columns, representing the responses of all employees within the organization at the individual level.
- Captures employees' perceptions and attitudes -  quantifying scores for metrics such as recommendation, engagement, satisfaction, leadership perception, and others.
- Features a mix of numeric and categorical data types.
- No missing values were reported in the dataset, indicating completeness and reliability for analysis.
- Demographic variables include gender, race, department, and job level.

## Key Metrics
- eNPS Rating: Serves as a key indicator of employee satisfaction and engagement. Comes directly from the question "On a scale of 0 to 10, how likely is it that you would recommend DataSkillUp as a place to work?"
- eNPS Score: Employee Net Promoter Score, calculated as the percentage of Promoters (scores 9-10) minus the percentage of Detractors (scores 0-6). Indicates overall employee loyalty and satisfaction.
- Percentage agreeable: The percentage of responses that are 4 or higher on a 5-point scale. Helps in identifying the proportion of employees who have a positive perception of specific aspects of their work environment.



## Data Preparation
- Ensured there were no missing values in the dataset. 
- All survey question columns were renamed to concise and meaningful names for ease of analysis.
- Transformed the dataset into a long format for specific analyses and visualizations, such as percentage calculations and heatmaps.
- Split the data into its numerical subsets for applying correlation analysis.

## Data Analysis
Combination of summary tables, visual techniques such as density plots, boxplots, heatmaps, and correlation analysis can be used to explore such data meaningfully at an overall level and solve similar problems on other datasets. Below are a few observations from the analysis.

##### _Summary Table_

| Gender | Count | Mean eNPS Rating          | eNPS Score                | Median eNPS Rating          | StdDevation eNPS Rating |
|--------|-------|---------------------------|---------------------------|-----------------------------|-------------------------|
| Female | 490   | 7.01                      | -15.1                     | 7                           | 1.83                    |
| Male   | 510   | 7.41                      | 6.86                      | 8                           | 2.03                    |

- Summary table provides an overview of key engagement metrics by gender.
- Survey includes responses from 490 female employees and 510 male employees, providing a balanced perspective across genders.
- Male employees have a slightly higher mean eNPS Rating (7.41) compared to female employees (7.01), indicating a marginally higher likelihood of recommending the organization as a place to work.
- Because females have lower scores on the eNPS values, we can infer that some amount of the difference in engagement can be explained by the questions in this survey

##### _eNPS Summary Table_


| Gender | Count | Promoters | Detractors | Neutral | % Promoters | % Detractors | % Neutral | eNPS Score |
|--------|-------|-----------|------------|---------|-------------|--------------|-----------|------------|
| Female | 490   | 98        | 172        | 220     | 20.0        | 35.10        | 44.90     | -15.1      |
| Male   | 510   | 176       | 141        | 193     | 34.5        | 27.65        | 37.84     | 6.86       |


 
- Summary table for eNPS provides an overview of promoters and detractors by gender.
- The disparity in the number of promoters and detractors between genders underscores potential differences in employee experiences, highlighting specific issues in female employee engagement and satisfaction.
- Addressing the concerns of female detractors could significantly enhance overall employee morale and eNPS scores since a larger proportion of females are dissatisfied with the organization (detractors).

##### _eNPS Rating - Visual Inspection_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/705e77f1-1390-4fd9-9273-33fc6d34e4e0)
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/239f4d26-1c5a-4405-b40e-6b12d9823d97)


- Female employees have a broader distribution of eNPS Rating with peaks around 6 and 8, whereas male employees' scores are more concentrated around 7, indicating differences in how likely each gender is to recommend the company.
- Boxplots confirms the summary table statistic - Male employees have a slightly higher median eNPS Rating compared to female employees.

**_This difference in mean eNPS Rating, eNPS scores, and the percentage of promoters and detractors warrants a deeper dive into the responses of both genders._**

To explore these differences, visual methods such as density plots, boxplots, and heatmaps are employed to compare the engagement scores and perceptions between male and female employees.

##### _Density Plots_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/cb9c9701-4542-41dc-9f69-ecd8b023f021)

 - Density plots reveal disparities in the responses between genders, indicating distinct behavioral patterns across various metrics.
 - We observe clear differences in survey responses for both groups, particularly in variables such as `TrustInSeniorLeaders`, `OpportunityForGrowth`, `RecognitionForContributions`, `WorkplaceAuthenticity` and `PersonalLifeFlexibility`.
 - For example, we observe that female employees have a pronounced peak at lower scores for `RecognitionForContributions`, suggesting a need for improved recognition practices for females compared to their male counterparts.


##### _Boxplots_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/2c635f34-d8a7-494c-82d1-26814cd89816)


 - Boxplots highlight differences in means and showcase the spread of the two groups, emphasizing disparities in their distributions. The box shows the InterQuartile Range (IQR), or the middle 50% of values, while the whiskers extend out to Q1 - 1.5x IQR and Q3 + 1.5x IQR
 - We observe that for most questions, the median answer for both males and females is the same. However, there are differences in the medians for the following questions: `OverallSatisfaction`, `SafeLearningEnvironment` and `BeliefInSurveyAction`.
 - Some variables, while having the same median, have offset IQRs where one of the quartiles extends in the positive or negative direction. The following questions reflect where males have higher responses with the same means: `SeniorLeadersValueDifferences`, `TrustInSeniorLeaders`, `RecognitionForContributions`, `WorkplaceAuthenticity`, `ManagerAutonomy`, `OpportunityForGrowth`, `PersonalLifeFlexibility`. 
 - The following questions reflect where females have higher responses with the same median: `RoleCareerAlignment`.


##### _Heatmaps_


![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/fcd93081-8211-47e7-8ddf-b23621b73da5)

 - Heatmaps illustrate variations in the percentage of agreeable responses, highlighting the differing responses between genders.
 - We observe stark difference in responses such as `PersonalLifeFlexibility`, `OverallSatisfaction`, `OpportunityForGrowth`, `ManagerAutonomy`, `SeniorLeadersValueDifferences` and `InformedByLeadership`.
 - The disparities in the responses emphasize gender-specific variations, indicating different experiences between male and female employees.
 

To further understand the relationships between various metrics, correlation analysis can be employed to explore the interactions between survey responses for male and female employees.

##### _Correlation Analysis_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/2d2f36af-c813-4664-8ebe-f60523d2fb51)
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/48b84bac-1703-447c-8089-56a713ca8790)



 - Correlation analysis identifies the most strongly correlated pairs of engagement metrics within each gender group.
 - This analysis also illustrates how different aspects of employee engagement are related within each group.
 - For males, there is strong correlation between pairs such as `SafeLearningEnvironment` and `WorkplaceAuthenticity` (0.48) and `WorkplaceAuthenticity` and `TrustInSeniorLeaders` (0.42).
 - For females, there is slight correlation between `SafeLearningEnvironment` and `WorkplaceAuthenticity` (0.25) and `SafeLearningEnvironment` and `TrustInSeniorLeaders` (0.21).
 - Both male and female employees show a positive correlation between a safe learning environment and workplace authenticity, as well as between workplace authenticity and trust in senior leaders. However, these correlations are stronger for male employees.
 - There is a gender-specific dynamic in how leadership values and learning environments interact. Male employees show a notable correlation between `SafeLearningEnvironment` and the perception that `SeniorLeadersValueDifferences`. This correlation does not appear in the top correlations for female employees.


## Observations 
- Gender-specific differences exist in responses to several categories of survey questions, all of which highlight better experiences for males than females. 
- Targeted interventions in career development & recognition, work-life balance, and leadership trust are necessary to ensure equity in employee experiences and improve engagement.

## Recommendations  
- **_Evaluate Drivers of Low Work-Life Balance_**: Everyone shows extremely low scores in their workload being reasonable, however females have particularly low scores ’PersonalLifeFlexibility`. The question remains - why is this affecting females more than males? Is it more of a reflection of issues with managers and senior leaders? Or is it connected to our in-office policies? Understanding the drivers of this difference will allow us to make the changes necessary to improve this for everyone.

- **_Investigate Issues In Role Fit_**: In many ways, our managers are doing a decent job of supporting their employees. They give timely feedback, care about employees personally, and give solid recognition. Yet, employees are struggling with whether their skills are being used properly and if their role aligns with their interests. There are two possible hypotheses. First, this could be symptomatic of a culture where there is too much red tape - too many meetings, too much documentation, too much planning and not enough actual doing of the job. Or, this could indicate issues in hiring, where we have previously tried to hire flexible generalists to fit into our roles rather than experts. By investigating these issues, we can create an environment where people are more excited about the work they do every day. 


- **_Unconscious Bias Training_**: The differences in the experiences between males and females is stark, particularly in the way they are treated by others. Receiving recognition, receiving information from leaders, having an environment where people can safely learn and make mistakes - these are all tangible behaviors where issues are creeping in. Making headway on these issues would trickle down into more positive perceptions of managers and leaders at the company, and improve overall engagement 

## Future Analysis Scope  
- Identify key drivers of engagement for the groups. 
- Extend the analysis to demographic categories such as race, department, and job level to identify disparities.

## Conclusion
By leveraging summary tables, visual techniques, and correlation analysis, we have quickly investigated key areas where male and female employees have differing experiences and perceptions of the company.  In a few lines of code, we were able to identify three key areas of concern. These insights can guide strategic HR decisions to enhance overall employee satisfaction, address specific gender-based needs, and drive organizational success.


