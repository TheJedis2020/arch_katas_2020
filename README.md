# The "Farmacy Food" System  

![image](./Images/Title.png)  

## Prelude  

All successful business stories start with a problem to solve. In this case, all began with a very personal pain. Kwaku, the person who originated the idea of "Farmacy Food", was frustrated, overwhelmed by a recent failure of his latest business venture. His energy level was low, his time was extremely limited, and his mind was preoccupied by anything but maintaining a healthy diet. It was then, when a thought of how to get a healthy snack without worrying about its quality or wasting too much precious time on preparing it or looking for it struck a business chord. Modern entrepreneur is a high pressure business machine, and a well-functioning machine needs high quality fuel provided when necessary. We are what we eat. We function as we eat. It is especially important in these trying times, where COVID-19 wreaks havoc in the restaurants and food markets. Kwaku already has the dots - the kitchen, the fridges, the locations. Our goal as a team is to help him to connect them, by creating a system that can grow, expand, thrive and benefit both the owners and the community as a whole.  

## The Vision  

We also understand that any system or business usually have humble beginnings and then grow organically into something more. The question is, into what. _Ab initio_, all __Farmacy Food__ has is a kitchen, the fridges, and a modest accounting and payment capabilities managed via QuickBooks.
Our vision is to build up from these capabilities and to evolve __Farmacy Food__ into a meeting place and even a social network, where health experts and customers can live the motto of business founder, Kwaku: _"Let thy food be thy medicine"_. There they would exchange and purchase recipes, meal plans and health related content, with the underlying infrastructure allowing them to purchase meals or subscribe whole meal plans from the experts of their choice, with a guarantee of delivery to the smart fridge near them.
Our conviction that we are not creating a mere mechanism, but a living community and therefore a system that can both help the business and community to grow, and also to be able to grow with them.  

## Business Requirements  

#### Short term  

* Support for third party smart fridges
* Monitor smart fridges inventories and customer purchases
* Generate work orders to kitchen based on inventory status
* Scale to multiple locations in the city, thousands of users

#### Mid term  

* Allow customer feedback and customer surveys
* Allow customer subscriptions
* Scale nationally, hundreds of thousands of users.
* Allow referrals and referree rewards
* Allow coupons and promotions

#### Long term  

* Support partnerships and donations
* Connect customers with health food experts for dietary counseling
* Establish a platform for engagement between health food professionals and the community.
* Establish a social network around the motto of _"Let thy food be thy medicine"_.

##  The Strategy  

All businesses desire to expand, and do so in a responsible and a community-serving way. In general terms the strategy we have adopted follows these guidelines:  

* We have an established and clear vision for the end state of our architecture. 
* Modern cloud-based technology allows for rapid establishment of event queues and distributed services.
* We therefore do not see benefits in evolving the architecture from a more simple and monolythic architectural style to the more distributed.
* We prefer to evolve not architectural styles, but rather capabilities. 
* We add architectural and technological elements as needed to support the capabilities, that would still be relevant in the end state.
* The benefits of this approach is elimination of unnecessary refactoring and technical debt as we evolve the system.
* Of course if we experiment with something that we don’t know we can do shortcuts, but we should have a very clear reason for __not__ aiming to the ideal target state.
* The motto is "we are not so rich that we could afford to buy cheap stuff".

 [Here](./Strategy.md) we outline our strategy - how we plan to scale and expand our architecture to empower __Farmacy Food__ to achieve its full potential.  

## The Architecture  

* [General Architecture](./GeneralArchitecture.md) - the general architectural idea.  

#### Basic Capabilities  

* [Fridge Capability](./Key%20Capabilities/Fridge%20Capability.md)
* [Card and Payment](./Key%20Capabilities/Card%20and%20Payment.md)
* [Identity and Profile](./Key%20Capabilities/Identity%20and%20Profile.md)  
* [Kitchen Capability](./Key%20Capabilities/Kitchens.md)
* [Meal Inventory](./Key%20Capabilities/Meal%20Inventory.md)

#### Intermediate Level Capabilities  

* [Customer Subscriptions](./Key%20Capabilities/Customer%20Subscriptions.md)
* [Notifications](./Key%20Capabilities/Notifications.md)
* [Feedback and Ranking](./Key%20Capabilities/Feedbacks.md)  

#### Advanced Capabilities  

* [Data Platform](./Key%20Capabilities/Data%20Platform.md)
* [Referrals and Rewards](./Key%20Capabilities/Referrals%20and%20Rewards.md)
* [Expert Platform and CMS](./Key%20Capabilities/Experts%20Platform.md)  

## Workflow  

* [Customer journey](./Workflow%20and%20Journeys/CustomerJourney.md)
* [Meal journey](./Workflow%20and%20Journeys/MealJourney.md)
* [Expert Workflow](./Workflow%20and%20Journeys/ExpertWorkflow.md)  

## Architectural Desision Records (ADRs)  

You can find the Architectural Decision Records [here](https://github.com/TheJedis2020/arch_katas_2020/tree/main/ADRs)  

# Directory Structure

- [ADRs](https://github.com/TheJedis2020/arch_katas_2020/tree/main/ADRs) - contains all architecture decisions and assumptions
- [diagrams](https://github.com/TheJedis2020/arch_katas_2020/tree/main/diagrams) - contains architecture diagrams (also available as a singe [PDF file](https://github.com/TheJedis2020/arch_katas_2020/blob/main/diagrams/FarmacyFood.pdf))
	- [Legend](https://github.com/TheJedis2020/arch_katas_2020/blob/main/diagrams/Legend.jpg)
	- [System Overview and Use Case Diagram](https://github.com/TheJedis2020/arch_katas_2020/blob/main/diagrams/System%20Overview%20and%20Use%20Case%20Diagram.jpg)
	- [System Component Diagram](https://github.com/TheJedis2020/arch_katas_2020/blob/main/diagrams/System%20Component%20Diagram.jpg)
	- [Data Platform Diagram](https://github.com/TheJedis2020/arch_katas_2020/blob/main/diagrams/Data%20Platform%20Diagram.jpg)
- [Key Capabilities](./Key%20Capabilities/)
- [Workflow and Journeys](./Workflow%20and%20Journeys/)

