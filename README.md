# Extract, Transform, and Load Using Python and SQL

## Background
For this project, I have been tasked with organizing a company's crowdfunding data—an old Excel file consisting of 1,000 companies and the key details of their crowdfunding events. To tackle this, I chose to migrate the data to a SQL database. To ensure proper organization within the database, I separated the crowdfunding data into four separate tables. The tables included the 'Category' table, a list of every unique campaign category; the 'Subcategory' table, a list of each unique subcategory in the dataframe; the 'Campaign' table, containing crucial campaign details such as IDs, company names, goals, outcomes, and dates; and finally, the 'Contacts' table, which held information for each crowdfunding organization. Once the data was organized, I created and assigned a primary key to each table.

Using Python scripts, I first imported the raw Excel file into a pandas dataframe, then split the data into four pandas dataframes—each representing one of the SQL tables. I then used Python code to create and assign primary keys for each table before finally exporting the data to csv files. Once the csv files were created, I loaded it into the SQL database and created an entity-relationship diagram to illustrate the relationships between the tables. 

## Extract, Transform, and Load (ETL) Process

To accomplish our goal of loading the excel data into a SQL database, I had to separate the data into four distinct dataframes that will later be loaded as individual tables in SQL. I performed this in a jupyter notebook using python.

First, I extracted the raw excel workbook (crowdfunding.xlsx) and put it into an pandas dataframe.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/89d56eea-527c-4c3d-bc09-75a1df8b2af8)

**Figure 1.** *A snapshot of the raw data from the excel workbook in a pandas dataframe. Full table is in the jupyter file in the main branch of this repository*
___

After I put the raw data into a pandas dataframe, I created a 'Category' dataframe that contains:

* A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories (this is necessary since the category id will be the primary key for this table in the SQL database.

* A "category" column that contains only the category titles

I accomplished this by splitting the categories and subcategories into separate columns in the dataframe. Then, I created a list of all of the unique categories in the database and assigned them to a category number based on how many categories there were in the database.

This dataframe was loaded into the SQL database as a table named 'Category.'

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/b686ef39-2b70-4ed8-9828-990da47ec079)

**Figure 2.** *Category dataframe.*
___
The same process was done with subcategories. The subcategories were extracted and a dataframe was created with the subcategory name and a aubcategory id. The subcategory id will be later used as the primary key in SQL.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/1962ed0d-a59f-44a7-a68a-f4c5f638eabc)

**Figure 3.** *Subcategory dataframe.*
___

Next, I used the company's database to create a campaign dataframe to have the following columns:

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

This will be our first dataframe and will be uploaded into the table named 'Campaign' in the SQL database. The 'cf_id' will later be used as the primary key when uploaded to SQL.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/5f658439-d8de-4a3f-bdcd-c14bb6d4afe9)

**Figure 4.** *A screenshot of finished dataframe including a few of the columns.*
___

Finally, I created a contacts dataframe to contain the contact information for each crowdfunding organization. I included the first name, last name, email, phone number, and contact id. This dataframe will be loaded into the SQL database as 'Contacts.' The contact id will later be used as the primary key when loaded to SQL.
I created this dataframe by extracting the contact information from the raw data and splitting the information into separate columns (i.e., first name, last name, email, and phone number).

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/66c2427f-618e-4f9f-afcf-3a1d72d70aaf)

**Figure 5.** *Contacts dataframe.*
___

After the four dataframes were created (category, subcategory, campaign, contacts), they were exctracted into excel workbooks and loaded into the SQL database as separate tables. A schema of the database and an ERD was created to illustrate the relationship between the tables.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/9da2807e-b49e-476d-a5d6-1993567c81f7)

**Figure 6.** *Entity-relationship diagram of the SQL database.*

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/6c60c271-a192-4edd-9e06-d22287e9b6ab)

**Figure 7.** *Database schema.*
