# Business growth strategy  

![image](./Images/Businessgrowth.jpg) 

Follow the links for the more detailed description of involved capabilities.  

## Short term  

* Build [Identity and Profile]() to allow personalized [Purchases]() and [Payments](). At this point it is possible to begin issuing customer cards and tokens for identification at fridges without the card. Purchase of id tokens should be encouraged by, for example, letting schools or health clubs distribute them for discounts.
* Build [Fridge Capability](), that would allow to create __Purchase Session__ for each purchase and would allow the fridge status to be monitored over the network. Plus it will enable theft meal protection and it will prevent customers taking someone else's meal by mistake. 
* Build [Meals Inventory]() capability with __Fridge Admin API__ and __Fridge Admin Application__ to manage meals inventory in fridges. Meals inventory should consume meal status events from kitchen and fridges. The same messages will be used in the future by other capabilities, so at this point we introduce asynchronous event bus using message broker like Kafka.
* Build [Kitchen Capability]() with the __Kitchen Service API__ and __Kitchen Application__ 
* The [Meals Inventory]() and [Kitchen Capability]() would now facilitate management of all the steps of meal production, delivery and purchase. The [Meals Inventory]() now makes possible to track every meal from the moment of order creation to the moment of purchase finalization.   
* Scale the business by expanding city-wide, to as many locations as possible, to increase exposure and traction.
    - __Requirements overview:__ The architecture should be highly fault-tolerant and be elastic enough to withstand peaks at peak times. Ther perfomance requirements are moderate - up to thousands of users at peaks. It should also be able to scale together with the business for scenarios like setting up dozens of fridges at new locations. The Payment and Identity capabilities should also be highly available to process the payment. For that purpose the [Payments]() capability would utilize several card processing providers. Kitchen capability should be planned scalable from the outset to allow more than one kitchen to fullfill the orders.
    - __Architecture characteristics:__ Fault Tolerance, Elasticity, Scalability, Availability, Cost
    - __Architecture preferences:__ Microservices, Event Driven

## Mid Term  

* Add [Notification Service]() with __Notificaiton Scheduler__ to  notify customers of meal arrivals and advertising content, and also to allow the feedback collection promots to be scheduled and sent. Consider 3P purchase.
* Add [Feedback Capability]() to allow the customers to provide feedback and ranking for meals they have consumed. 
* Add [Subscription Capability]() through which the customer would be able to make personal orders for single meals or to purchase simple subscription plans via a __Subscription Services__. Add several basic subsctiption options to __Meal Subscription DB__ and allow users access these via __Farmacy Food Application__ and __Subscription Service API__. __Subscription Services__ can now notify customers of meal arrivals to their preferred fridges, and to schedule feedback collection messages.
* [Subscription Capability's]() __Work Orders Engine__ will now post work order messages to [Kitchen Capability]() to create kitchen work orders automatically according to customer subscriptions. Work orders will be directed to kitchens according to fridge locations.
* To make the __Farmacy Food__ viral, add [Referrals and Rewards Capability](). Customers would be able to send referral codes to their friends and family, which will be stored in customer profiles, making each purchased by referral upgrate the customer credit in the [Identity and Profile](). These credits would be used on the next referree orders, offering discounts, coupons, promotions and other exciting opportunities.  
* Begin to scale the business nationally by introducing new kitchens and new fridges in locations nationwide.
    - __Requirements overview:__ The system should be able to handle workflows. The Notification Service should be elastic and scalable to handle peak times also support plugins to handle different types of communication channels, but the performance requirements are still moderate. Subscription and Feedback capabilities must be scalable and evolvable to allow further expansion of these services for the next stage of business evolution. Referrals and rewards API, and also Feedbacks API should be available. Must be able to pivot several times at this stage.
    - __Architecture characteristics:__ Scalability, Elasticity, Workflow, Evolvability, Plugins
    - __Architecture preferences__: Event Driven. Microkernel for __Notifications Sender.__

## Long Term  

* Add [Data Platform]() to consume meal status events, purchase notifications and other data from the event bus. It will include __Ingestion Module__ to stream data into __Data Lake__, to be analized by __Processing and Analytics__ subsystem. This will allow analytics, operation reports, business performance tracking, data exploration and demand planning. This capability will be used by business administrators, health experts and data scientists to plan demand and devise business strategy.
* Add [Expert Platform Capability]() and [CMS](). This will connect health food experts, Kwaku's meal production and distribution system, and the customers. The health food experts will publish meal plans for customers to select and turn into subscriptions.
* Expand [Subscription Capability]() to use meal plans from the Expert Platform as templates for customer subscription.
* Expand [Feedback Capability]() and [Referrals and Rewards Capability]() to let users provide feedback and ranking for experts and meal plans, and refer friends and family to experts.
* Expand [Notification Service]() to allow the experts to push commercial content and feedback requests.
* Build upon the [CMS]() and the capabilities above to evolve into a health-oriented community social network. Continue to build community through the viral capabilities and social media advertizing.
* Expand to new locations nationally and internationally.  
    - __Requirements overview:__ Evolvability and scalability are the key requirements. Consider 3P party services for CMS, Messaging service and social media exposure. Performance and cost become main concerns with expansion and addition of Data Platform. Availability needs to be high for expert-customer interactions to flow seamlessly. More and complex workflows are introduced.
    - __Architecture characteristics:__ Evolvability, scalability, availability, performance, costs.
    - __Architecture preferences:__ Event driven.
