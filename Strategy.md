# Strategy  

## Stage 1 - The basics  

To achieve our vision, we would begin by expanding the existing infrastructure with basic capabilities and services, like [Identity and Profile]() to allow for personalized [Purchases]() and [Payments]() Capabilities.  We would add new [Fridge Capability]() that would open new opportunities by creating Purchase Session for each purchase and would allow the fridge status to be monitored over the network.  

We then would augument the [Kitchen Capability]() with the Work Order Creation Engine, and start managing all the steps of meal production, delivery and purchase with the help of [Meals Inventory](). Now the business administrators can track meal status, monitor fridges inventory and create Kitchen Production Orders accordingly.  

## Stage 1 - The intermediate  

The next stage would be to introduce [Subscription Capability]() through which the customer would be able to make personal orders for single meals or to purchase simple subscription plans via a [Subscription Services](), and a [Notification Service]() to notify customers of meal arrivals and advertising content. [Notification Service]() would also begin to collect feedback and meal rankings via feedback messages and the [Feedback Capability](). Customer subscription would utilize already existing [Kitchen Capability]() to create kitchen work orders automatically according to subscriptions.  

## Stage 1 - The advanced  

We would connect all systems in a hybrid Microservices/Event-Driven architecture, what allows high flexibility, scalability and elasticity, coupled with ability to support workflows. The messages are mostly meal status messages, notifying the system via the event bus in the [Data Platform](). The status messages are consumed by the services that need to plan responses, like [Notification Service](). The [Data Platform]() will allow us to gather customer preferences and consumption patterns, allowing us to perform business analytics and leading to better service and smarter business decisions.  

To make our idea viral, we will utilize [Referrals and Rewards Capability](). Customers would be able to send referral codes to their friends and fmily, which will be stored in customer profiles, making each purchased by referral upgrate the customer credit of the referree. These credits would be used on the next referree orders, offering discounts and other exciting opportunities.  

Finally on top of these basic services we would now build our [Expert Platform Capability](). This is the core of our Vision, the heart of our community-building architecture, connecting health food experts, Kwaku's meal production and distribution system, and the customers looking to improve their well-being through timely and healthy meals. Also, using [Content Management System Capability](). the health experts would publish articles, conduct research, collect feedback and promote their expertize.  

