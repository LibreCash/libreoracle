
# LibreOracle

**LibreOracle** is LibreBank ecosystem’s own oracles system.

In order to ensure emission and remission of LibreCash tokens in the LibreBank ecosystem some external data on the average ETH rate to USD is required (based on the data from large markets such as *Poloniex*, *Bitfinex* etc)

To ensure stability and independence of sources and rates delivery to LibreBank smart contracts we developed the LibreOracle system that is used along with [Oraclize oracles](https://github.com/LibreCash/contracts/tree/master/contracts/oracles)

  

## Oracle system components

1. **Currency rate acquisition module**. It consists of web-client and modules that get currency rates from markets’ APIs. At the moment there are modules for the following markets:  

- Bitfinex
- Bitstamp
- GDAX
- Gemini
- Kraken
- Poloniex
- Wex.nz

2. **Data aggregation module**. It does aggregation and averaging out initial rates data from the markets.

4. **Blockchain Ethereum module**. It communicates with the Ethereum Blockchain and ensures operation of requests monitoring and rate information entry into the Blockchain.

4. **Self-diagnostic check and logging module**. It conducts diagnosis of other modules’ operation and overall system performance check.  
In case of any problems urgent mailout takes place. It can be switched off.

5. **Remote administration and configuration module**. It is meant for remote oracles system parameters management and its stability monitoring. It can be switched off.
6. **Ethereum network smart contracts** is the point of contact between the Blockchain and the external world that informs the oracles system in case the data needs to be updated (certain variable status setting and event generation) and ensures result value storage (checking the sender of the data).

## Oracles system operation workflow

1. After the launch of the oracles system recurrent data polling of the markets starts, as well as data processing and accumulation. The data is also saved to the additional database.
2. Event and smart contract state monitoring launch.
3. If a smart contract requested data it sends up-to-date data back.

 
## Software components of the LibreOracle oracles system

1. **OracleLightnode** is a software system that takes care of getting and sending rates. Direct sending of rates to smart contract is possible, as well as indirect when the information is sent and accumulated in OracleMasternode.

2. **OracleMasternode** is a software system that interacts with (monitors and manages) OracleLightnode nodes. It is meant for service needs and oracles’ nodes management.

3. **OracleUI** is a web-client and an interface of interaction with OracleMasternode.
