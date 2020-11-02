# Reusing subscription capability for same day meal orders

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Food" system allows for direct meal purchases at the fridges and a subscription service. The subscription capability can also be used for same day orders.

### Requirements

The customer requirements regarding orders are vague, but it could be inferred that a same-day order would be a desirable business option if kitchen capability allows for it.

### Business Assumptions

* The "subscription" means the ability for an identified customer to purchase a pre-paid option to have a personal meal delivered to a smart fridge of his chosing at the appointed time for a certain number of days. 
* The expiration date of subscribed meal is set on the same day as it is about to be consumed
* It is assumed that meals prepared for subscribed customers are marked with their name and otherwise are distinct from regular meals to be easily identified in the fridge.
* The one-day time constrained subscription is equivalent to daily meal order, allowing to create a separate UI for meal orders that rides atop the subscriptions engine.

## Decision drivers

* While same day orders are different from subscriptions, requiring different capabilities, upon close examination it becomes clear that a same day order can be formulated as a kind of 1-day subscription under a certain time constraint.

## Considered options 

* Creating separate capability for same day orders.
* Reusing subscription subsystem.

## Decision

Reusing subscription subsystem.

__Reasons:__ 

* Single redundant meal purchase system for all kinds of orders.
* Better maintainability and deployability.

### Consequences

* Different UI will have to be developed for same API as subscriptions.
* Maintaining a special subscription template which has to be protected.
* There will be need for time constraints checks when creating the order.
* Kitchen load may influence availability of option and time constraints.