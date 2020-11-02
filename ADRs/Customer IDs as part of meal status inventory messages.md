# Customer IDs as part of meal status inventory messages

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Foods" system Subscription Notiication engine consumes meal status update messages. It then needs to notify Notifications Scheduler to send personalized messages to customers. Should we embed customer IDs as part of meal status update messages with an option of it being empty in many cases, or should Subscription Notiication engine query the Meals Inventory DB to attribute a meal to a customer? 

### Requirements

* The "Farmacy Food" system needs to issue personalized notifications to subscribed customers. 

### Business Assumptions

* Large portion of meals, perhaps most of them, will be purchased anonymously at the fridge, and not ordered by subscriptions.

## Decision drivers

* Most of the meals records in inventory will not need customer ID attribute, therefore introducing it in the main inventory DB may be redundant.
* On the other hand, enrichment is a costly operation, that may result in time to process the initial un-enriched message and additional API calls.
* Having ID as part of message makes for a simpler system as long as the message as a whole is not too large.
* At the moment the messages seem to be small and simple.

## Considered options 

* Query the Meals Inventory DB directly by Subscription Notification engine to enrich the meal inventory message.
* Include customer ID for all meal inventory messages. Leave it empty for anonymous purchases.

## Decision

 Include customer ID for all meal inventory messages. Leave it empty for anonymous purchases.

__Reasons:__ 
* Speed of processing.
* Simpler system as long as messages are small.

### Consequences

* Having to manage additional attribute in the entire Meals Inventory DB.
* Larger DB size.
* The decision will have to change if messages become too large or with too many attributes.