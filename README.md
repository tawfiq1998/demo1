#Foreign Exchange project 

is a microservice to store Foreign Exchange transactions for Bloomberg 

the structour of the microservice is as the following

##Controller layer
contains endpoint to recive the transaction request ("ForeignExchangeController").

request format should be as following (JSON Format) :

```json
{
    "fromCurrencyCode":"fromCurrencyCode" english text only,
    "toCurrencyCode":"toCurrencyCode" english text only,
    "transactionDate":"transactionDate" format ( yyyy-MM-dd'T'HH:mm:ss.SSSZZZZ),
    "dealAmount":"dealAmount" zero and positive valus only
}
```


**EXAMPLE Request : **

```json
{
    "fromCurrencyCode":"JOD",
    "toCurrencyCode":"USD",
    "transactionDate":"2020-08-24T21:49:31.702+0400",
    "dealAmount":12.0
}

```

##Service layer
validate the request and then pass the transaction to repository layer.

*checkCurrencyType validator send request to service provided by "https://apilayer.com/" 
with a monthly limit 250 request

##Repository layer
to handle DB transaction of type entity("ForeignExchangeTransaction")

##Test Cases
unit test using (JUNIT) that tests the methods EX(ValidationServiceTest calss whitch test validations methods)
