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

