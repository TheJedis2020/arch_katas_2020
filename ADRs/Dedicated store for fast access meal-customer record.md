# Dedicated store for fast access meal-customer record

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Foods" system should allow customer subscription to meals identification at the fridge of the taken meals with respect of belonging or not belonging to the customer that has opened the fridge. While the simple solution would be to add an attribute of customer ID to every meal managed by Meals Inventory, and to every meal status message, the immediacy of resolving taken meals attribution at the fridge demands a faster and more reliable approach.

### Requirements

* The smart fridge must support detection of meals taken by the customer and issue a warning if the meal taken by the identified customer belongs to another identified customer. 

### Business Assumptions

* Fridge is capable of issuing a warning (light, sound), if a subscribed customer picked a meal of another subscribed customer.
* It is assumed that meals prepared for subscribed customers are marked with their name and otherwise are distinct from regular meals to be easily identified in the fridge.
* Additionally to the meal, subscribed customer can pick up anything else from the fridge except meals for other subsctibed customers, the final payment upon door closure will include the difference.
* Large portion of meals, perhaps most of them, will be purchased anonymously at the fridge, and not ordered by subscriptions.

## Decision drivers

* Most of the meals records in inventory will not need customer ID attribute, therefore introducing it in the main inventory DB is redundant and would make the DB larger and slower.
* At the time of creating meal order from subscription, Subscriptions Work Order engine is already aware of the customer ID, meal ID (because it creates the meal order), and the target fridge. Therefore it does not need Inventory meals DB to create a record quickly.
* Without a dedicated fast store, Purchase Session will have to query the larger Inventory DB to attribute taken meals customer ID, which may have a performance penalty. Additional to that, attributing meals to customers at the fridge during a purchase is a critical activity for the subscriber purchases, where reliability and performance is paramount.
* If there is a problem of accessing Invenotory DB, the reliable dedicated store will still allow the fridge to open doors for the customer.

## Considered options 

* Query the Meals Inventory DB directly when customer identifies with the fridge.
* Add a dedicated, fast access, reliable and simple store that for each meal created by order from Subscription Work Orders engine will keep a meal ID, fridge ID and customer ID.

## Decision

Meals Inventory will feature a dedicated, fast access, reliable and simple subscribed meals store that for each meal created by order from Subscription Work Orders engine will keep a meal ID, fridge ID and customer ID. The SubscribedMealsStore records will be created directly by Subscription Work Orders engine. The SubscribedMealsStore records will be queried directly by Purchase Session. The SubscribedMealsStore record will be erased by Purchase Session when it finalizes the purchase.

__Reasons:__ 
* Speed of access.
* Improved reliability at critical areas. 
* Isolation of part of DB that required higher reliability and performance from the rest of the Inventory.

### Consequences

* Having to manage additional store.
* Must be of higher reliability than Inventory DB, should consider distributed store and improved reliability measures for this store.
* Must have improved elasticity for peak times.