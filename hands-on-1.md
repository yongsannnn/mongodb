1. Use sample_trianing database

2. Project company name and year founded and find by criteria below
    a. All companies founded in year 2006
    b. All companies founded after the year 2000
    c. All companies founded between the year 1900 and 2010

3. Project the coy name, valuation amth and the valuation currency of it's IPO, and find by following criteria
    a. All companies with valuation amount higher than 100 mil
    b. All coy with valuation amt higher than 100mil and currency being USD



2a.
```
db.companies.find({
    "founded_year": 2006 
},{
    "name": 1,
    "founded_year":1
}).pretty()
```

2b. 
```
db.companies.find({
    "founded_year": {
        "$gt" : 2000
    }
},{
    "name": 1,
    "founded_year":1
}).pretty()
```

2c.
```
db.companies.find({
    "founded_year": {
        "$gte" : 1900,
        "$lte" : 2010
    }
},{
    "name": 1,
    "founded_year":1
}).pretty()
```


3a.
```
db.companies.find({
    "ipo.valuation_amount": {
        "$gt" : 100000000
    }
},{
    "name": 1,
    "ipo.valuation_amount": 1,
    "ipo.valuation_currency_code": 1
}).pretty()
```

3b.
``` 
db.companies.find({
    "ipo.valuation_amount": {
        "$gt" : 100000000
    },
    "ipo.valuation_currency_code" : "USD"
},{
    "name": 1,
    "ipo.valuation_amount": 1,
    "ipo.valuation_currency_code": 1
}).pretty()
``` 