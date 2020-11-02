# Notifications Scheduler to handle scheduled notification

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Foods" system should allow sending notifications to subscribeds after they have received the meal, to prompt them to send customer satisfaction feedback. The messages should arrive a set amount of time after purchase confirmation.

The Subscription Notification service issues messages to customers on meals status change, so there is a similarity, but unlike those messages, the feedback prompts are not sent immediately.

### Requirements

* Support for push message, email, and/or SMS notifications to subscribed customers, some immediate and some deferred.

### Business Assumptions

It was not explicitely stated by the "Farmacy Food" customer which kinds of messages should be pushed to customers and at which intervals. We therefore assume the messages sent to subscribed customers are meal status and customer satisfaction surveys.

* Notification of meal arrival to the fridge.
* Customer satisfaction surveys sent two hours after the meal has been picked by a customer.
* Notification to the customer that did not pick up a meal for a long time (it will be discarded by the refiller at the next refill as expired).

## Decision drivers

* The Subscription Notification service consumes meal status messages and if the meal is a subscriber meal, sends notifications to subscribers. However the responsibility control of the sending time belongs to Notification Scheduler service, which is a final stop before a message is dispatched to the customer.
* The Subscription Notification service is under a larger load, already consuming meal status messages, prone to load peaks.

## Considered options

* Subscription Notification service would cache deferred messages to Notification Scheduler service and handle the scheduling.
* Subscription Notification service would mark the messages with "time-to-send" and have Notification Scheduler service schedule and send the customer messages.

## Decision

Have Subscription Notification service mark the messages with "time-to-send" and have Notification Scheduler service schedule and send the messages.

__Reasons:__ 
* Notification Scheduler service does not have to process the content of the message, unlike the Subscription Notification service, it only cares about time and addressee, having it handle the scheduling improves modularity and represents better separation of concerns.
* Removing BL for message scheduling and deferred sending from Subscription Notification Service into Notifications Scheduler improves performance and reliability, as it is now more available to handle meals status messages.
* In case Subscription Notification Service is down, its messages are still cached by Notifications Scheduler and will be sent, which is a better reliability.

### Architectural style

__Microservices__.

### Consequences

* Adding scheduled messages store to Notifications Scheduler.
* Adding "time-to-send" field to messages coming from Subscription Notification service.