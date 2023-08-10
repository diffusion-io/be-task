# Diffusion Back End Engineering Task

In this task, we are looking for talented individuals to demonstrate their proficiency in designing and implementing a robust API and integrating it with a database. The objective of this task is to create a trade management system that allows for efficient tracking, management, and analysis of trades, ultimately enabling the calculation of profit and loss for traders over time.

## Task

Your task is to implement an example trade management system. This trade management system should take the form of a RESTful API which allows users to make requests and open and close fictional trades.

1. <u>API Design and Implementation:</u> Create a RESTful API that will serve as the interface for interacting with the trade management system. The API should allow users to perform operations such as **executing new trades**, **updating trade details**, **retrieving trade information**, and more.

Assume for this task that a completed trade takes the form of the following JSON:
```
{
    timestamp: int
    chain: Enum
    user: address
    wallet: address
    tradeID: hex
    tradeType: Enum
    asset: Enum
    amount: int
    beforePrice: double
    executionPrice: double
    finalPrice: double
    tradedAmount: double
    executionFee: double
    transactionFee: double
}
```

where the `Enum` variables are restricted to the following values:

```
{
    chain: [ethereum, arbitrum, optimism, polygon]
    tradeType: [limitBuy, limitSell, marketBuy, marketSell]
    asset: [BTC, ETH, XRP, XLM, DOGE]
}
```

**Note:** You should pay close attention to the meaning on `limit` and `market` when using the `tradeType` variable.

You can assume for the sake of this task that all market data is random, and that execution fees and transaction fees are 30 and 50 basis points respectively.

You should develop a suite of unit and integration tests to validate the functionality of the API and the accuracy of trade calculation logic.

2. <u>Database Architecture:</u> Choose an appropriate database system and design the schema to efficiently store trade-related data. Explain carefully your chosen schema and choice of database system, and justify why this is the correct choice for the trade management system.

**Note:** You are not expected to perform a database integration as part of this task, it is sufficient to store all data in a local CSV file.
   
3. <u>Trade Calculation Logic:</u> Implement API logic to calculate the profit and loss of traders over time, when filtered by specific trade parameters. This will involve aggregating trade data, accounting for factors like entry and exit prices, quantities, and transaction costs.

**Examples:** 

- Calculating the daily profit and loss for a trader in aggregate
- Calculating the cumulative fees paid over time by a trader
- Calculating the daily profit and loss for a trader by asset traded, or trade type
   
Explain how you would optimise these calculations when the amount of trade data gets large, are there particular approaches you would take?

**Bonus:** Each trade will adjust the price of the asset, and cost the trader, this is called "slippage". Write an endpoint to calculate the cost to the trader due to slippage over time.

4. <u>Authentication and Authorization:</u> Explain how you would go about implementing secure authentication and authorization mechanisms for API endpoints to ensure that only authorized users can access and manipulate trade data. Why is this approach better than other approaches?

5. <u>Documentation:</u> Provide clear and concise documentation detailing how to use the API, including endpoint descriptions, request and response formats, and examples of API usage.
   
## Evaluation Criteria:
Your solution will be evaluated based on the following criteria:

- <u>Functionality:</u> Does the API perform the required operations accurately? Are the profit and loss calculations correct?
- <u>Code Quality:</u> Is the code well-organized, readable, and maintainable? Are best practices followed?
- <u>Database Design:</u> Is the database schema well-structured for the given requirements? Does it allow for efficient data retrieval? How does the system scale in the presence of concurrent requests?
- <u>Security:</u> Are authentication and authorization mechanisms designed effectively? Are potential security vulnerabilities addressed?
- <u>Testing:</u> Are there comprehensive tests covering various scenarios? Does the solution demonstrate robustness?
- <u>Documentation:</u> Is the API documentation clear and complete? Can a developer easily understand and use the API?
  
## Submission

Please submit your solution as a well-documented codebase, including API implementation, database schema, and any necessary setup instructions. You can also provide a brief overview of your design decisions and any challenges you encountered during development.
