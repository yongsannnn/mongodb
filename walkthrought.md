## See all databases associated with the user database
```
show databases; 
```

## To select a specicfic data base, use "use"
```
use sample_airbnb;
```
*If you "use" a data base which name does not exist, Mongo assume you want to create a new one. 

## See collections in a database
```
show collections;
```
This is to ensure that you are on the correction collection. 

## Check the currently selected database
```
db 
```

## Find documents from a collection

### Show all
```
db.listingsAndReviews.find()
```
* They will only show 20 records, for more type "it"


### Limit the number of documents found
Limit to the first ten documents in the collection
```
db.listingsAndReviews.find().limit(10)
```

### Format the output nicely with . pretty()
```
db.listingsAndReviews.find().pretty().limit(10)
```
* `limit()` must always be at the back.

### Projecting
* Show only certain keys from the documents
// Only show name, summary and address keys from the document.
```
db.listingsAndReviews.find({},{
    "name" : 1,
    "summary": 1,
    "address": 1
}).pretty()
``` 

#### Projecting a sub-document(i.e, objects)
```
db.listingsAndReviews.find({},{
    "name" : 1,
    "summary": 1,
    "address.street" : 1,
    "address.country": 1
}).pretty()
```

## Searching for documents by criteria
* Find all the listing that have exactly 2 beds. 
* Criteria & Projection.
```
db.listingsAndReviews.find({
    "beds" : 2
},{
    "name": 1,
    "address": 1,
    "beds": 1
}).pretty()
```

* Find all the listings that have exactly 2 beds and 2 bedrooms

```
db.listingsAndReviews.find({
    "beds": 2,
    "bedrooms": 2
},{
    "name": 1,
    "address.country": 1,
    "beds": 1,
    "bedrooms": 1
}).pretty()
```

* Find by country
```
db.listingsAndReviews.find({
    "address.country": "Brazil"
},{
    "name":1,
    "address.country":1,
    "beds": 1,
    "bedrooms":1,
}).pretty()
```

* Count number of results
```
db.listingsAndReviews.find({
    "address.country": "Brazil"
},{
    "name":1,
    "address.country":1,
    "beds": 1,
    "bedrooms":1,
}).count()
```

* Find and project with the criteria (country Brazil, 2 beds and 2 bedrooms.)
```
db.listingsAndReviews.find({
    "address.country": "Brazil",
    "beds" : 2,
    "bedrooms" : 2
}, {
    "name": 1,
    "address.country": 1,
    "beds": 1,
    "bedrooms":1,
}).pretty()
```


### Find by Inequality
When there is a $, it means special. $gt means greater than. $gte means greater than equal to
```
db.listingsAndReviews.find({
    "beds": {
        "$gt": 3
    }
},{
    "name":1,
    "beds":1
})
```

* Find all listing that have 3 or more beds $gte
```
db.listingsAndReviews.find({
    "beds": {
        "$gte": 3
    }
},{
    "name":1,
    "beds":1
})
```

* Find all listings that have less than 6 beds $lt
```
db.listingsAndReviews.find({
    "beds": {
        "$lt": 6
    }
},{
    "name":1,
    "beds":1
})
```

* Find all listings that have 3 to 6 beds using multiple Inequality.
db.listingsAndReviews.find({
    "beds": {
        "$gte": 3,
        "$lt": 6
    }
},{
    "name":1,
    "beds":1
})


### Find by elements within an array
Find all listing that include "Pets Allowed" in the array of amenities. 
```
db.listingsAndReviews.find({
    "amenities":"Pets allowed"
},{
    "name": 1,
    "amenities": 1
}).pretty()
```

Find all listing that have *both* "Pets allowed" and "Pets live on this property".
```
db.listingsAndReviews.find({
    "amenities":{
        "$all":["Pets allowed", "Pets live on this property"]
    }
},{
    "name": 1,
    "amenities":1
}).pretty()
```

Find all listings that have either wifi or internet
```
db.listingsAndReviews.find({
    "amenities":{
        "$in":["Wifi", "Internet"]
    }
},{
    "name":1,
    "amenities": 1
}).pretty()
```

Find all listings that have been reviewed by the id: 6184569
```
db.listingsAndReviews.find({
    "reviews":{
        "$elemMatch": {
            "reviewer_id": "6184569"
        }
    }
},{
    "name":1,
    "reviews": {
        "elemMatch":{
            "reviewer_id":"6184569"
        }
    }
}).limit(5).pretty()
```

use $ne : value in criteria to show all that does not have 