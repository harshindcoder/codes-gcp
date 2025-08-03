# codes-gcp

This repository is for step by step practise of Google Cloud Platform. There are not many resources relatd to GCP practise other than Original Documentations. The purpose of this repository is to provide step by step guide to practise GCP products for data engineers.

Topics covered in this repository are:
1. Fundamental of Data engineering : [Link](#1-fundamentals-of-data-engineering)
2. Some intro to big data capabilities of GCP : [Link](#2-big-data-capabilities-of-gcp)
3. Data warehouse in BigQuery
4. Orchestration for Batch Data loading Using Cloud Composer
5. Data Lake using Dataproc
6. Processing Streaming Data with Pub/Sub and Dataflow
7. Visualizing data using Data Studio
8. Machine Learning on GCP
9. User and Project Management on GCP
10. Cost Calculation and Strategy in GCP
11. CI/CD on GCP
12. Other Data Engineering Resources for GCP 

# 1. Fundamentals of Data Engineering
80% of time people in data industry spend on collecting, cleaning and transforming the data. 
Data Engineering help us to automate most of these processes using various technologies. GCP is one of the platforms where we can do these processes in one place using various products. These products integrate with each other seamlessly.

Data Architecture is the most crucial part of data ecosystem.

Data Life cycle:
Most of the challenges in data engineering is related to moving data from one place to another. The difference is only about how and newer technologies. Data is often present is different sources of company on different systems. These systems are called data silos we as data engineers generally need to gather all these data in our data cycle to one place for decision making using data.

The place of gathered data is generally called Data Warehouse and Data Lake. The difference in both is that Data Warehouse is monolithic structure where everything from storage, compute, schema and SQL interface are handled as one interface and they generally handle structured data. Data lakes are modular in a way that different part can be handled by different tool so they can also handle unstructured data.

Data is very much like a water. It goes from upstream to low stream in systems. Some times we just need to transfer data from one system to another or in more complex scenarios we may need to filter, join, and split multiple steps downstream before the data can be consumed by the end users.

Data life cycle mostly starts from frontend applications and flows up to the end for data users as information in the dashboard or ad hoc queries.

(Insert Fig of Data Life Cycle Diagram.)

So in the end data engineer is someone who designs and builds data pipelines.

In the end I want to point out about three things which every data engineers need to know. I advise you to look on the internet about what they are and where they are use.
1. ETL
2. ELT
3. Map Reduce
4. Big Data

## Knowledge Check:
1. What is ETL?
2. What is difference in ETL and ELT?
3. What is Map Reduce?
4. What is main role of data engineer?

## Resources:
Any contribution from readers is welcomed.

# 2 Big Data Capabilities of GCP

> GCP is like a supermarket. Same things have many varieties. For cleaning, transformation and other uses what product you use will change the way your final pipeline will work. So choose your tools properly.

In this section we will start using GCP console, Cloud Shell, and Cloud Editor.

We will be using GCP free tier for this course or if you already using GCP you can also use your active account as the exercises we will do in this repository are cheap in terms of price to pay if any needed to pay.

> GCP will require first time payment of 1000 Rs in India or other in other countries as of 2 Aug 2025. It is returned if you do not continue using GCP after free tier period. For proper guidance look at GCP free tier policies.

## Understanding cloud

Renting someone else's server is in short what cloud is. As long as you are not using own machine you are using cloud.

For data engineers it is using services, APIs, and trusting the others machines for building there data products on.

## Getting started with GCP

1. Access the GCP console from this [Link](http://console.cloud.google.com/) from any browser.

2. Log in with you google/gmail account.

3. Register for free tier from the given options.

Many people have fear of need to pay for GCP uses.
You will mostly no need to pay until your free tier credits are used up or the time limit exceed. But there may be certain services which may require us to pay. But we will try to keep these costs as low as possible. If you are using free tier then these costs will be deducted from your free tier credits. So follow the process and you may not need to pay.

## GCP console
After registration we will be directed to GCP console. GCP centralize every interaction of user in this single console.

GCP console have everything you will need to do from user configuration, monitoring bills, checking logs, and much more.

1. Start by clicking on Navigation menu (the hamburger or three dashes button) at the top left
of your screen.  
2. You can see products such as BigQuery, Cloud Storage etc. here.
3. Pin all the services we will be required in our course for now pin BigQuery which you can see for other things go to all products and pin them when we use them so they will be visible in top of the navigation bar in pinned section.

## Creating first GCP project
Steps to create a project:
1. On top bar you see **My First Project**. This is your project name. We want to change this default one to a new one. So click on it. We will call this button project menu from now on.
2. After coming in project menu. Click on **NEW PROJECT** at the top right.
3. After that you will need to fill a form with the project detail. Add new project name in the form. There are two pieces of project information in GCP.
Project name: user friendly name - does not need to be unique.
Project ID: Need to be unique globally.

Both can be same as long as second one is unique.

For example :

Project Name: [yourname]-codes-gcp
Project ID: [yourname]-codes-gcp
Both can be same since above will most probably be same unless two of you who use this repository are same try to use 1,2 .. after you name to check whether you are first one to use this repository or second one..

4. Click **CREATE**

5. After creating your project, click on Project menu again and follow these steps:
A. Search for you created project.
B. Click your project name from the list.

this way you will work on your own project, not the default **My First Project**.

## GCP Cloud Shell

You can access Linux terminal in the GCP console. This is a standard Linux environment preinstalled with all necessary libraries.

Lets use it:
1. Open the terminal by clicking on top right button in the  GCP console. You can check it by hovering your coursor over buttons in right.

2. Wait for a few second to let it start.

3. Still in the terminal, if you check the bar, you will see the **Open Editor** Button. Click on it.

4. terminal will change into text editor. Editor is not proper IDE but it will be usefull in minor corrections in code.

Lets warmup by creating Hello GCP python script:
1. Go to File | New File and then name the file **hello_gcp.py**.

2. In editor write the following command.
```
print("Hello GCP, I am using you for a first time.")
```
The editor will automatically save your file.
3.Lets run python script from terminal by clicking **Open Terminal** button and run the following Python command:
```
#python hello_gcp.py
```
The terminal will print your text out.

So until now we setup our project. Try to run our first script in our project. 

## GCP servies for data engineers

We seen that GCP Console navigation bar contained lots of services in GCP. The services you will generally use in company are predecided during creating the data architecture on GCP. Data engineers are also involved in this process.

There are five groups of services in GCP:
1. VM-based : You have machine with OS online to setup everything yourself.
2. Managed Services : Google Manage software for you. OS + software (E.g. Hadoop on GCP is to use Dataproc).
3. Serverless (fully managed services) : Just Start using no need to consider anythin about machine type etc. (E.g. Bigquery).

I want to divide GCP products into three categories:
1. Big Data 

List of services under big data:
1. Bigquery
2. Dataproc
3. Dataflow
4. Pub/Sub

We will use them but please try to know more about these products on youtube or google.

2. Storage and DB:

List of services:

1. Cloud Storage
2. Bigtable
3. Dataflow
4. Pub/Sub

These are for storage and data tranfer.

3. ETL Orchestrator

List of services:

 1. Cloud composer
 2. Data Fusion
 3. Dataprep

These are for automation and orchestration.

4. Identity and management tools

List of services:

1. IAM & Admin
2. Logging
3. Monnitoring 
4. Data Catalog

for supervision.

5. MI and BL
List of services:

1. Vertex AI
2. Looker
3. Data Studio

Other than about services we need to know about types of accounts on GCP.

We need to know there are two type of accounts on GCP.

User Account : Is our personal account as human users.
Service Account : Which is used by non-human.

For Example : Company want to run some pipelines without employees involvment for very sensitive data then they will use service account.

## Knowledge Check:
1. What is GCP console?
2. How to create a new project?
3. How to work in new project?
4. How to work with Cloud console and Cloud Editor?
5. Different Cloud services use by data engineers and there types.
6. Types of account on GCP.

# Data Warehouse in BigQuery
Data Warehouse is usually single source of truth where as discussed before various data silos combine.

In this section we will be using BigQuery, Google Cloud Storage (GCS) and Cloud SQL.

Try to open BigQuery and GCS services on your console in your project and enable the APIs. There will be automatic notification for enabling APIs if you have never enabled them.

Try to remember what is Google Console, Cloud Shell and Cloud Editor and use them just to become familiar with them.

Before going forward you should have basic knowledge of Python, SLQ, Linux commands, and Git.

### Assignment if you do not know above things.
1. Python - I will add later
2. SQL - I will add later
3. Git - I will add later
4. Linux Commands -  I will add later

>Use python3 in cloud shell when running later codes not python.

## Intro to Google Cloud Storage and BigQuery

GCS is object storage. It's a fully managed service by GCP.

Object Storage is a highly scalable data storage architecture that can store very large amounts of data in any format.

We will be using GCS as dump storage from databases, for exporting historical data from BigQuery, for storing machine learning model files, and for any other purposes related to storing files.

BigQuery is fully managed data warehouse in the cloud. It allow us to store and anlayze data immediately without thinking about infrastructure.

BigQuery allows you to insert streaming data. BigQuery allows you to perform machine learning using BigQuery SQL directly in the console at scale. This is very useful for organizations that require quick access to machine learning capabilities.

## BigQuery Console

We will learn BigQuery by doing so follow me:
1. Open GCP console and choose **BigQuery** from navigation bar. Then we will come to BigQuery main page also called BigQuery Console.

2. Familiarize with names of the buttons and panels. Then go to the Explorer panel in left.

3. We can see our project name under **Explorer** as a default.
In the center panel is query element. we will write query in here and run it either using the **RUN** button or using keyboard shortcuts.

4. Try our hell_bigquery by typing in the editor of **Untitled query** in the center panel.
Type
```
SELECT "Hello BigQuery";
```
Then click on the **RUN** button.

5. The result of the query will ve shown at the bottom as tables and there will also be some other things like Job History etc. Explore them on your own.

### Creating dataset in BigQuery

Dataset meaning creating data tables in BigQuery. We should always try to think from the business perspective when creating datasets in the bigquery. Always try to give you datasets a meaninful name rather thane table1, table2 etc.

Now follow these steps to create a dataset in BigQuery:
1. In Explorer you can see three dots in right of your project name. Click on it. It is also called action button.
2. Click on create dataset button.
3. Choose a name for the dataset. Any name will do.
4. Choose the data location. Choose any for now.
5. Set everything else as default for now and click **CREATE DATASET**.

You can see your dataset under the project name in **Explorer** panel.

### CSV file into BigQuery Table
Simplest way to load data in Bigquery is to use BigQuery console.

To do that click on action button(three dots vertically) next to your created dataset. Be careful do not select action button next to your project name.

You can find **CREATE TABLE** button in top right corner of the screen. Create table by completing the form as per the following details:

Create table from : Upload
Select file: Find any CSV file that you have. (Note keep it very small otherwise it can go beyond free tier. If possible keep in KBs.)

Table name : Any name

Schema : Click **Auto detect** checkbox.

After completing steps, you can see your table under the dataset. They you can see table using **SELECT** statement or choose **PREVIEW** after clicking table name in **Explorer**.

Write Some SQl queries on the table you created and try to check if it is working.

Now delete this table and dataset after completing the above activities to stop wasting space for now.

#### Data types in BigQuery
Check out datatypes used in BigQuery [here](https://cloud.google.com/bigquery/docs/reference/standard-sql/data-types).

Now lets talk about timestamp data in BigQuery. BigQuery only support UTC format to make the timestamp consist all around the world.

So upto know we created dataset in BigQuery then added table to dataset. We added CSV file to our table and also learned about data formats and restrictions in BigQuery.

## Preparing before developing our data warehouse

Step 1 : Access your Cloud Shell

Step 2 : Check the curret setup using the command line

type in Cloud Shell
```
#gcloud info
```
click **authorize** if prompted.

We want to check the account and project. Make sure it's you email and the project you created.

Account : [your email]
Project : [your project]

Step 3 : After checking the environment we want to configure a new environment using the gcloud init command. In cloud shell run the following command:
```
gcloud init
```

Choose option:
```
[2] Create a new configuration
```

then give this configuration a name, for example, **personal-config**. Choose the option to use your existing email.
```
[1] your email
```

Lastly choose you project number:
```
[number] project name.
```
The last option to configuring the default region and zone. Just choose n(no). This option may not require based on when you are using shell to run the commands.

Step 4 : The final prerequisite is to download the example code and dataset from this repository. We will use codes and data from this repository only.

Step 5 : Upload data to GCS from Git. There are three steps:
1. Create a GCS bucket.
2. Enter the bucket information.
3. Upload a local file to the GCS bucket using **Upload** option.

1. Create a GCS Bucket
Go to **Navigation** menu and choose Cloud Storage. Click the **CREATE BUCKET** button.

2. Enter the bucket information.
Fill in the bucket name [your own project name]-data-bucket.

Bucket name should be unique globally. So using our project name as prefix is way to ensure uniqueness.

Choose **Default** for location.

3. Upload data folder in our repository on bucket.

## Practising developing a data warehouse

We will discuss different scenarios.

Scenario 1:
We have data in CloudSQL-MySQL database we want to do some queries on it and download the result as CSV files.

Steps and planning for scenario 1:
Planning : 
1. Create MySQL Database 
2. Extract MySQL to GCS 
3. Load GCS to BigQuery
4. Create BigQuery Data Mart

Step 1 : Create a MySQL database in CloudSQL

This step is not part of building data warehouse. But to simulate table extraction from application databases to GCS, this will be very helpful.

1. Create a CloudSQL instance
2. Connect to the MySQL instance
3. Create a MySQL database
4. Create a table in the MySQL database
5. Import CSV data into the MySQL database

###Create a CloudSQL instance
You can do it by using Navigation section but for simplicity we will run it using the gcloud command in Cloud Shell.
Run this command in cloud shell:
```
gcloud sql instances create mysql-instance-source \
--database-version=MYSQL_5_7 \
--tier=db-g1-small \
--region=us-central1 \
--root-password=codesgcp123 \
--availability-type=zonal \
--storage-size=10GB \
--storage-type=HDD
```
>Warning : It is going to cost us. Do not forget to delete the instance after this practice exerice. It cost hourly so do not leave it running.

Wait for around 5 minutes it take some time. Refresh after the process is complete and go to Cloud SQL homepage and you will see that your MySQL instance is ready.

### Connect to the MySQL instance
Run this command in cloud shell
```
gcloud sql connect mysql-instance-source --user=root
```
Password is as given is above command before. Now you will see MySQL shell.

### Create a MySQL database
Lets create MySQL database named ```apps_db```.

Run this script in MySQL shell:
```
CREATE DATABASE apps_db;
```
Check database is created using this command:
```
SHOW DATABASES;
```

### Creating a table in the MySQL database
While in mysql shell, we need to create the table using a Data Definition Language (DDL) statement.

Create table by running following DDL:
```
CREATE TABLE apps_db.stations(
    station_id varchar(255),
    name varchar(255),
    region_id varchar(10),
    capacity integer
);
```
this will create a table station in apps_db database.

### Import CSV data into the MySQL database
Do not close the cloud shell.

To upload the data, go to the Cloud SQL console:
1. Click the created mysql-instance source, and then find and click the **Import** button.
2. Choose the name of data file in our GCS bucket-name/file-name:
gs://[your project name]-data-bucket/data/dataset/stations/stations.csv
3. Change the File format option to CSV.
4. Input the destination database,apps_db, and the table name, stations.
5. Once everything is complete, click the **Import** button.
6. Now we will return to Cloud Shell and try to access the stations table. In the MySQL shell, run the following query:
```
SELECT * FROM apps_db.stations LIMIT 10;
```
Make sure you saw some data.
Exit from MySQL shell by typing 
```
exit
``` 

### Extract data from MySQL to GCS
First of all, we need to handle Identity and Access Management (IAM). We need to assign the CloudSQL service account a Storage Object admin role first. This step will be a little bit confusing if you are new to IAM, but it's good starting point for understanding IAM without going into too much depth.

Find service account for your mysql-instance-source by clicking on it in CloudSQL console and scrolling down.

It will be in this format:
[any text] @gcp-sa-cloud.sql.iam.gserviceaccount.com.

Copy the service account as we want to add IAM role to it.

Follow these steps:
1. go to navigation bar
2. Choose IAM & Admin -> IAM
3. Click +Add
4. Paste the CloudSQL service account into New principals.
5. then select a role
Type gcs object and you will be able to  choose Storage Object Admin (not Storage Admin).

After finishing process. Your CloudSQL service account will have permission to write and delete file objects in all GCS buckets in you project.

Next we want to load the data.

We will load data by using the shell script from our git repository code section.

The file name is  gcloud_export_cloudsql_to_gcs.sh.

Change the bucket name to yours and read it carefully using gcloud editor which we learned in start. Before that load this file on our cloud editor by copy paste in cloud editor and save with the same name as ours. If you type ls and enter in terminal  after this you will see that file is saved.
After changing bucket name come to cloud shell and run the script by running this command:
```
sh gcloud_export_cloudsql_to_gcs.sh
```
This script will export data to GCS from mysql instance. In real world scenario we extract data from on of the clone instance. Application databases usually have a clone instance for providing high availability. Hence it is good to extract data from there. 

So, finally we have done E in ETL process, which is to Extract data from a data source into a GCS bucket.

We have done what we want to do with MySQL instance so we can delete it now.
You can delete the MySQL instance by running the following command:
```
gcloud sql instances delete mysql-instance-source
```
Check CloudSQL home page to ensure that the instance is deleted.

