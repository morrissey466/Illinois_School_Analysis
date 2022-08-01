# School Performance Metrics

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/school_art3.jpg" width="900"/>
</div>

## Objective
The purpose of this project was to analyze which factors are most strongly correlated with student performance.  To get into the details here lets define what we consider performance for the students, the group of students analyzed and the data itself.    

In this review performance will simply be how students scored on standardized testing on SAT, Math & ELA performance scores.  

The group of students included in the data from the Illinois State Board of education data as linked to below. 

https://www.isbe.net/pages/illinois-state-report-card-data.aspx

The defintions for each factor tested are listed at the bottom of this page. 

Lastly the machine learning alogrithm testing will be detialed out as follows below:  

Description of preliminary data preprocessing
The data was pulled from Illinois State Board of Education. We cleaned the data to retrieve our dependent and independent variables.

Description of preliminary features engineering and preliminary feature selection, including their decision-making process
The data can’t be divided into two separate categories because of the mass amount of score variations. This led us to use linear regression over classification analysis.

Description of how data was split into training and testing sets
We used scikit-learn to split the data into four data sets (two being training sets and two being testing sets) and calculated a summary report. X would hold the independent variables and Y would hold the dependent variable. After getting our model.fit, scikit-learn calculates the Y_prediction which is used to get a summary report. The summary report consists of R squared score, mean squared error, and root mean squared error.


## Group Workflow

![FUN AT SCHOOL](https://github.com/smlit30/Project_Test/blob/main/Workflow_7_22.jpg)

### Extract
For our data we found that best available data to test was from the Illinois State Board of Education.  We choose Illinois as the data was readily available, standardized and linked together through and RDTS number so that we could have a primary key to link everything together.  Initial thoughts were to include data from multiple states but the different reporting systems and metrics proved to be too high of a hurdle.  Thus Illinois was choosen as the state to run our test. 

### Transform 
While reviewing the data as shown through the "clean_data" notebook.  We choose factors that had enough data to test throughout the state.  "Enough" in this sense means any column that didn't have at least 750 data points for was dropped in the dataset.  The rest of the file goes through the process of joining the various tables on informaton from general school information, financial information & performance results. This was all gathered into one dataset so it could be reviewed easily and tested through Machine Learning. 

### Load
Once we finalized the dataframe it was then loaded in Amazon Web Services (AWS) in the form of a relational database.  This way the finalized dataframe could be downloaded publicly.  The dataframe was also sent into a CSV file on this github repository.

#### -Database Layout

The below layout is a visual for how our different databases are joined.  The RCDTS is the primary key for all four tables.  

![data_tables](https://github.com/smlit30/Project_Test/blob/main/data_tables.jpg)

### Visualize 
Lastly various visuals were created to give any casual viewer a better understanding of what the data means, how to interpret it and hopefully some usefull insights on how to move forward in the future.  



## Visuals for this Project
Our first visuals includeda layout of zip codes with their proficiency % of ELA & Math scores.
https://public.tableau.com/app/profile/spencer.litzau/viz/FP_Zip1_Trial/Sheet1

https://public.tableau.com/app/profile/spencer.litzau/viz/FP_Zip2_Trial/Sheet2


These next visuals show ELA & Math proficiency of different schools with the average admin salary and vs teach salary as the Y axis. 
https://public.tableau.com/app/profile/spencer.litzau/viz/FP_ELA1_Trial/Sheet6

https://public.tableau.com/app/profile/spencer.litzau/viz/FP_ELA2_Trial/Sheet7

Lastly we have chronic absenteeism compared to math proficiency scores.  
https://public.tableau.com/app/profile/spencer.litzau/viz/FP_MP2_Trial/Sheet5


## Results Summary

We found the following results from our regression test on different school factors for performance.  
  

## Definitions For Tested Factors

<details open>
<summary>DEFINITIONS DROP DOWN</summary>
<br/>
<pre>

### District General Definitions
Type - Options "District or School" - Indicates whether the data is at the school or district level. 

District - Name of School District 

City - City of School/District 

County - County of School/District 

District Type - Determines whether the district includes both elementary school and high shool "UNIT" 

District Size - Broken down into small, medium, and large. Determined by the Illinois State Board of Education. 

Avg Class Size – All Grades  - is the average number of students in each class in a school as of the last day of school.

Student Enrollment - Total students enrolled in that district. 

Student Enrollment - Low Income % - Percent of enrolled students who who receive or live in households that receive Supplemental Nutrition Assistance Program or Temporary Assistance to Needy Families benefits; are classified as homeless, migrant,runaway, Head Start, or foster children; or live in a household where the household income meets the U.S.Department of Agriculture income guidelines to receive free or reduced-price meals.


Avg. Class Size - All grades. The total number of students enrolled divided by the number of classes. 

Avg Teaching Exp - the sum of teaching years for all full-time classroom teachers divided by the number of teachers. 

Bachelor Degree - The percentage of all full-time classroom teachers who have a Bachelor's Degree. 

Masters Degree - The percentage of all full-time classroom teachers who have a Masters Degree. 

Teacher Retention Rate - The three-year average of the percentage of full-time teachers returning to the same school from the previous year. 

Avg. Teacher Salary - the sum of the salaries for all classroom teachers, divided by the number of full-time equivalent classroom teachers.

Avg. Admin Salary -  the sum of the salaries for all school administration, divided by the number of school administration.

### School Factor Definitions

District Type - Determines whether the district includes both elementary school and high shool "UNIT" 

District Size - Broken down into small, medium, and large. Determined by the Illinois State Board of Education. 

Student Enrollment - Total	- Total enrollment for the school. 

Student Enrollment - Low Income % - Percent of enrolled students who who receive or live in households that receive Supplemental Nutrition Assistance Program or Temporary Assistance to Needy Families benefits; are classified as homeless, migrant,runaway, Head Start, or foster children; or live in a household where the household income meets the U.S.Department of Agriculture income guidelines to receive free or reduced-price meals.

Class Size - All grades. The total number of students enrolled divided by the number of classes. 

Teacher Retention Rate - The three-year average of the percentage of full-time teachers returning to the same school from the previous year. 



</pre>
</details>


## Team Work Factors

<details open>
<summary>Communications & Presentations</summary>
<br/>
<pre>

### Communications Protoctal

How we coordinated this project. 

To make sure all team members stayed on the same page we met at least four times a week.  Two for each of the class times during the week (including the office hours in case additional help was needed).  We met an hour prior to Saturday office hours so that we could coordinate any help needed from our TA's and again on Sundays if needed prior to submitting the weekly deliverable.  

In person meetings were set up through Zoom calls between the four members. 

We coordinated our meet ups and zoom calls through the slack app.  This allowed us to keep up with each others progress, ask questions and provide assitance as needed.  We had two channels, one of which was just the team members and the others were the team members and the TA's.  

Project & coding communication was done through github where we could each upload our work where others could see it.  


### Presentation Information

https://docs.google.com/presentation/d/1sUJlMlsgifso6Dr9J_aTH_MecfJC7vevpyQWsx8IgJI/edit#slide=id.g13ee678766f_0_283

</pre>
</details>
