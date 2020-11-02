# Separate channels for anonymous and personal meal status messages

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Food" system maintains meal status via Meals Inventory subsystem.

The Meals Inventory subsystem consumes meal status messages from various other subsystems to maintain inventory integrity, indicating whether the meal has been ordered, produced, placed in a fridge, purchased or expired. The system also needs to notify subscribed customers of their meals status changes, but it does not send messages to non-identified customers.

Customer needs to create subscription at least once to be identified henceforth by the system. Since we assume that majority of meal purchases are anonymous, it means that a relatively small subset of meal status messages should be reflected to customers.

### Requirements

Analysis of the "Farmacy Food" briefing has yielded the following potential requirements:

* Maintaining a meals inventory.
* Support for push message, email, and/or SMS notifications to subscribed customers.

### Business Assumptions

It is worthy of notice that the requirements are quite general and vague, allowing both for freedom of interpretation of business casem but also greater freedom of error. Therefore following business assumptions were made by the team, reflecting what we consider to be a balanced system of business decisions:

* The messages sent to subscribed customers are meal status and customer satisfaction surveys.
    * Notification of meal arrival to the fridge.
    * Customer satisfaction surveys sent two hours after the meal has been picked by a customer.
    * Notification to the customer that did not pick up a meal for a long time (it will be discarded by the refiller at the next refill as expired).
* It is assumed that meals prepared for subscribed customers are marked with their name and otherwise are distinct from regular meals to be easily identified in the fridge.

### Additional context

* Promotional materials are not to be handled by the subscriptions subsystem.

## Decision drivers

* Meals Inventory Service and Purchase Session Management Service produce messages about meals status. The subscriptions subsystem has to issue personalized messages based on the meals status messages.
* The subscriptions subsystem activity has clearly distinguished peak times
    * Purchase events
    * The meal arrival messages
* Messages that the subsystem must produce or consume
    * __Consume__ messages from Meals Inventory Service about following meals statuses: 
        * Meal arrived to fridge. _Frequent at peaks_.
        * Meal is close to expiration (subscriber meals expire on the supposed consumption day). _Infrequent_.
        * Meal was purchased by the customer. _Frequent at peaks_.
    * __Produce__ following messages to Kitchen Meals Ordering service
        * Production orders for the kitchen based on subscriptions. _No peaks_.
    * __Produce__ following messages to Notifications Scheduler service
        * __Immediate__ Notifying customer his meal has arrived to the fridge. _Frequent at peaks_.
        * __Immediate__ Notifying customer about approaching expiration. _Infrequent_.
        * __Scheduled__ Proposals to fill customer satisfaction survey two hours after meal was taken from the fridge. _Frequent at peaks_.
* Notifications Scheduler service is also used to send promotional materials, but it is not directly dependent on existing subscriptions and has nothing to do with subscriptions tracking.
* TBD Michael - is the above OK?

## Considered options 

* Notifications Scheduler service would consume all meals status messages, use internal business logic to find out which of them should produce customer notifications and send them.
* Introduce Subscriptions Notifications service.

## The decision

* Introduce Subscriptions Notifications service that would listen to meals status  messages, and produce costomer notifications messages for Notifications service to consume, based on a store that connects meals IDs with customer IDs (described in separate ADR).
* The subscriber meal status notifications will use a separate queue than meals status messages.

__Reasons:__ 

* Separates meal status messages meant for inventory maintanance from customer notification messages into two separate queues improves performance, reliability, modularity and scalability of the system.
* TBD Michael - is the above OK?

### Architectural style: 

__Microservices__.

### Consequences

* Having to maintain additional microservice.
* Having to manage two separate queues.
