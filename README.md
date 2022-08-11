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



### Visualize 
The following visualizations help give a layout to what we found with our results and are presented through Tableau.    



## Visuals for this Project
To help better display our results and finding the below tableau visualization dashboard is available.  

https://public.tableau.com/app/profile/spencer.litzau/viz/IllinoisSchoolData8-6/Dashboard1

The map shows the different city each district is in with a description of the ELA & Math scores when it is highlighted.  The graphs show a combined score for the ELA & Math versus different variables to show which factors may play a role in helping improve test score performance. 

You can also select different tabs to get a more in depth look at each graph.  

## RESULTS

The Equation used for getting these results:

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/results1.jpg" width="500"/>
</div>

How did the factors affect SAT scores?
We broke up these factors up into 3 sections, High Schools, Districts, and District Financials. 

These factors gave results we expected and some not so much. 

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/results2.jpg" width="500"/>
</div>

We can see Teacher Retention Rate, Advance Courses, Physical Education, and Avg Class Size all giving positive correlations towards SAT scores. Then, Community Remediation, Chronic Absenteeism and Chronic Absenteeism Low Income showing negative correlations. Most of the positive correlations were expected but two surprising factors were Avg Physical Education and Avg Class Size. We tend to see lower student teacher ratio being better but from the data we can conclude otherwise.

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/results3.jpg" width="500"/>
</div>

We can see Student Enrollment, Avg Class Size, Avg Teaching Experience, Master Degree, Teacher Retention Rate, Teacher Avg Salary, and Admin Avg Salary all have giving positive correlations towards SAT scores. Then, Student Enrollment Low Income and Bachelor Degree showing negative correlations. Most of these were to be expected with more experience comes better performance. But Bachelor Degree being negative was surprising. A high amount of Bachelor degree teachers may be new teachers which would trend well with the avg teaching experience. 

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/results4.jpg" width="500"/>
</div>

We can see Total Expenditures, Education Funding, and Local Property Taxes all have giving positive correlations towards SAT scores. Then, Total School Tax Rate, General Admin Dollars, General Sate Aid Dollars, and Federal Funding showing negative correlations. Each of these districts were looked at per student to make everything similar. The total school tax rate has a major correlation in the negative. 

The Equation used for getting these results:

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/equation.jpg" width="300"/>
</div>

Next, we decided to see how each factor affected the predicted model. These are the R squared results:

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/final1.jpg" width="500"/>
</div>

There were 2 factors which made significant impacts to the predicted model, Community College Remediation and Chronic Absenteeism. 

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/final2.jpg" width="500"/>
</div>

There was 1 factor which made significant impact to the predicted model, Student Enrollment – Low Income %. This factor shows how important a homelife environment can impact a student’s success. This dropped the model prediction by 43%. 

<div id="header" align="center">
    <img src="https://github.com/smlit30/Project_Test/blob/main/final3.jpg" width="500"/>
</div>

For Financial, we can see the factors make little differences to the predicted model. 

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
