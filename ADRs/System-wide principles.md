# Customer IDs as part of meal status inventory messages

## Status

[ ] Reviewed by Michael
[ ] Reviewed by Dmitry

## Context and Problem Statement

The system handles transactions of meals across several actors (from kitchen to customer)
and various locations (from kitchen to smart fridge).
A cloud architecture is the obvious choice for this.

This document describes broad aspects of the cloud architecture.
It defines the performance needs of the system, without getting into specifics.

### Requirements

* Availability
    * Very important. We don't want to block a sale due to downtime
    * It’s Possible (but discouraged) to have planned/scheduled downtime at night. No movement of meals (production, sales, etc.) would be done at this time window.
* Reliability
    * The system handles food and money, so things need to be 100% reliable.
    * We must not sell spoiled food, or charge customers incorrectly.
* Scalability
    * Events in the system are correlated to a physical product (meal), so the system handles a relatively small number of actions.
    * Each metro area generally has separate products/users/staff, so scalability can be handled by having separate servers per area, with minimal communication between them.
* Performance
    * Most actions (e.g. sale of a meal) should be updated in the system within a few seconds.
    * Real-time is not needed.
    * On the other hand, we don’t want the customer to stand in front of a fridge and not be able to open it due to a long delay. The upper limit of a few seconds is a hard limit.
* Elasticity
    * Peak system activity is expected during lunch. System should be able to handle that load.
    * Might have unexpected peaks due to events (e.g. conference), but the impact is limited since the fridge capacity is limited - the activity stops when the food runs out.
* Security:
    * Handling Personal Identifiable Information (PII) - regulated by GDPR in Europe, might per-state regulations in the US.
    * Handling money - PCI DSS compliance.
    * Handling sensitive personal information, e.g. dietary preferences - no legal limitations, but need to be careful from an ethical and user expectation standpoint.
    * Not officially handling medical records, so HIPAA compliance is not needed.


### Business Assumptions

See above.

## Decision drivers

This document does not list any decisions.

## Considered options 

This document does not list any decisions.

## Decision

This document does not list any decisions.

### Consequences

This document does not list any decisions.
