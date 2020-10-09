# SCHOOL DISTRICT ANALYTICS PROJECT
## Summary
The purpose of this analysis is to demonstrate the effect that removing a case of academic dishonesty at Thomas High School (THS) has on the overall School District Analysis Results. The technical challenge is to use Python Pandas library in Jupyter Notebook to adjust the data to exclude the Thomas High School scores and recalculate the overall school district statistics.    
### Background
The original School District Analysis used two datasets to produce a grid of statistics by which Maria, the chief data scientist for the School District, could present to her superiors to see what was happening with math and reading scores by school and type in the district.  Data was also provided about the budget of the schools to see if there is any correlation between the amount of funds spent at a school and the level of test scores.  However, Maria noticed an anomaly in the results for Thomas High School and has requested that the analysis be re-run removing the 9th grade scores for that School and recalculating all the statistics.
# ANALYSIS
Since the school analysis code was already written for the first analysis, that code is used as a basis for the new analysis.  The first task is to take the combined data set that had been cleaned already, and to replace all the 9th grade test scores for THS for both reading and math with the NaN value.  In order to do this, the Numpy dependency is imported along with Pandas.  Numpy contains the .NaN value that is used to replace the real scores. 
  ```import numpy as np```
In order to replace the scores in the dataframe student_data_df, the ```loc``` function is used to identify the particular school, grade and score that is going to be replaced as shown in the following code:  

>```student_data_df.loc[(student_data_df["grade"]== "9th") ```
```& (student_data_df["school_name"]== "Thomas High School"),["reading_score"]]=np.nan```
  
1.  DISTRICT SUMMARY - A comparison of the relevant statistics before and after changing the 9th grades scores for the District as a whole using the total students as the denominator for both:  
  
||Before Change | After Change|
|----------|---------------|---------------|
| Total Student Count | 39,170 | 38,709 |
| 9th Grade Thomas student count| 461| 461|
| Average Passing Math% District wide | 75.0 | 74.8|
| Average Passing Reading% District wide | 85.8 | 85.7|
  
the District Summary figures calculated in the analysis both before and after removing the 9th grade scores, use the total student count in the denominator.  This isn't quite right for a proper comparison because it is like 461 students getting all 0s and averaging that in.  This will cause the passing scores to go down overall.  

The District Summary before the change looked like this:
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/Dist_Sum_before.PNG)
  
After the removal of THS 9th graders, the district summary looks like this:
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/Dist_Sum_after.PNG)
 


2.  SCHOOL SUMMARY - A summary of the results with the THS passing percentages calculated as a percent of the total students at the school show that at 66.9% passing math and 69.66 passing reading, shows the problem with the calculation of using the total students at the school as the denominator.

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/Summary_by_school_before.PNG)
  
However, after changing the denominator to exclude the 9th graders, the passing percents go up to 93.2% for math and 96.9% for passing reading as shown in the following chart:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/Summary_by_school-after.PNG)

A comparison for the % Passing results prior to removing the 9th grade scores versus after removing 9th grade using the proper denominator is shown below:
  

|THS|Before Change | After Change|
|----------|---------------|---------------|
| Total Student Count | 1635 | 1635 |
| 9th Grade Thomas student count| 461| 461|
| Average Passing Math% THS wide | 93.3 | 93.2|
| Average Passing Reading% THS wide | 97.3 | 96.9|
| Overall Passing % THS wide |90.95 | 90.6|
  
So there was a slight decrease in the passing percentage overall after removing the 9th grade scores for THS.

  

3.  THOMAS HIGH SCHOOL VERSUS OTHER SCHOOLS - Removing the ninth graders' math and reading scores for Thomas High School moved the school overall passing score from 90.95% to  90.63%.  This small decrease did not change the schools range based on overall score as compared to other schools.  They are still then 2nd highest scores. 

Top Schools before removing 9th grade at THS:
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/top%20schools%20before.PNG)
  
Top Schools after removing 9th grade at THS:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/Rank%20by%20school.PNG)

4. AFFECT ON MATH AND READING SCORES BY GRADE

There is no affect on the math and reading scores for any grade except the 9th grade for THS.  

The reading scores by grade before the 9th grade scores are removed are as follows:
  
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/before%20reading.PNG)

The reading scores by grade after the 9th grade scores are removed are as follows:
  
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/after%20reading.PNG)

The math scores by grade before the 9th grade scores are removed are as follows:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/before%20math.PNG)

The math scores by grade after the 9th grade scores are removed are as follows:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/after%20reading.PNG)

5. AFFECT ON SCORES BY SCHOOL SPENDING

The effect on the statistics by school spending is so small, that the figures must be shown out to 2 decimals to see any difference.  The only buckect that changed is the one that contains THS which is $630-644

Results by Budget Bin before removing 9th grade scores:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/bofre%20spending.PNG)

Results by Budget Bin after removing 9th grade scores:
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/after%20budget.PNG)


6. AFFECT ON SCORES BY SCHOOL SIZE

Likewise, there was no noticeable change in overall results based on school size:

![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/before%20size.PNG)
![]( https://github.com/xactuary/School_District_Analysis/blob/master/Resources/after%20size.PNG)
  
7. AFFECT ON SCORES BY SCHOOL TYPE
  
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/before%20by%20district.PNG) 
![](https://github.com/xactuary/School_District_Analysis/blob/master/Resources/after%20type.PNG) 

