# Pewlett Hackard Analysis

## Overview

I have been tasked to help Bobby, an up and coming HR analyst, for  ***Pewlett Hackard***, a large company boasting several thousand employees. As baby boomers begin to retire at a rapid rate, Pewlett Hackard is looking toward the future in 2 ways.
1) First, it's offering a retirement package for those who meet certain criteria
2) Second, it's starting to think which positions will need to be filled in the near future. The number of upcoming retirements will leave thousands of job openings. What would happen to a company if they didn't look ahead and prepare for this many vacancies? It probably won't be pretty. 

Bobby, specifically, needs to find answers to the following questions.
* Who will be retiring in the next few years?  and 
* How many positions will Pewlett Packard need to fill?

This analysis will help future-proof Pewlett Hackard by generating a list of all employees eligible for the retirement package. The employee data Bobby needs is only available in the form of 6 CSVs because Pewlett Hackard has been mainly using Excel and VBA to work with their data. But now they have finally decide to update their methods and insted use SQL, a definite upgrade considering the amount of data. 

My task is to help Bobby build an employee database with SQL by applying my data modelling, engineering and analysis skills.

## Purpose of this Analysis
As a part of my past assignment at Pewlett Hackard, I analysed various factors and created the following tables.
1. retirement eligibility
2. retirement_info
3. current_emp
4. number_of_employees_retiring_per_department
5. manager_info
6. dept_info

Now Bobby's manager has given both of you two more assignments: determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program. Then, we’ll write a report that summarizes our analysis and helps prepare Bobby’s manager for the “silver tsunami” as many current employees reach retirement age.

## Analysis Results

Four major points from the two analysis deliverables. 

1) ### Retirement Titles 
    The total number of records retreived was **133,776**. However it does not tell us the correct number of people about to retire - there are a lot of duplicate entries. 
    
    **Image 1 (below): Table - Retirement Titles**

    ![Retirement Titles](./Resources/retirement_titles.png)
    
    
    The reason behind the duplicates records is that the data is coming straight out from the table **titles**, which contains all the titles that a person has ever held while working with Pewlett Hackard. The table **titles** has **443,308** records as compared to **300,024** in the table **employees**.

    TAKEAWAY - If we have a table that has the latest titles of all employees, many steps can be saved. In the past Pewlett Hackard has been using EXCEL and VBA - with SQL, this table can be create using some lines of code
    ```
    SELECT  DISTINCT ON (emp_no)
	    emp_no,
	    title,
	    from_date,
	    to_date
    INTO latest_titles_of_employees
    FROM titles
    ORDER BY emp_no;
    ```
    This new table **latest_titles_of_employees** has **300,024** records, the same as the employees table. 

2) ### Unique Titles
    We retrieved the unique people that are set to retire. The number came out to **90,398**. With a total employee count of **300,024**, this points to the fact that **30.13%** of employees of Pewlett Hackard are set to retire.

    **Image 2 (below): Table - Unique Titles**

    ![Unique Titles](./Resources/unique_titles.png)

    The table and the % of people that are set to retire points to the tough task in front of the HR department. Assuming that Pewlett Hackard is not overstaffed, 30% of less people could have a dramatic effect on the productivity of the company and even its viability. The time to Act is NOW!

3) ### Retiring Titles
    This table kind of explains the reason why this has come to the point of a a **Silver Tsunami**. Assuming a normal distribution, Managers constitute 0.000022% of the workforce. With so less managers, there is no one talking to the HR team about team members reaching retirement age.

    **Image 3 (below): Table - Retiring Titles**

    ![Retiring Titles](./Resources/retiring_titles.png)

    While the HR team should work on replacing all titles, it should also think about increasing the % of managers, and having ongoing (bi-annual/quarterly) discussion about their staffing situations and needs.

3) ### Mentorship Eligibility

    ![Mentorship Eligibility](./Resources/mentorship_eligibilty.png)

## Summary

Summary: Provide high-level responses to the following questions, then provide two additional queries or tables that may provide more insight into the upcoming "silver tsunami."

* How many roles will need to be filled as the "silver tsunami" begins to make an impact?

    The total number of people people who will be retiring is **90,398**

* Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?

    The total number of qualified, retirement-ready people ready for mentorship is **1,549**