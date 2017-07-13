
<a name="1"></a>
# MongoDB Cheat Sheet

<a name="2"></a>
## Concept Explain
 
| Mysql         | MongoDB       |
| ------------- |:-------------:| 
| Database      | Database      |
| Table         | Collection    | 
| Record        | Document      | 


<a name="3"></a>
## Basic Operation

```bash
mongo                        # connect to localhost mongoDB with default port
mongo --host 100.100.100.100 --port 27017    # connect to the remote mongoDB
help                         # show help 
show dbs                     # check all databases
use db-test                  # switched to db db-test or create db db-test if not exist
db                           # show current database
show collections             # show all collections in current database
db.help()                    # show all available operations in current database
db.collection-name.help()    # show all available operation in current collection
```


<a name="4"></a>
## Insert & update data

```bash
db.collection-name.insert({"id": "pekingzcc", "gender": "male"})  # insert data, if data(key) exist then ignore
db.collection-name.save({"id": "pekingzcc", "gender": "male"})    # insert data, if data(key) exist then update data  
db.collection-name.update({'id':"pekingzcc"},{'$set':{'gender':"female"}},upsert=true,multi=true)      # update by the query, "upsert=true" means if data not exist then insert, "multi=true" means if query multi documents, update all of them
```


<a name="5"></a>
## Find data

```bash
db.collection-name.find()                            # find all documents
db.collection-name.findOne()                         # find the first document
db.collection-name.find({'id':'pekingzcc'}).limit(10) # find top 10 documents match the query
db.collection-name.find().sort({"name":-1})          # find all documents sorted by name desc
```

<a name="6"></a>
## Delete data

```bash
db.collection-name.drop()                     # delete collection
db.dropDatabase()                             # delete current database
db.collection-name.remove({'yy':5})           # delete a document
db.collection-name.remove()                   # delete all documents
```
