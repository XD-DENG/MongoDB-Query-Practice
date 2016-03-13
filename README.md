# MongoDB-Query-Practice


## Import CSV data

(sample data used here is from USGS Earthquake Hazards Program http://earthquake.usgs.gov/earthquakes/search)

$ cd mongodb
$ ./bin/mongoimport --db data_for_test --collection earthquake_2008 --type csv --headerline --file /sample_data/Earthquake_2008.csv

(--drop argument)

## Simple query

show dbs
use data_for_test
show collections

db.earthquake_2008.count()

db.earthquake_2008.findOne({'mag':{$gt:7}})

db.earthquake_2008.find({},{"mag":1, "time":1, "place":1}).sort({"mag":1}).limit(50)

db.earthquake_2008.find({"mag":{$lt:5}},{"mag":1, "time":1, "place":1})

db.earthquake_2008.find({"mag":{$lt:5}},{"mag":1, "time":1, "place":1}).sort({"mag":1}).count()


## Reference
[1] https://docs.mongodb.org/manual/reference/program/mongoimport/
[2] https://docs.mongodb.org/manual/reference/program/mongoexport/