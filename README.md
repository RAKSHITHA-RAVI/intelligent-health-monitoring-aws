# Intelligent Health Monitoring & Heart Attack Prediction System (AWS)

An end-to-end, cloud-based healthcare analytics and machine learning system built using AWS.  
This project simulates continuous patient monitoring, processes large-scale health data, predicts heart attack risk using machine learning, and triggers real-time alerts for high-risk patients.

> 

##  Project Overview

Modern healthcare systems require scalable, real-time analytics to proactively detect health risks.  
This project demonstrates how **cloud computing, big data processing, and machine learning** can be combined to build an **intelligent, automated healthcare monitoring pipeline**.

The system:
- Stores historical and real-time patient vitals in Amazon S3  
- Processes and aggregates data using Apache Spark on Amazon EMR  
- Trains and deploys a heart attack risk prediction model using Amazon SageMaker  
- Performs real-time inference using AWS Lambda  
- Sends automated alerts using Amazon SNS  
- Enables SQL-based analytics using Amazon Athena  

---

##  System Architecture

**AWS Services Used**
- **Amazon S3** – Centralized data lake for raw, processed, and prediction data  
- **Amazon EMR (Apache Spark)** – Large-scale data cleaning and aggregation  
- **Amazon SageMaker** – Machine learning model training and real-time inference  
- **AWS Lambda** – Serverless risk evaluation and automation  
- **Amazon SNS** – Email alerts for high-risk patients  
- **Amazon Athena** – SQL analytics on health data stored in S3  

---

## 🔄 End-to-End Workflow

### 1️⃣ Data Ingestion (Amazon S3)
- Historical patient records and simulated real-time vitals are stored securely in S3.
- Simulated vitals replicate wearable device data:
  - Heart rate  
  - Blood pressure  
  - Sleep duration  
  - Physical activity  

---

### 2️⃣ Big Data Processing (Apache Spark on EMR)
- Apache Spark aggregates **7 days of vitals per patient**.
- Weekly summaries are computed:
  - Average heart rate  
  - Average systolic & diastolic blood pressure  
  - Average sleep hours  
  - Number of physically active days per week  
- The processed dataset is written back to S3 for machine learning.

---

### 3️⃣ Machine Learning Model (Amazon SageMaker)
- An **XGBoost classification model** predicts heart attack risk.
- Data preprocessing includes:
  - Splitting blood pressure into systolic and diastolic values  
  - One-hot encoding categorical features  
  - Removing identifiers to prevent data leakage  
- Model performance is evaluated using **AUC (Area Under ROC Curve)**.
- The trained model is deployed as a **real-time SageMaker endpoint**.

---

### 4️⃣ Real-Time Risk Scoring & Alerts (AWS Lambda + SNS)
- AWS Lambda:
  - Reads processed patient data from S3  
  - Invokes the SageMaker endpoint  
  - Calculates risk scores for each patient  
- If the risk score exceeds a predefined threshold:
  - An email alert is automatically sent via Amazon SNS to healthcare providers  

---

### 5️⃣ Analytics & Insights (Amazon Athena)
- Athena enables SQL queries directly on S3 data.
- Used to analyze:
  - High-risk patients  
  - Risk trends by age group  
  - Relationship between sleep, activity, and heart attack risk  
- Supports long-term, data-driven healthcare monitoring.

---

##  Machine Learning Details

- **Algorithm:** XGBoost  
- **Task:** Binary classification (Heart Attack Risk)  
- **Evaluation Metric:** AUC  
- **Inference Mode:** Real-time via SageMaker endpoint  

---
## 🛠️ Tech Stack

- **Programming:** Python  
- **Big Data:** Apache Spark, Amazon EMR  
- **Machine Learning:** XGBoost, Amazon SageMaker  
- **Cloud & Serverless:** AWS S3, AWS Lambda, Amazon SNS  
- **Analytics:** Amazon Athena  

---


