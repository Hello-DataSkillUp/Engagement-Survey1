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
- Demographic variables include gender, race, department, and job level

## Key Metrics
- Recommendation score: Serves as a key indicator of employee satisfaction and engagement. Comes directly from the question "On a scale of 0 to 10, how likely is it that you would recommend DataSkillUp as a place to work?"
- Percentage agreeable: The percentage of responses that are 4 or higher on a 5-point scale. Helps in identifying the proportion of employees who have a positive perception of specific aspects of their work environment.
- eNPS: Employee Net Promoter Score, calculated as the percentage of Promoters (scores 9-10) minus the percentage of Detractors (scores 0-6). Indicates overall employee loyalty and satisfaction.


## Data Preparation
- Ensured there were no missing values in the dataset. 
- All survey question columns were renamed to concise and meaningful names for ease of analysis.
- Transformed the dataset into a long format for specific analyses and visualizations, such as percentage calculations and heatmaps.
- Split the data into its numerical subsets for applying correlation analysis.

## Data Analysis
Combination of summary tables, visual techniques such as density plots, boxplots, heatmaps, and correlation analysis can be used to explore such data meaningfully at an overall level and solve similar problems on other datasets. Below are a few observations from the analysis.

##### _Summary Table_

| Gender | Count | Mean Recommendation Score | Median Recommendation Score | SD Recommendation Score | Mean Percentage Agreeable |  eNPS Score         |
|--------|-------|---------------------------|-----------------------------|-------------------------|---------------------------|---------------------|
| Female | 490   | 6.04                      | 6                           | 1.88                    | 56.93                     | -49.6               |
| Male   | 510   | 6.45                      | 7                           | 2.10                    | 68.08                     | -32.0               |

- Summary table provides an overview of key engagement metrics by gender.
- Survey includes responses from 490 female employees and 510 male employees, providing a balanced perspective across genders.
- Male employees have a slightly higher mean `Recommendation Score` (6.45) compared to female employees (6.04), indicating a marginally higher likelihood of recommending the organization as a place to work.
- Both genders exhibit moderate levels of agreeable responses, with males at 56.93% and females at 68.08%, reflecting different levels of satisfaction.

##### _eNPS Summary Table_

| Gender | Count | Promoters                 | Detractors                  | % Promoters             | % Detractors              |  eNPS Score         |
|--------|-------|---------------------------|-----------------------------|-------------------------|---------------------------|---------------------|
| Female | 490   | 42                        | 285                         | 8.57                    | 58.20                     | -49.6               |
| Male   | 510   | 70                        | 233                         | 13.7                    | 45.70                     | -32.0               |

 
- Summary table for eNPS provides an overview of promoters and detractors by gender.
- The disparity in the number of promoters and detractors between genders underscores potential differences in employee experiences, highlighting specific issues in female employee engagement and satisfaction.
- Addressing the concerns of female detractors could significantly enhance overall employee morale and eNPS scores since a larger proportion of females are dissatisfied with the organization (detractors).

**_This difference in mean recommendation scores, mean percentage agreeable responses, eNPS scores, and the percentage of promoters and detractors warrants a deeper dive into the responses of both genders._**

To explore these differences, visual methods such as density plots, boxplots, and heatmaps are employed to compare the engagement scores and perceptions between male and female employees.

##### _Density Plots_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/69cbce62-7546-4596-a85b-2ecd0b9073c7)


 - Density plots reveal disparities in the responses between genders, indicating distinct behavioral patterns across various metrics.
 - We observe clear differences in survey responses for both groups, particularly in variables such as `TrustInSeniorLeaders`, `OpportunityForGrowth`, `RecognitionForContributions`, `WorkplaceAuthenticity` and `PersonalLifeFlexibility`.
 - For example, we observe that female employees have a pronounced peak at lower scores for `RecognitionForContributions`, suggesting a need for improved recognition practices for females compared to their male counterparts.


##### _Boxplots_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/a7637264-b879-4cd5-8745-8e34f5f7cdd3)


 - Boxplots highlight differences in means and showcase the spread of the two groups, emphasizing disparities in their distributions.
 - We observe that there are differences in means for variables such as `OverallSatisfaction`, `TrustInSeniorLeaders`, `RecognitionForContributions`, `SafeLearningEnvironment` and `BeliefInSurveyAction`.
 - Most variables show overlapping interquartile ranges, indicating that despite differences in means, the middle 50% of responses for each gender often fall within similar ranges.
 - Distibution of variables such as `OpportunityForGrowth` and `PersonalLifeFlexibility`, suggest that some respondents have significantly different experiences compared to the majority.
 

##### _Heatmaps_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/49b8992a-bf89-47d0-bf39-502fd6891ffa)


 - Heatmaps illustrate variations in the percentage of agreeable responses, highlighting the differing responses between genders.
 - We observe stark difference in responses for `PersonalLifeFlexibility`, `OverallSatisfaction`, `OpportunityForGrowth`, `ManagerAutonomy` and `InformedByLeadership`.
 - The disparities in the responses emphasize gender-specific variations, indicating different experiences between male and female employees.
 

To further understand the relationships between various metrics, correlation analysis can be employed to explore the interactions between survey responses for male and female employees.

##### _Correlation Analysis_
![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/e7861a30-127b-4ed2-b354-c65a64a37636)

![image](https://github.com/Hello-DataSkillUp/Engagement-Survey1/assets/165890395/d4e08a1a-9665-46de-aff0-d2773be8dd05)


 - Correlation analysis identifies the most strongly correlated pairs of engagement metrics within each gender group.
 - This analysis also illustrates how different aspects of employee engagement are related within each group.
 - For males, there is strong correlation between pairs such as `SafeLearningEnvironment` and `WorkplaceAuthenticity` (0.48) and `WorkplaceAuthenticity` and `TrustInSeniorLeaders` (0.42).
 - For females, there is slight correlation between `SafeLearningEnvironment` and `WorkplaceAuthenticity` (0.25) and `SafeLearningEnvironment` and `TrustInSeniorLeaders` (0.21).
 - Both male and female employees show a positive correlation between a safe learning environment and workplace authenticity, as well as between workplace authenticity and trust in senior leaders. However, these correlations are stronger for male employees.
 - There is a gender-specific dynamic in how leadership values and learning environments interact. Male employees show a notable correlation between `SafeLearningEnvironment` and the perception that SeniorLeadersValueDifferences. This correlation does not appear in the top correlations for female employees.


## Observations 
- Gender-specific variations exist in responses to several survey questions.
- Targeted interventions in recognition, work-life balance, and leadership trust are necessary to ensure equity in employee experiences and improve engagement.


## Recommendations  
- **_Improve Recognition for Contributions_**: Female employees report lower recognition, indicating a need for better recognition practices targeting female employees.
- **_Enhance Personal Life Flexibility_**: Both genders show low agreement in `PersonalLifeFlexibility`, with females significantly lower, suggesting the need for policies that support work-life balance.
- **_Foster a Safe Learning Environment_**: There is a notable correlation between `SafeLearningEnvironment` and other engagement metrics, especially for males. Enhancing this aspect can have a positive ripple effect.
- **_Increase Trust in Leadership_**: `TrustInSeniorLeaders` is strongly correlated with other positive engagement metrics. Initiatives to build and maintain trust can improve overall engagement.

## Future Analysis Scope  
- Identify key drivers of engagement for the groups. 
- Extend the analysis to demographic categories such as race, department, and job level to identify disparities.

