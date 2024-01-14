# Extract, Transform, and Load Project

## Background
A fictional company has asked me to better organize their crowdfunding data. This company kept their data in one excel workbook, but the company wants the data to be loaded into a SQL database to make the data handling process more efficient and organized. To do this, I had to separate the data into four separate dataframes with relational connection to each other. These four dataframes will be separate tables in the SQL database, and their relationships with each other are illustrated in the entity-relationship diagram. I have been tasked with extracting the data from a company's csv file into a jupytern notebook, cleaning it, separating the data into four dataframes using python, and then loading the four dataframes into a SQL database. 

## Extract, Transform, and Load (ETL) Process

To accomplish our goal of loading the excel workbook into a SQL database, we have to separate the data into four distinct dataframes. We will do this in a jupyter notebook using python.

First, I extracted the raw excel workbook and put it into an pandas dataframe.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/89d56eea-527c-4c3d-bc09-75a1df8b2af8)

**Figure 1.** *A snapshot of the raw data from the excel workbook in a pandas dataframe. Full table is in the jupyter file in the main branch of this repository*


After I put the raw data into a pandas dataframe, I created a 'Category' dataframe that contains:

* A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories

* A "category" column that contains only the category titles

I accomplished this by splitting the categories and subcategories into separate columns in the dataframe. Then, I created a list of all of the unique categories in the database and assigned them to a category number based on how many categories there were in the database.

This dataframe was loaded into the SQL database as a table named 'Category.'

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/b686ef39-2b70-4ed8-9828-990da47ec079)

**Figure 2.** *Category dataframe.*


Second, I extracted and trasnformed the 'crowdfunding.xlsx' excel file to create a campaign dataframe to have the following columns:

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

This will be our first dataframe and will be uploaded into the table named 'Campaign' in the SQL database.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/5f658439-d8de-4a3f-bdcd-c14bb6d4afe9)

**Figure 3.** *A screenshot of finished dataframe including a few of the columns.*
