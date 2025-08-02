# codes-gcp
This repository is for step by step practise of Google Cloud Platform. There are not many resources relatd to GCP practise other than Original Documentations. The purpose of this repository is to provide step by step guide to practise GCP products for data engineers.

Topics covered in this repository are:
1. Fundamental of Data engineering
2. Some intro to big data capabilities of GCP
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

1. Fundamentals of Data Engineering
80% of time people in data industry spend on collecting, cleaning and transforming the data. Data Engineering help us to automate most of these processes using various technologies. GCP is one of the platforms where we can do these processes in one place using various products. These products integrate with each other seamlessly.

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

Knowledge Check:
1. What is ETL?
2. What is difference in ETL and ELT?
3. What is Map Reduce?
4. What is main role of data engineer?