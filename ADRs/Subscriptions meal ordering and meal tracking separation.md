# Subscriptions meal ordering and meal tracking separation

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Foods" system should allow both direct purchases at the fridge and customer subscriptions based on the suggestions of health professionals as well as subscriber notifications.

### Requirements

Analysis of the "Farmacy Food" briefing has yielded the following potential requirements:

* Subscription service for meals per a period of time, while still allowing direct meal purchases at the fridge.
* Support for push message, email, and/or SMS notifications to subscribed customers.

### Business Assumptions

It is worthy of notice that the requirements are quite general and vague, allowing both for freedom of interpretation of business casem but also greater freedom of error. Therefore following business assumptions were made by the team, reflecting what we consider to be a balanced system of business decisions:

* The "subscription" means the ability for an identified customer to purchase a pre-paid option to have a personal meal delivered to a smart fridge of his chosing at the appointed time for a certain number of days. This means that at a certain point of time subscription must yield a kitchen production order for a personalized meal, which will then arrive at a designated fridge.
* The time duration of subscription may be on a resolution of a single day to several months.
* The expiration date of subscribed meal is set on the same day as it is about to be consumed
* The messages sent to subscribed customers are meal status and customer satisfaction surveys.
    * Notification of meal arrival to the fridge.
    * Customer satisfaction surveys sent two hours after the meal has been picked by a customer.
    * Notification to the customer that did not pick up a meal for a long time (it will be discarded by the refiller at the next refill as expired).

## Decision drivers

* Creation of production orders from subscriptions is a scheduled activity, that would ideally be balanced around both kitchen load, system load and customer pressure. Since there is unlikely to be a spike in sudden subscriptions, we can assume no significant load peaks. Therefore orders creation can be done at schduled intervals.
* Tracking of subscription meals has activity peaks at the following times:
    * Meal arrivals to fridge.
    * Meal purchases.
* Tracking system is required to send messages to subscribed customers, some immediate, some scheduled. Production orders creation system is required to send kitchen orders to kitchen, which is a different communication channel. All production order messages are immediate.
* Reliability requirements from production order creation subsystem are more strict than from tracking and notifications subsystem. It is more important that the customer is fed than to send him a satisfaction survey.
* Scalability and elasticity requirements are higher for tracking and notifications subsystem.

## Considered options 

* Service based architecture.
* Event driven architecture.
* Microservices architecture.

## Decision

__Two separate microservices:__

* Subscription Work Orders engine for scheduled creation of production orders based on subscriptions DB.
* Subscription Notification and tracking service.

__Reasons:__ 
* The services proposed are using different databases, produce and consume different communications message types and belong to different domains.
* The services would operate under different reliability, scaling and elasticity assumptions.

### Architectural style

__Microservices__.

### Consequences

* Having to maintain two types of entities under different rule sets.
* Impact on DevOps.

