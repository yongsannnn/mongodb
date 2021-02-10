### Create a new database
"use" the database as if it exists. 
"use animal_shelter"

This is the procedure how the database gets collection
Mongo will automaticaly save the new database when...
*It has at least ONE collection
*And that collection contain at least ONE document

### Insert into a collection
```
db.<collection name>.insert({...})
```

Insert a new dog named Fluffy into the system:
``` 
db.animals.insert({
    "name": "Fluffy",
    "age": 3,
    "breed": "Golden Retriever",
    "species": "Dog"
})
``` 

Once we done this step, if the database has not been save. It will now be saved. 

### Insert many into a document
``` 
db.animals.insertMany([
    {
        "name" : "Muffin",
        "age" : 10,
        "breed" : "Munchkin",
        "species" : "Cat" 
    },
    {
        "name" : "Socks",
        "age" : 3,
        "breed" : "Scottish Fold",
        "species" : "Cat"
    }
])
```


## Update an exisiting documents

### Update a document by its object id

#### "Prestige Method" aka PUT
Kill the old one, update a new one.
Replace entire document, but same identity. Keep old ID.
First object is the criteria object.
Second object is the data that you want to upload.

```
db.students.update({
    "_id" : ObjectId("60234c45b7dc9b5748b6a196")
},{
    "name" : "James Verses",
    "age" : 15,
    "subjects": ["Transfiguration","Alchemy"],
    "date_enrolled": new Date("2015-06-15")
})
```

#### "Patch Method"
Only change the part that you want to change
By using $set you can update the KEYS of the document. 
```
db.students.update({
    "_id" : ObjectId("60234c45b7dc9b5748b6a196"),
},{
    "$set" : {
        "age" : 16
    }
})
```

### Update Many
Update all the students whose age 13 or higher with a FYP true. 
```
db.students.updateMany({
    "age" : {
        "$gte" : 13
    }
},{
    "$set" : {
        "fyp" : true
    }
})

```


### Delete
db.students.remove({
    "_id": ObjectId("60234c45b7dc9b5748b6a197"),
})


## Manage sub-documents
How to add something into an array.
Inserting an animal with an array first.
```
db.animals.insert({
    "name" : "Cookie",
    "age" : 1,
    "breed" : "Baegle",
    "species" : "Dog",
    "tags" : ["Playful", "Energetic", "Young"] 
})
```

### Push to the back of the tags array for Cookie
```
db.animals.update({
    "_id" : ObjectId("60235930b7dc9b5748b6a198"),
},{
    "$push": {
        "tags" : "Good with kids"
    }
})
```

### Remove specific item from an array

```
db.animals.update({
    "_id" : ObjectId("60235930b7dc9b5748b6a198"),
},{
    "$pull": {
        "tags" : "Young"
    }
})
```

### Updating sub-documents
Adding a sub document to cookie first
using $set
```
db.animals.update({
    "_id" : ObjectId("60235930b7dc9b5748b6a198"),
},{
    "$set":{
        "vet": {
            "name" : "Dr Jay Lim",
            "contact" : 81238123,
            "address" : "Clementi Ave 1"
        }
    }
})
```