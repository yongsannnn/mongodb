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
