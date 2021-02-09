Use the accounts document from the sample_analytics database and answer the following questions:
1.Find all accounts that have the InvestmentStock product
2.Find all accounts that have both the Commodity and InvestmentStock product
3.Find all accounts that have either Commodity OR CurrencyService product
4.Find all accounts that does not have CurrencyService product
5.Find all products have a limit of more than 1000, and offer both InvestmentStock and InvestmentFund products

Q1
```
db.accounts.find({
    "products": "InvestmentStock"
},{
    "account_id":1,
    "products":1
}).pretty()
```

Q2
``` 
db.accounts.find({
    "products": {
        "$all": ["Commodity", "InvestmentStock"]
        }
},{
    "account_id":1,
    "products":1
}).pretty()
```

Q3 
```
db.accounts.find({
    "products": {
        "$in": ["Commodity", "CurrencyService"]
    }
},{
    "account_id":1,
    "products":1
}).pretty()
```
Q4
```
db.accounts.find({
    "products": {
        "$ne" : "CurrencyService" 
    }
},{
    "account_id": 1,
    "products": 1
}).pretty()
```
This works because there is only one thing you don't want, thus NE can work
*OR* 
Don't want CurrencyService and Commodity.
```
db.accounts.find({
    "products": {
        "$nin" : ["CurrencyService","Commodity"] 
    }
},{
    "account_id": 1,
    "products": 1
}).pretty()
```

Q5
```
db.accounts.find({
    "limit": {
        "$gt": 10000
    },
    "products":{
        "$all": ["InvestmentStock", "InvestmentFund"]
    }

}, {
    "account_id":1,
    "limit": 1,
    "products":1
}).pretty()
```




