# Demand Planning

## Status

ACCEPTED

## Context and Problem Statement

Customers buy meals from the fridge.

If the fridge is empty, the customer cannot buy a meal
We need to prepare enough meals and deliver them to the fridge on time.

If the fridge is full and not all the meals are bought, they expire.
We need to prepare not too many meals.

### Requirements

We want to predict (as much as possible) what are the best ways to refill the fridges.
This means when to refill and with which meals.

Planning for kitchen supplies is out of scope.

### Business Assumptions

Meals are produced and delivered at predetermined times, e.g. every morning.

It is possible in the future to create higher priority orders to resolve a local shortage.
For example, if a fridge is emptied out suddenly due to a one-time event, we might want to
rush out an order to refill that specific fridge so that it won’t be empty.
This has logistical implications, such as having delivery staff on call for taking
the meals from the kitchen to the fridge. The system will support this future development,
but this is not the main design concern for now.

## Decision drivers

Use Machine Learning (ML) tools to predict future demand. The idea is to predict which meals will
be bought from each fridge, based on previous usage at that location.

The ML Engine must be aware of all purchase actions.

The specifics of the ML mechanism used is out of scope of this document.

## Considered options 

* The Demand Planning Engine will poll the Meals Inventory DB at predefined intervals (e.g. every 10 minutes).
* The Demand Planning Engine will listen to meal purchase events.

## Decision

* The Demand Planning Engine will be notified of each meal purchase (see Purchase Handling ADR).

* The Engine can access the Meal Inventory Service to query current status in each location.

* The Engine calculates projected future demand, and sends orders to the kitchen. This could be on a daily basis or any other frequency, based on business needs. It can also react to sudden “fridge empty” situation in case of a large purchase, or other anomaly.

__Reasons:__ 
* The Engine has full access to the inventory data. This allows it to use any necessary planning algorithm, without depending on limited information.
* Orders are created automatically by the Engine to ease work in the kitchen.

### Consequences

Demand Planning Engine is a high-level concept that can interface with several other parts of the system.
The downside is that it depends on those parts of the system. Changes in those parts should be reflected in the Engine.