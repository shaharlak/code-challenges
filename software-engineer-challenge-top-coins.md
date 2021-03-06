# WATTx Software Engineer Challenge: **Top Coins**

### Overview

For this task, you will prototype a price list service for top crypto assets.

The service should expose a HTTP endpoint, which when fetched, displays an up-to-date list of top assets and their current prices in USD. 
* The endpoint should support `limit` parameter which indicates how many top coins should be returned.
* The output should be either `JSON` or `CSV` compatible.

Example call should look somehow like this:

```
$ curl http://localhost:6667?limit=200

Rank,	Symbol,	Price USD,
1,	BTC,	6634.41, 
2,	ETH,	370.237,
3,	XRP,	0.471636,
...	...	...
200,	DCN,	0.000269788,
```

The ranking and price information should always be up-to-date. For example let's say that Wings ranking changes from #199 to #200, the list should reflect that change.

### Data Sources

To make the challenge a bit more interesting, we ask you to:

* Use [coinmarketcap API](https://coinmarketcap.com/api/) to get the current USD prices
* Use [cryptocompare API](https://www.cryptocompare.com/api#-api-data-coinlist-) to get the current ranking information for the top 200 assets.

We know that you can get all the necessary data from either one of those but part of this challenge is to see how you deal with the problem of merging information from multiple data sources.

### Architecture

Your solution should consist of at least 3 separate services that run independently (service oriented architecture):

* Pricing Service - keeps the up-to-date pricing information
* Ranking Service - keeps the up-to-date ranking information
* HTTP-API Service - exposes a HTTP endpoint that returns the up-to-date list of 200 top coins prices.

You're free to pick any pattern for inter-service communication. We ask you to explain the rationale behind your choice in the README, some of the most well known patterns are: 

* Publish / Subscribe over a messaging bus such as RabbitMQ, NATS, MQTT
* HTTP API
* Remote Procedure Calls
* Shared Database

### Hints

- You're free to use any language and any libraries. Think about the best fit for solving the task. Remember that the next step would be a pair programming session with one of our engineers, so you need to be comfortable with the language you've choosen. At WATTx we're pretty agnostic but are using mostly `Go` and `Python`.
  - That being said, we strongly recommend that you don't use any application frameworks. We want to clearly see and understand your own style and intentions without being influenced by any conventions imposed by a framework.
- We recommend you use `docker` and `docker-compose` for orchestrating your solution.
