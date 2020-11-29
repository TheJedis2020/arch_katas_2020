# Data Platform  

![image](../diagrams/Data%20Platform%20Diagram.jpg) 

## Capability rationale and description

Each meal-related event, be it creation of an order, meal preparation, meal arrival to fridge and meal purchase generate messages that producers send to the topics in Data Platform Queues, to be consumed by services such as Notification Scheduler. Each such message bears a customer id, meal details, referral code if relevant, and meal status.
To facilitate business analytics __Farmacy Food__ needs robust and reliable Data Platform. Through this platform the experts and the administration can track trends, analyze consumer preferences and predict inventory needs. 


## Use cases

* Collect data for logs and analytics

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

* Event-driven

## Relevant ADR(s)

* [Event bus and Data Lake for messaging and Business Analytics ADR](../ADRs/Event%20bus%20and%20Data%20Lake%20for%20messaging%20and%20Business%20Analytics.md).