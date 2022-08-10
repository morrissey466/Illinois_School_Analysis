# School Performance Metrics

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/school_art3.jpg" width="900"/>
</div>

## Objective
Throughout this project our team aimed to see which factors might be most strongly correlated with school perforamnce results.  In the preceeding text we will provide context on how we gathered our data (including what we didn't include), how we transformed the data from its original context to something that could be put into a database and tested through machine learning.  Then finally show visualizations that accurately reflect what we found.  

   
## Group Workflow

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/Workflow_7_22.jpg" width="900"/>
</div>

### Extract
There is an abundance of school data out on the internet so the first challenge was selecting usable data.  We first considered nationwide by state but different states record results with different breakdowns and tracking methods.  This lead us to choose one state that collected all of its data the same way and the state that did this the best was Illinois.  

The most reliable information we could find was from the Illinois State Board of Education found at the below URL. 

https://www.isbe.net/pages/illinois-state-report-card-data.aspx

In this dataset we found the best performance metrics were the results from Standardized test metrics on Math & ELA (English & Language Arts) scores.  

In the next section, Transform, we will go through the tools and methods used to filter this information down to be useful.  

### Transform 
To transform the data to be more usable in our test we looked at all the factors that data was collected on including proficiency from low income families, total students (with breakdown by race and age), attendance rate, mobility rate, dropout & graduation rates with many others. Using Python & Pandas we created filters so that we dropped any data that didn't have sufficient data collected (less than 750 districts).  Our team then reviewed the remaining data and used what we though would have the strongest correlation to the test performance results.  

The main tools here were simply using python & pandas to create and manipulate dataframes from the initial csv files downloaded from the state.  

### Load
Using python the dataframes were then uploaded to a sql database hosted on Amazon Web Services.  This way the end results could be pulled from a public database and available to the public.  

The relational database layout is set up as shown below with the primary key as the district RDTS number.  This is a unique number that identifies each individual school district with the data associated with it.  

#### -Database Layout

The below layout is a visual for how our different databases are joined.  The RCDTS is the primary key for all four tables.  
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/data_tables.jpg" width="900"/>
</div>


Lastly the machine learning alogrithm testing utilized through Python found the following results:  

Description of preliminary data preprocessing
The data was pulled from Illinois State Board of Education. We cleaned the data to retrieve our dependent and independent variables.

Description of preliminary features engineering and preliminary feature selection, including their decision-making process
The data can’t be divided into two separate categories because of the mass amount of score variations. This led us to use linear regression over classification analysis.

Description of how data was split into training and testing sets
We used scikit-learn to split the data into four data sets (two being training sets and two being testing sets) and calculated a summary report. X would hold the independent variables and Y would hold the dependent variable. After getting our model.fit, scikit-learn calculates the Y_prediction which is used to get a summary report. The summary report consists of R squared score, mean squared error, and root mean squared error.

The below is the R2 equation that was used to calculate how well the factors fit the model.  
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/equation.jpg" width="500"/>
</div>


The following pictures show the follwing results between the Math & ELA results between the factors of class size and schools with low income families. 

Class Size & ELA Scores
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/class_size_ELA.jpg" width="500"/>
</div>

Class Size & Math Scores
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/class_size_math.jpg" width="500"/>
</div>

School % of low income families & ELA Scores
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/low_income_ELA.jpg" width="500"/>
</div>

School % of low income families & Math Scores
<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/low_income_math.jpg" width="500"/>
</div>

The remaining factors yielded the below results of our linear regression algorithm.  


<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/lr_hs_results.jpg" width="500"/>
</div>

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/lr_ds_results.jpg" width="500"/>
</div>

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/lr_fn_results.jpg" width="500"/>
</div>

Each table shows the impact of each factor toward the model score. In the High School table, we can see Teacher Retention Rate, Community College Remediation, and Chronic Absenteeism being factors in causing the model to decrease. This shows they are import factors to determined the student success. 

In the District table, we can see Student Enrollment – Low Income being the only big factor in causing the model to decrease. This decreases the model below 0.4 making it a huge factor in student success. 

In the Financial table, we can see the factors make little differences when it comes to student success. 


### Visualize 
The following visualizations help give a layout to what we found with our results and are presented through Tableau.    



## Visuals for this Project
To help better display our results and finding the below tableau visualization dashboard is available.  

https://public.tableau.com/app/profile/spencer.litzau/viz/IllinoisSchoolData8-6/Dashboard1

The map shows the different city each district is in with a description of the ELA & Math scores when it is highlighted.  The graphs show a combined score for the ELA & Math versus different variables to show which factors may play a role in helping improve test score performance. 

You can also select different tabs to get a more in depth look at each graph.  



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

### Communications Protocol

How we coordinated this project. 

To make sure all team members stayed on the same page we met at least four times a week.  Two for each of the class times during the week (including the office hours in case additional help was needed).  We met an hour prior to Saturday office hours so that we could coordinate any help needed from our TA's and again on Sundays if needed prior to submitting the weekly deliverable.  

In person meetings were set up through Zoom calls between the four members. 

We coordinated our meet ups and zoom calls through the slack app.  This allowed us to keep up with each others progress, ask questions and provide assitance as needed.  We had two channels, one of which was just the team members and the others were the team members and the TA's.  

Project & coding communication was done through github where we could each upload our work where others could see it.  


### Presentation Information

https://docs.google.com/presentation/d/1sUJlMlsgifso6Dr9J_aTH_MecfJC7vevpyQWsx8IgJI/edit#slide=id.g13ee678766f_0_283

</pre>
</details>
