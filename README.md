# Data-Cleaning-in-Excel
## Inroduction
Data cleaning is a critical first step in the data analysis process. It involves identifying and correcting errors, inconsistencies, and inaccuracies within a dataset to ensure the quality and reliability of insights drawn from it. Common tasks include handling missing values, removing duplicates, fixing formatting issues, standardizing categories, and correcting data types. A clean dataset not only improves the accuracy of analysis but also lays the foundation for effective visualizations, modeling, and business decision-making. Below are some of the steps I took in making sure the "Employee" Dataset is ready for analysis.
## Cleaning the “EMPLOYEE UNCLEAN” Dataset
On getting the data, I loaded it into excel and looked through the data to gain some understanding of each column in the dataset. After which, I then converted the data to a table and then checked for duplicates for which there were none. I then loaded the data into Power Query and performed the following data cleaning process:
1.	Firstly, I checked to see if the data types for each column is correct and I changed the “Date employed” and “Date of birth” columns to date data type. I removed the empty cells the “Name” column 
2.	Some columns had empty cells so I went on to fill them. I decided to fill up the empty cells in these columns because, the columns “StaffID” and “Name” were unique to each employee. So, a missing value in some of these columns could just be as a result of improper data entry.  Some of these columns were:
- The “Salary” column which I was able to replace its empty columns with 0 since it is a whole number data type column
- The “Gender” column also had nulls which I replaced with “Other”. So, there are three groupings in the “Gender” column namely: Female, Male, Other.
- The “Department” column also had some null which I replaced with “Not Specified”
-	The “Location” column also had some empty cells which I replaced with “Not Known”
3.	After checking the missing data column, I then went on to check for misspellings. The “Gender” column had different misspellings like fem#le, female, etc. for the female and malee, etc. for male. All of which were replaced with the appropriate gender spellings – “Female” and “Male” respectively.  The “Location” column also had some misspellings such as such as Ogu n, Abuuja, Lag0s, etc. all of which was replaced with their appropriate spellings. I then Load and close to Excel.
4.	In Excel, I calculated the age of each employee by first inserting two new cells one of which was used to write the function for today’s date `(=TODAY ())` and then populated the other cells with it. Then I subtracted the “Date of Birth” of the employees from the previously written today’s date in a new column which returns a date. I then went on to change the date to a number format and divided by 365 days which then gives us the age of each employee. Rounded down the column to be left with whole numbers and then renamed the column as “Age”. Then I went on to copy and paste as values in other to avoid referencing error. 
5.	Now that I have the age column, I went on to group them using Nested IF Function. First, I found out the minimum and maximum age using the functions: ```=MIN(J2:J1311) AND =MAX(J2:J1311)```. After getting a minimum age of 25 and maximum age of 55 I then went on to write my IF Function as thus: 

 ``` =IF([@Age]<=45, "Adults (36 - 45)", IF([@Age]<=35, "Young Adults (25 - 35)", "Middle Age (46 - 55)"))```

With an interval of 10, I was able to group the column “Age” as the following:
- 	25 – 35 – Young Adult
- 	36 – 45 – Adults 
-  46 – 55 – Middle Age
6.	I then took a second look at my data and decided that I needed to split up the “Date Employed” column for possible analysis. Which prompted me to load the data back into Power Query and then used the “split column” with a “/” delimiter to split up the column into “Month Employed”, “Day Employed” and “Year Employed” respectively. I then close and load back to excel.
7.	Using VLOOKUP, I inserted the month name into the “Month (Text)” column using the “Month Employed” column. Writing my VLOOKUP function as thus:
    ``` =VLOOKUP([@[Month Employed]],Sheet1!$A$1:$B$13,2,0)```

