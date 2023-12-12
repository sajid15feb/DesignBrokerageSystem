# DesignBrokerageSystem

Problem Statment:-
In trade brokerage system, brokerage application receives huge number of requests from different users on multiple channels. These requests are always come from multiple platforms such as mobile, website or over a call etc. 
Every trade has following attributes:
1. ShareName
2. ShareQuantity
3. SharePrice
4. TraderId
5. BuyOrSell
6. TradeId (optional in case of new trade request)

In brokerage system following tasks are done in given order:
1. Validation of trade 
	- Basic validation of trade details
	- In case of Buy, check wallet balance in Broker system
	- In case of Sell, check for number of ShareQuantity in Broker system
	
2. If trade is new trade then book trade in brokerage system
	- In case of Buy, block amount in wallet
	- In case of Sell, block number of share quantity in broker system
	- Create internal Trade Id (primary key) and send trade to Share Exchange (Black Box and can be assumed that it's integration is over Messaging System such as Kafka, MQ etc.)
	- Store this trade and make it available for end users to view.	
4. If trade is already registered with broker then update/cancellation the trade details in system.	
	- In case of Buy, block/release delta amount in wallet
	- In case of Sell, block/release delta  number of share quantity in broker system
	- Send updated request to Share Exchange (Black Box and can be assumed that it's integration is over Messaging System such as Kafka, MQ etc.)
	- Update this trade and make it available for end users to view.	
3. Reporting of trade status to initiator
	- Need to give back response to initiator of trade about its acceptance, rejection and other status.
	- Need to provide mechanism to get trade details at any time based on generated Trade Id

Need to design above brokerage system to perform above mentioned tasks. Also consider below points in design:
1. High availability
2. Volume of trade requests such as 100K in an hour. 
3. Deployment strategy
4. Database and why?
5. Resiliency
6. Monitoring system
