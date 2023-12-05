# Extract, Transform, and Load Project

## Background

In an effort to better organize crowdfunding data for a fictional company, I have been tasked with extracting the data from a company's csv file, cleaning the data, and loading it into a SQL database. Using python, I extracted the csv file into a pandas dataframe, transformed and cleaned the data for SQL readability using python functions, and loaded it into a SQL database.

## Extract, Transform, and Load (ETL)

First, we needed to extract and trasnform the 'crowdfunding.xlsx' excel file to create a dataframe to have the following columns:

* The "cf_id" column

* The "contact_id" column

* The "company_name" column

* The "blurb" column, renamed to "description"

* The "goal" column, converted to the float data type

* The "pledged" column, converted to the float data type

* The "outcome" column

* The "backers_count" column

* The "country" column

* The "currency" column

* The "launched_at" column, renamed to "launch_date" and with the UTC times converted to the datetime format

* The "deadline" column, renamed to "end_date" and with the UTC times converted to the datetime format

* The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category DataFrame

* The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/5f658439-d8de-4a3f-bdcd-c14bb6d4afe9)

**Figure 1.** *The finished dataframe 
