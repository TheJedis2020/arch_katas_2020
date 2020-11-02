# Notifications Sender to handle several notifications channels

## Status

ACCEPTED

## Context and Problem Statement

The "Farmacy Food" system should allow sending notifications to subscribers after they have received the meal, to prompt them to send customer satisfaction feedback.

The system should support ability to send messages via various communications channels, e.g. SMS, push notifications, emails, recorded messages, etc.

### Requirements

* Support for push message, email, and/or SMS notifications to subscribed customers, some immediate and some deferred and future possible channels and integrations

### Business Assumptions

Several communication channels to communicate with customers should be supported.

## Decision drivers

* Several communication channels should be supported by the notifications service as plugins.
* New media channels addition should be supported as simply as possible by developing new model and implementation of certain interfaces.

## Considered options

* Have the Notifications Sender engine be a microservice that communicates with other microservices dedicated to sending messages down specific channels.
* Make notifications Sender a microkernel service that supports communication capability plugins.

## Decision

Make notifications Sender a microkernel service that supports communication capability plugins.

__Reasons:__ 

* Easy to react to change in plugin models while minimizing changes to the core system.
* Easy to deploy specific models rather than the whole system.
* Easy to test specific model as a component in isolation.

### Architectural style

__Microkernel__.

### Consequences

* Simple to maintain, deploy and add plugins.
* Extensible.
* Should consider switching to microservices if core system starts changign frequently.