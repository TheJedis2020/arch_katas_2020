# Separate microservices for prices acces and calculation

## Status

ACCEPTED

## Context and Problem Statement

The customers should be able to see the final price at purchase or via the application. The system must be highly available and elastic to support the all purchases at peak times.

### Requirements

* The price must be recalculated when the policies or base price change. 
* High availability and fault-tolerance is a must.

### Business Assumptions

* The base price for a meal will be held in meals inventory.
final meal price should be modified by various pricing policies, according to time, place, customer type etc.
* The purchase session, and the customer apps must have fast access to the current prices. 


## Decision drivers

* While the price must sometimes be recalculated, we don't want them to be calculated when customer views the prices. Recalculation takes time and the pricing calculation engine must access several other services to calculate the price correctly. Since this part of system needs to be highly available, it is preferable to separate the query amd the calculation. 

## Considered options 

* A single microservice that calculates final price on the fly.
* Add a dedicated, fast access, reliable and simple cache store with it's own fault tolerant API, that will only pull the calculated prices from the cache. The cache will be updated at certain times of day by pricing calculation engine.

## Decision

Add a dedicated, fast access, reliable and simple cache store with it's own fault tolerant API, that will only pull the calculated prices from the cache. The cache will be updated at certain times of day by pricing calculation engine. When session starts get latest prices per current meals (meal types) in the fridge and “freeze” prices per session. If prices updated during the ongoing session then customer is not impacted. 

__Reasons:__ 
* Speed of access.
* Improved reliability at critical areas. 
* Isolation of part of DB that required higher reliability and fault-tolerance from the rest of the Inventory.

### Consequences

* Having to manage additional store.
* Must be of higher reliability than Price Policies or Meals Inventory DB, should consider distributed store and improved reliability measures for this store.
* Must have improved elasticity for peak times.
