# Pewlett Hackard Analysis

Software: pgAdmin 4, Visual Studio Code Version: 1.57.1 

### Overview

Pewlett Hackard is a large company looking to prepare for a large number of retirements. To aid in preparing for this, they hire an analyst to perform employee research. Specifically, the purpose of the analysis is to help Pewlett Hackard 
(1) determine the number of retiring employees per title and (2) identify employees who are eligible to participate in a mentorship program. To assist with this research, we will help the analyst build an employee databasewith SQL.

### Method
Six csv files were provided and are included in the Data folder. Using these files, an entity relationship diagram was created using an online platform, QuickDBD (quickdatabasediagrams.com). pgAdmin was used to explore relationships between tables and ultimately select for retiring employees by title born between January, 1, 1952 and December 31, 1955. Parameters including emp_no, first_name, and last_name were retrieved from the Employees table and the title, from_date, and to_date columns were retrieved from the Titles table. The original csv files of these tables can be found in the Data folder. The tables were joined on the primary key, emp_no, and filtered on the birth_date column. This new relationship was stored in the Retirement Titles csv also found in the Data folder. Beause this table contained duplicate entiries, reflecting employees who may have siwtched titles, the DISTINCT ON statement was used to retrieve the first occurence of the employee number to gauge an accurate count of retiring employees without duplicates. This filtered list was stored in Unique Titles csv. Finally, the Unique Titles table was joined with the titles column from the Titles csv to create a Retiring Titles table. 

To determine the employees eligibile for the mentorship opportunity, a query was written to retrieve emp_no, first_name, last_name, and birth_date from the employees table. This was joiend with the from_date and to_date from the Department Employee table and the title column from the Titles table. The table was filtered for those employees born between January 1, 1965 and December 31, 1965. 

### Results
1. A total of 90,398 employees are eligible for retirement (~30 percent of the total employees at Pewlett Hackard).

2. The Retiring Title table below (**Fig. 1**) shows that a majority of the employees eligible for retirement hold senior positions (Senior Engineer or Senior Staff). 

3. As shown in **Fig. 1**, a majority of those retiring hold technical positions, versus managerial.

**Fig. 1**

<img width="178" alt="Screen Shot 2021-06-21 at 12 05 02 AM" src="https://user-images.githubusercontent.com/45336910/122705668-35e83c80-d224-11eb-84de-552c5c5f2eb1.png">

4. 1,549 employees are eligible for the mentorship program, which represents ~1.5% of those eligbile for retirement.

### Summary
90,398 jobs will need to be filled as those born between 1952 and 1955 retire. However, only 1,549 employees are eligible for the mentorship program.  We also recomment the following two queries:

1. Determine the titles of those eligible for the mentorship program. This will confirm that there are enough mentors with each title to train for each position. For example, there does not seem to be mentor in a manager position eligible to train for the two manager positions that will need to be filled.

3. Given the large amount of positions that need to be filled, we advise that they expand the mentorship eligbility criteria to include those born outside of 1965.
