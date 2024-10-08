# AWS-Part1-Venkat

___

# Project Description: 311 Service Requests of City of Vancouver
This is my documentation of the design & implementatio of City of Vancouver Data Analytical Platform by using the free [Source](https://opendata.vancouver.ca/explore/dataset/3-1-1-service-requests/information/?disjunctive.department&disjunctive.service_request_type&disjunctive.status&disjunctive.closure_reason&disjunctive.local_area&disjunctive.channel) datasets available in the Open Data portal website of segment 3-1-1 service requests. This project concentrates on details of designing and implementing DAP in detail.

## Project Title: DAP Design & Implementation for 311 Contact Center of City of Vancouver
* Customer initiated service requests received by 3-1-1 Contact Centre from 2022-2024.
* Service requests refer only to those call types that generate a requ​​es​​t to a City of Vancouver department to provide service.
* The City of Vancouver is increasingly leveraging data to improve its operations and services to citizens.
* This document outlines the implementation of an AWS Data Analytic Platform (DAP) designed to address the city's needs in 3-1-1 service request analysis.
* The DAP offers a secure, scalable, and cost-effective solution for data management, processing, and analysis, empowering city officials to make data-driven decisions for the benefit of Vancouver residents.
## Project Objective:
* To design and implement DAP for City of vancouver's 3-1-1 Service Requests..
## Datasets
* The Dataset used is taken from [City of Vancouver Open Data Portal](https://opendata.vancouver.ca/explore/dataset/3-1-1-service-requests/information/?disjunctive.department&disjunctive.service_request_type&disjunctive.status&disjunctive.closure_reason&disjunctive.local_area&disjunctive.channel) for the category of "3-1-1 Service Request metrics"<br>
[cumulative_3-1-1-service-requests_2023_open.xlsx](https://github.com/user-attachments/files/17021197/cumulative_3-1-1-service-requests_2023_open.xlsx)
* This dataset contains location information such as address or intersection where service was requested and the local area corresponding to the case (incident) location.
## Methodology:
* The process involves different steps explained in detail below:
### Step1: Data Analytical Question Formulation
* In this dataset I will be using the 3-1-1 Service Requests services. The main metric we will be suing here will be about “What is the count of service request for each type of requests respectively.” I felt after having a business established next comes the part where we can utilise various services available from the City of Vancouver for its residents. I felt we can understand this from the information of 3-1-1 Service requests. 
### Step2: Data Discovery
* After the identification of analytical questions above, the next step was the identification of data. Having a virtually developed data structure of metrics and columns we can use from dataset we can proceed.
* It was important to understand these fields to be able to design the succeeding data processing and analysis workflows.
* I have selected the information of “3-1-1 Service Requests” from (City of Vancouver, n.d) portal.
### Step3: Data Storage Design
* In this part we will mainly be discussing on storage. The storage design for the application is raw data storage, Amazon S3, structured data, and Amazon Redshift. This way, the data is retained at scale, and retrieval is very efficient.
* The calls data od 3-1-1 Service Requests as mentioned above are stored in a separate table so that historical data does not get updated and modified and is easily accessible for comparisons.
### Step4: Data Preparation
* In this the data collected in raw format is then preprocessed to make it less erroneous and more standard. 
* This step is essential to ensure the data will be clean and ready to offer good information during the analysis.
* Similarly other metrics were used in the rest of the datasets.
### Step5: Data Ingestion
* In this, raw data is in the form of call logs extracted from the city's 3-1-1 service requests records and loaded to Amazon S3 using AWS Data Pipeline.
* This configuration permits daily updating of current year data and ensures that the medium provides the most recent calls data.
* It's set up to allow for regular bulk updates and live ingesting for real-time analytical purposes.
### Step6: Data Storage
* In this the processed raw datasets are stored in Amazon S3/Redshift, making the processed data available for analysis.
* The data storage phase also has data security measures, such as encryption, to prevent unauthorized access to the data by any unauthorized personnel.<br>
![figure 10](https://github.com/user-attachments/assets/cd60eb27-1b2f-41e1-a117-22f21720db68)
* The above image display the details of “storage” for “Dataset 3” using ‘AWS-S3’.<br>
![figure 11](https://github.com/user-attachments/assets/fa6e7ead-1def-4962-85c7-761b02855c0e)
* The above image display the details of “storage” for “Dataset 3” using ‘AWS-S3’.
### Step7: Data Pipeline Design
* In this an AWS Glue/Step Functions data pipeline is created for the movement of data, which means that data can be processed automatically.
* All the processes, starting from the intake of data, processing it, storing it, and eventually analyzing it, are planned and in place to facilitate the movement of data and its subsequent processing.<br>
![appx003](https://github.com/user-attachments/assets/2dab7de3-fba9-497e-8554-f90a176ce0ee)
* The above image shows the data pipeline of 3-1-1 service requests details.
### Step8 & 9:	Data Cleaning & Structuring
* In Cleaning preliminary cleaning of the data was explained as crucial for the desired quality of the data set.
* This consists of removing such records as duplicates, methods utilized to eliminate data entry errors, and gaps in the values.
* The data must be adequately cleaned so that correct analysis and correct decisions can be made.
* In Structuring the collecting data is arranged in a rather formal format, which can be easily filtered and analysed.
* This is done to sort the data into tables or partitions, all in an attempt to have the key attributes of the database organized appropriately to enhance quick and accurate data retrieval.<br>
![figure 24](https://github.com/user-attachments/assets/ed227826-5c2d-4cb2-a8fe-62628c6bfcf4)
* The above image display the details of “Schema Information” for “All Request Dataset” using ‘AWS-DataBrew’.<br>
![figure 25](https://github.com/user-attachments/assets/ec401357-24b8-4a22-8ed0-71cb27bf5085)
* The above image display the details of “Schema Information” for “Open Requests Dataset” using ‘AWS-DataBrew’.
### Step10: Data Pipeline Implementation
* In this the data pipeline is the pipeline configuration for Data as explained above: This includes checking on the status of jobs and eliminating any issue that may occur during the job process. It also ensures that the data offered is well-processed and available for implementation promptly.<br>
![figure 30](https://github.com/user-attachments/assets/78560fb8-85e6-4aaf-b2f8-3a24e773f82c)
* The above image display the details of “ETL information” for “All Request Dataset” using ‘AWS-Glue’.
### Step11:	Data Analysis
* In this Data analysis is done, and to make queries such as those in the analytical question above, one can use Amazon Athena or QuickSight.<br>
![figure 34](https://github.com/user-attachments/assets/a61de548-95f1-4cd4-b157-a405917e771d)
* The above image display the details of “Table” for “3-1-1 service request center Dataset” using ‘AWS-Athena’.
### Step 12: Data Visualization
* These visualizations are ways the data analysis results are presented in an easily understood format. These renderings glance at the audiences by displaying a time series or the cross tab of trends over time or across kinds of work or regions.<br>
![figure 38-1](https://github.com/user-attachments/assets/1630e3ce-6251-4feb-90f6-010efe61d4a0)
* The above image display the details of “3-1-1 service request center Dataset” report using ‘Excel’.
![figure 38](https://github.com/user-attachments/assets/f722f975-439a-4bb0-b1c0-e3f72b212e3f)
* The above image display the details of “3-1-1 service request center Dataset” report using ‘Excel’.
### Step 13: Data Publishing
* Data publishing can be defined as the grouping or disseminating of the analysis results to other parties.
* This could be in compressed files copied to an S3 bucket for consumption, pre-built and ready dashboards in QuickSight, or weekly, daily, or monthly summaries sent as email or dropped into a folder or S3 bucket.
### Step14: Cost Estimation
* The AWS Pricing Calculator was used to estimate the cost of setting up and the subsequent running of the data analytic platform.
* It costs approximately $ 630.84 to process and analyze the business license data every month using Amazon S3, Athena, Glue, and Quick Sight.
* This estimate will factor in the data's size, its quality in terms of storage, processing, and data visualization, and the frequency of updates of the business license records.<br>
![14 cost](https://github.com/user-attachments/assets/1691f02f-7406-46e2-8b81-b5bd7036db82)
* The above image shows the cost estimation of City of Vancouver project.
