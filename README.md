# MongoDB-Query-Practice


## Import CSV data

(sample data used here is from USGS Earthquake Hazards Program http://earthquake.usgs.gov/earthquakes/search)

$ cd mongodb

$ ./bin/mongoimport --db data_for_test --collection earthquake_2008 --type csv --headerline --file /sample_data/Earthquake_2008.csv

(--drop argument)


## Simple query

List the databases, select one database, and list the collections(tables) in the database selected.

```
show dbs

use data_for_test

show collections
```

Return how many documents (rows) there are in the collection (table) in which we're interested.

```
db.earthquake_2008.count()

```

Select one document in which the variable 'mag' is bigger than 7.

```
db.earthquake_2008.findOne({'mag':{$gt:7}})
```

Select all the documents in which the variable 'mag' is less than 5.

```
db.earthquake_2008.find({"mag":{$lt:5}})
```

Select all the documents in which the variable 'mag' is less than 5. Additionally, we only return the variables "mag", "time", and "place".

```
db.earthquake_2008.find({"mag":{$lt:5}}, {"mag":1, "time":1, "place":1})
```

Select variables "mag", "time" and "place" (It's empty in the first {}, so there is no selection condition). Then we sort ascently and only return the first 5 documents.

```
db.earthquake_2008.find({},{"mag":1, "time":1, "place":1}).sort({"mag":1}).limit(5)
```



## Reference

[1] https://docs.mongodb.org/manual/reference/program/mongoimport/

[2] https://docs.mongodb.org/manual/reference/program/mongoexport/