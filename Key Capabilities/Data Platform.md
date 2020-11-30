# Data Platform  

![image](../diagrams/Data%20Platform%20Diagram.jpg) 

## Capability rationale and description

Farmacy Food is not just about food. It's about smart, intelligent and AI driven decisions at the right time. There's plenty of information in the ssytem which could be used for decisions, analytics and maybe even clinical researched in the future. Each event, be it creation of an order, meal preparation, meal arrival to fridge customer feedback contains information that could used. Therefore, __Farmacy Food__ needs robust and reliable Data Platform to support periodic as well as near real time stream analytics data appetites. Through this platform the experts, knowledge employees and the administration can track trends, analyze consumer preferences and predict inventory needs. In addition analysts and data scientists will get all tools to support their needs in data exploration, machine learning model training and machine learning model hosting. Data platform will also require __Encryption__ capability at the very detailed level to store and process highly sensitive data.


## Use cases

* Periodic (batch) analytics
* Near real time stream analystics
* Data exploration
* Data visualization
* Machine Learning model training
* Machine Learning data featurization
* Machine Learning model hosting

## Components

* Ingestion subsystem.
* Data Lake.
* Processing subsystem.
* Serving subsystem.

## Architectural characteristics

* Fault Tolerance.
* Performance.
* Elasticity.
* Scalability.
* Supports workflows.

## Architectural choice

* Lambda Architecture

## Relevant ADR(s)

* [Event bus and Data Lake for messaging and Business Analytics ADR](../ADRs/Event%20bus%20and%20Data%20Lake%20for%20messaging%20and%20Business%20Analytics.md).
