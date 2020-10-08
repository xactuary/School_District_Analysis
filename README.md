# SCHOOL DISTRICT ANALYTICS PROJECT
## Summary
The purpose of this analysis is to demonstrate the effect that removing a case of academic dishonesty at Thomas High School has on the overall School District Analysis Results. The technical challenge is to use Python Pandas library in Jupyter Notebook to adjust the data to exclude the Thomas High School scores and recalculate the overall school district statistics.    
### Background
The original School District Analysis used two datasets to produce a grid of statistics by which Maria, the chief data scientist for the School District, could present to her superiors to see what was happening with math and reading scores by school and type in the district.  Data was also provided about the budget of the schools to see if there is any correlation between the amount of funds spent at a school and the level of test scores.  However, Maria noticed an anomaly in the results for Thomas High School and has requested that the analysis be re-run removing the 9th grade scores for that School and recalculating all the statistics.
# ANALYSIS
Since the school analysis code had already been written for the first analysis, that code is used as a basis for the new analysis.  The first difference, however, is to take the combined data set that had been cleaned already, and to replace all the 9th grade test scores for both reading and math with the NaN value.  In order to do this, the Numpy dependency is imported along with Pandas.  Numpy contains the .NaN value that is used to replace the real scores. 
  ```import numpy as np```
In order to replace the scores in the dataframe student_data_df, the ```loc``` funciton is used to identify the particular school and grade and score that is going to be replaced as shown in the following code:  

>```student_data_df.loc[(student_data_df["grade"]== "9th") ```
```& (student_data_df["school_name"]== "Thomas High School"),["reading_score"]]=np.nan```
  
A comparison of the relevant statistics before and after changing the 9th grades scores for the District as a whole usng the total students as the denominator for both:  
  
||Before Change | After Change|
|----------|---------------|---------------|
| Total Student Count | 39,170 | 38,709 |
| 9th Grade Thomas student count| 461| 461|
| Average Passing Math% District wide | 75.0 | 74.8|
| Average Passing Reading% District wide | 85.8 | 85.7|
  
The district analysis is mis-leading because it removes the scores for the 9th graders at Thomas High School but still divides the remaining scores by the same denominator.  So it looks like the passing percent is going down when in fact, it may be going up.  Therefore it is necessary to dig deeper to see what is really going on.

A summary of the results with the Thomas High School passing percentages calculated as a percent of the total students at the school looks like this:






