# codes-gcp

This repository is for step by step practise of Google Cloud Platform. There are not many resources relatd to GCP practise other than Original Documentations. The purpose of this repository is to provide step by step guide to practise GCP products for data engineers.

Topics covered in this repository are:
1. Fundamental of Data engineering : [Link](#1-fundamentals-of-data-engineering)
2. Some intro to big data capabilities of GCP : 
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










