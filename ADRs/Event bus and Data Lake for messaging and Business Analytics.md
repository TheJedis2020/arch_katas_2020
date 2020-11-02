# Event Bus and Data Platform for messaging and business analytics

## Status

_ACCEPTED_

## Context and Problem Statement

We want "Farmacy Food" to have robust Event Bus for different services streaming inventory and service messages, and a Data Platform for business analytics, demand planning, reporting etc.

### Requirements

* The "Farmacy Food" system needs subsystem for message exchange between services.
* The "Farmacy Food" system needs subsystem business analytics, reporting and demand planning.

### Business Assumptions

Businesses rarely have the whole picture of their client base. In order to react to changes in customer population and customer behavior in a timely and flexible way, in order to better predict demand and optimal fridge contents, the system behavior must be recorded and analyzed.

## Decision drivers

* The system rides on top of asynchronous event bus with various topics that passes mostly meal status events. These events can be recorded for further analysis.
* There is a need for Data Warehouse to keep the results of Business Analytics processing for reporting and planning.

## Decision

* Event bus with several topics for message exchange streaming.
* Data Lake for raw data collection.
* Analytics and processing module for data analysis.
* Data Warehouse


### Architectural style

* __Event based architecture__
* __Data Lake__

### Consequences

* Need to maintain Business Analytics infrastructure.
* Costs vs Usability balance must be carefully observed.
