1.Create a new mongodb database with the name fake_school
2.Create a new collection name students
3.Add to the students collection the following documents:

Name: Jane Doe
Age: 13
Subjects: Defense Against the Dark Arts, Charms, History of Magic
Date Enrolled: 13th May 2016

Name: James Verses
Age: 14
Subjects: Transfiguration, Alchemy
Date Enrolled: 15th June 2015

Name: Jonathan Goh
Age: 12
Subjects: Divination, Study of Ancient Runes
Date Enrolled: 16th April 2017

Q1
```
use fake_school
```

Q2 
Have inserted the subjects into an array(list) for easy retrieve in future
``` 
db.students.insert([
    {
        "name" : "Jane Doe",
        "age" : 13,
        "subjects" : ["Defense Agaisnt the Dark Arts", "Charms", "History of Magic"],
        "date_enrolled": new Date("2016-05-13")
    }
])
```

Q3
``` 
db.students.insertMany([
    {
        "name" : "James Verses",
        "age" : 14,
        "subjects": ["Transfiguration","Alchemy"],
        "date_enrolled": new Date("2015-06-15")
    },
    {
        "name" : "Jonathan Goh",
        "age" : 12,
        "subjects": ["Divination","Study of Ancient Runes"],
        "date_enrolled": new Date("2017-04-16") 
    }
])
```



1.Add in the following pets:
Name: Jorden,
Age: 15
Breed: Golden Retriever
Species: dog


Name: Dash
Age: 3
Breed: Hamster
Species: Hamster


Name: Carrot
Age: 1.5
Breed: Australian Dwarf
Species: Rabbit

Q1
```
db.animals.insertMany([
    {
        "name" : "Jorden",
        "age" : 15,
        "breed" : "Golden Retriever",
        "species" : "Dog"
    },
    {
        "name" : "Dash",
        "age" : 3,
        "breed" : "Hamster",
        "species": "Hamster"
    },
    {
        "name" : "Carrot",
        "age" : 1.5,
        "breed" : "Australian Dwarf",
        "species" : "Rabbit"
    }
])
```

Q2 Change Carrot Age to 2.5
```
db.animals.update({
    "_id" : ObjectId("60235fafb7dc9b5748b6a19e"),
},{
    "$set" : {
        "age" : 2.5
    }
})
```

Q3
Replace Dash the hamster's information (using the PUT method) with the following:
Name: Dash
Age: 4.5
Breed: Winter White
Species: Hamster

```
db.animals.update({
    "_id" : ObjectId("60235fafb7dc9b5748b6a19d")
},{
    "name" : "Dash",
    "age" : 4.5,
    "breed" : "Winter White",
    "species" : "Hamster"
})
```

Q4 Delete Jorden, because it went to the rainbow bridge due to old age.
```
db.animals.remove({
    "_id" : ObjectId("60235fafb7dc9b5748b6a19c")
})
```
