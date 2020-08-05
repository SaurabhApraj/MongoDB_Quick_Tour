# MongoDB Quick Tour

## Comparison with SQL
```bash
Table      - Collection
Row        - Document
Column     - Field
Table Join - Embedded Document
```

## To Start Server
```bash
mongod
```

## Show all databases

```bash
show dbs
```

## Create database or use database
```bash
use students
```

## Create Collection
```bash
db.createCollection("student")
```

## Show current database
```bash
db
```

## Drop Database
```bash
db.dropDatabase()
```

## To check no. of Collections
```bash
show collections
```

## Drop Collection
```bash
db.student.drop()
```

## Inserting values in collection
#### .insertOne()
```bash
db.student.insertOne({
  _id:1,
  name:"abc",
  class:10,
  age:16
})
```
#### .insertMany()
##### .insertMany( [ {} , {} , {} , {} ] )
```bash
db.student.insertMany([
  {_id:2,name:"pqr",class:12,age:18},
  {_id:3,name:"xyz",class:8,age:14},
  {_id:4,name:"pqr",class:10,age:16},
  {_id:5,name:"abc",class:12,age:18}
])
```

## Read Collection
```bash
db.student.find()
```
### Pretty Format
```bash
db.student.find().pretty()
```
## .find(Query,Projection)
## Query
### Comparison Query Operators
#### $eq - equal to
```bash
db.student.find({class:{$eq:10}})
```
#### $gt - greater than
```bash
db.student.find({age:{$gt:14}})
```
#### $gte - greater than or equal to
```bash
db.student.find({age:{$gte:14}})
```
#### $in - in
```bash
db.student.find({age:{$in:[18,14]}})
```
#### $lt - less than
```bash
db.student.find({age:{$lt:18}})
```
#### $lte - less than or equal to
```bash
db.student.find({age:{$lte:18}})
```
#### $ne - not equal to
```bash
db.student.find({age:{$ne:18}})
```
#### $nin - not in
```bash
db.student.find({name:{$nin:["abc"]}})
```


### Logical Query Operators
#### $and ,$or ,$not ,$nor 
```bash
db.student.find({$and:[{name:"abc"},{class:12}]})
```
```bash
db.student.find({$or:[{name:"abc"},{class:10}]})
```
```bash
db.student.find({age:{$not:{$lt:18}}})
db.student.find({age:{$not:{$gt:20}}})
```
```bash
db.student.find({$nor:[{name:"abc"},{class:10}]})
```


## Projection
#### 0 or 1
```bash
db.student.find({name:{$eq:"abc"}},{class:1})
```
```bash
db.student.find({name:{$eq:"abc"}},{class:0})
```

## Update Collection
#### .updateOne()
```bash
db.student.updateOne({_id:1},{$set:{age:21}})
```
#### .updateMany()
```bash
db.student.updateMany({name:"abc"},{$set:{age:20}})
```

## Delete Collection
```bash
db.student.deleteOne({_id:1})
```

## Limit
#### It will display first 2 fields
```bash
db.student.find().limit(2)
```

## Count
```bash
db.student.find().count()
```

## Sort
### ascending = 1 , descending = -1
```bash
db.student.find().sort({age:1})
db.student.find().sort({age:-1})
```

## Chaining
```bash
db.student.find().limit(2).sort({age:1}).pretty()
```
