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

Use the inspections collection from the sample_training database for the questions below
1.Find all businesses which has violations issued
2.Find all business which has violations, and are in the city of New York.
3.Count how many businesses there in the city of New York
4.Count how many businesses there are in the city of Ridgewood and does not have violations (hint: google for "not equal" in Mongo)


```
1. 
db.inspections.find({
    "result" : "Violation Issued"
},{}).pretty()
``` 
```
2.
db.inspections.find({
    "result" : "Violation Issued",
    "address.city" : "NEW YORK" 
},{}).pretty()
```
```show
3.
db.inspections.find({
    "address.city" : "NEW YORK" 
},{}).count()

ans; 18279
```
```
4.
db.inspections.find({
    "address.city" : "Ridgewood",
    "result": "No Violation Issued" 
},{}).count()

ans: 11
```