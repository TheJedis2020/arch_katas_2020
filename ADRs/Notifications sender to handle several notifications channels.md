# Notifications Sender to handle several notifications channels

## Status

_PROPOSED_

## Context and Problem Statement

The "Farmacy Foods" system should allow sending notifications to subscribeds after they have received the meal, to prompt them to send customer satisfaction feedback. The system should support ability to send messages via various communications channels, e.g. SMS, push notifications, emails, recorded messages etc.

### Requirements

* Support for push message, email, and/or SMS notifications to subscribed customers, some immediate and some deferred.

### Business Assumptions

Several media channels to communicate with customers should be supported.

## Decision drivers

* Several communication channels should be supported by the notifications service, but the core message processing, composition and sending is rather small and simple and is not supposed to change much.
* The specifics of sending messages via various channels is of no interest to the core.
* New media channels addition should be supported as simply as possible.
* TBD Michael

## Considered options

* Have the Notifications Sender engine be a microservice that communicates with other microservices dedicated to sending messages down specific channels.
* Make notifications Sender a microkernel service that supports communication capability plugins.

## Decision

Make notifications Sender a microkernel service that supports communication capability plugins.

__Reasons:__ 
* TBD Michael

### Architectural style

__Microkernel__.

### Consequences

* Simple to maintain, deploy and add plugins.
* Extensible.
* Should consider switching to microservices if core system starts changign frequently.