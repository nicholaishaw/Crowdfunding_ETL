# Extract, Transform, and Load Using Python and SQL

## Background
For this project, I have been tasked with organizing a company's crowdfunding data—an old Excel file consisting of 1,000 companies and the key details of their crowdfunding events. To tackle this, I chose to migrate the data to a SQL database. To ensure proper organization within the database, I separated the crowdfunding data into four separate tables. The tables included the 'Category' table, a list of every unique campaign category; the 'Subcategory' table, a list of each unique subcategory in the dataframe; the 'Campaign' table, containing crucial campaign details such as IDs, company names, goals, outcomes, and dates; and finally, the 'Contacts' table, which held information for each crowdfunding organization. Once the data was organized, I created and assigned a primary key to each table.

Using Python scripts, I first imported the raw Excel file into a pandas dataframe, then split the data into four pandas dataframes—each representing one of the SQL tables. I then used Python code to create and assign primary keys for each table before finally exporting the data to csv files. Once the csv files were created, I loaded it into the SQL database and created an entity-relationship diagram to illustrate the relationships between the tables. 

## Extract, Transform, and Load (ETL) Process
### Raw Dataset:
First, I extracted the raw Excel workbook (crowdfunding.xlsx) and put it into a pandas dataframe.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/89d56eea-527c-4c3d-bc09-75a1df8b2af8)

**Figure 1.** *A snapshot of the raw data from the excel workbook in a pandas dataframe. Full table is in the notebook in the main branch of this repository*

### Category and Subcategory Tables:
Following the import of the raw data into a pandas dataframe, I proceeded to create the 'Category' and 'Subcategory' dataframes. This involved extracting category and subcategory data from the raw dataframe into new ones, which includes:

**Category Dataframe:**
* A "category_id" column that is numbered sequential form 1 to the length of the number of unique categories. *This is a necessary step as it will be the primary key when uploaded to the SQL database.*

* A "category" column, a list of the categories.

**Subcategory Dataframe:**
* A "subcategory_id" column that is numbered sequential form 1 to the length of the number of unique subcategories. *This is a necessary step as it will be the primary key when uploaded to the SQL database.*
  
* A "subcategory" column, a list of the subcategories.

I accomplished this by splitting the categories and subcategories into separate columns in the dataframe. Then, I retrieved each unique crowfunding category and subcategory from the raw dataset and stored them in distinct lists. Lastly, I used a list comprehension to loop through the cateogry and subcategory lists and assign them a unique id number.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/b686ef39-2b70-4ed8-9828-990da47ec079)

**Figure 2.** *Category dataframe.*

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/1962ed0d-a59f-44a7-a68a-f4c5f638eabc)

**Figure 3.** *Subcategory dataframe.*

### Campaign Table:
Next, I used Python scripts to retrieve and transform data from the original raw dataframe to form a campaign dataframe. The campaign dataframe possessed the following columns

* The "cf_id" column. ***This will be the primary key when uploaded to the SQL database.***

* The "contact_id" column. ***This is a foreign key from the contacts dataframe.***

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

* The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category dataframe. ***This is a foreign key from the category dataframe.***

* The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory dataframe. ***This is a foreign key from the subcategory dataframe.***

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/5f658439-d8de-4a3f-bdcd-c14bb6d4afe9)

**Figure 4.** *A screenshot of finished dataframe including a few of the columns.*
___
### Contacts Table:
Finally, I created a 'contacts' dataframe by extracting the contact information of each crowdfunding event from the company's contact excel file. This included the first name, last name, email, phone number, and contact id. I put the data in a pandas dataframe and transformed the columns to correct formatting. Since the raw excel file contained the contact id, contact name, and email in a single column, I iterated through the contact information and separated them so that the contacts dataframe could include the following columns:  

* A column named "contact_id" that contains the unique number of the contact person. *This will be the primary key when uploaded to the SQL database.*
* A column named "first_name" that contains the first name of the contact person.
* A column named "last_name" that contains the first name of the contact person.
* A column named "email" that contains the email address of the contact person

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/66c2427f-618e-4f9f-afcf-3a1d72d70aaf)

**Figure 5.** *Contacts dataframe.*
___
### SQL Upload
After the four dataframes were created (category, subcategory, campaign, contacts), they were exctracted into csv files and loaded into the SQL database as separate tables. I engineer a schema of the database and created an ERD to illustrate the relationship between the tables.

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/9da2807e-b49e-476d-a5d6-1993567c81f7)

**Figure 6.** *Entity-relationship diagram of the SQL database.*

![image](https://github.com/nicholaishaw/Crowdfunding_ETL/assets/135463220/6c60c271-a192-4edd-9e06-d22287e9b6ab)

**Figure 7.** *Database schema.*
