# Meal Inventory Updates

## Status

ACCEPTED

## Context and Problem Statement

Farmacy Foods produces meals in one or more central kitchens, delivers those meals to various locations, where they are sold to customers via a smart fridge or point-of-sale system.
The meals are the central aspect of the business, and there is a big focus on food quality.

### Requirements

* Each meal will be tracked from the point of its order (in case of an ordered meal), through creation in the kitchen and delivery, stocking the fridge, and purchase by the customer.
* Customer can give feedback on a meal after buying it.
* Customers can search for available meals nearby.
* Some history of the meal should be recorded, such as where it was produced, for tracking purposes.

### Business Assumptions

* Inventory changes are not too frequent, since they are tied to movement of a physical meal - like an employee stocking the fridge, or a customer buying a meal.
* Meals are generally produced and purchased in a single area. There is no interaction between the databases.
* Peak load is expected around lunch time.

## Decision drivers

* The database should have fast querying by location, for searching.
* This is the part of the system with the highest load, since every event needs to query it. On the other hand, the rate of changes is tied to physical events in the world, so it is generally not too high.

## Considered options 

* Tracking each meal separately vs. grouping meals by type
* Central database vs. per-fridge database 

## Decision

Meals are tracked in a central database where each meal has a unique ID.

A meal status may include (but not limited to) several attributes:
* Type
* Where and when it was produced
* Status - ordered, produced, available for purchase, or purchased
* Location - kitchen, fridge, or sold to customer
* Date and time of expiration
* Price
* Additional attributes to indicate if the meal was created due to subscription or regular production order
* User ID for reserved meals (empty for meals that aren't reserved)
* Referral code

Any event involving the meal is updated in the system via the Data Platform, including:
* Creating the meal order - add a new entry in the database
* Delivery from kitchen to fridge - update location of meal
* Sale - update status as sold

There will be several APIs to the database, for the various use-case.
For example, the employee in charge of stocking the fridge uses the Refiller Applicatino that connects with a dedicated API.

__Reasons:__ 
* Simpler architecture with a single database.
* Single enterprise wide database rather than a per fridge database.
* Scaling for faster read-only access can be done with read-only replicas of the database.

### Consequences

* Central database offers a simple design.
* The APIs offer an abstraction over the database.
* Central database with high load, which is also a central point of failure.