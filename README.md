# School_District_Analysis
## Overview
This is an analysis of math and reading scores of 15 schools of a district by using documents students_complete.csv and schools_complete.csv 

The school board has  that the students_complete.csv file shows evidence of academic dishonesty; specifically, reading and math grades for Thomas High School ninth graders appear to have been altered. Since the school board does not know the full extent of the academic dishonesty, in order to do an acurate analysis, the math and reading scores for Thomas High School were replaced with NaNs while keeping the rest of the data intact.

First analysis has  done without this replacement and then it has done with the replacement and the reasults are discussed in this report.

### Purpose

The purpose is to see how to use loc method in pandas to replace the altered data with NaNs for more acurate analysis and to examine how effect this change on the overall analysis.   

## Results of Analysis and essential points of the code

The loc method has been used to to replace the scores which supposed to be altered with NaNs, the codes are as follows:

> student_data_df.loc[(student_data_df["grade"]=="9th") & (student_data_df["school_name"]=="Thomas High School"),["reading_score"]]=np.nan

> student_data_df.loc[(student_data_df["grade"]=="9th") & (student_data_df["school_name"]=="Thomas High School"),["math_score"]]=np.nan

The the last 10 rows of data frame named "student_data_df" will appeare after that as

> students_data_df_replaced_with_nan.png

In thie frame one cen easily see that the math and reading scores of 9th grade students at Thomas High School (THS) are replaced with NaN and all ather data remained as it was.


### The affect of  replacing the ninth graders’ math and reading scores the district summary

In establishing the data farme "district_summary_df", "new_students_count" was defined as the total number of studennts minus the number of the ninth grade students at THS. Because, to find percentage of passing students it has been used. The number of ninth grader students at THS is calculated by the code

> ninth_grade_at_ths_count=school_data_complete_df[(school_data_complete_df["grade"]=="9th") & (school_data_complete_df["school_name"]=="Thomas High School")].count()["student_name"]

### The affect of  replacing the ninth graders’ math and reading scores on the school summary 

In establishing the data frame "per_school_summary_df", the series "nem_per_school_counts" was defined to use ti calculate perrcentages of passing of math, reading and overall, in which 9th grade students at THS are not included. It is established by the code

> new_per_school_counts=school_data_complete_df.groupby(["school_name"]).count()["math_score"]

I have used here the simple fact that math score does not include 9th grade students at THS, they are all NaN and NaNs are not taken acount in any calculations. This simple manipulation provides Step 5 to Step 14 in the deliveriable 2 to be brought out. That is why in "PyCitySchools_Challenge.ipynb" these spteps are empty.

### The affect of  replacing the ninth graders’ math and reading scores at the Thomas High School’s performance relative to the other schools

### The affect of  replacing the ninth graders’ math and reading scores to general analysis
#### In terms of Math and reading scores by grade

#### In terms of scores by spending

#### In terms of scores by size

#### In terms of scores by school type

## Summary
