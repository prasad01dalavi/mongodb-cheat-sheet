# Mongo Database Tutorial
-- MongoDB is a NoSQL Database

-- Default Server URL: localhost:27017


## Mongo Database Commands:
```bash
# List all database:
show databases

# Create(if doesnot exist) and select database:
use database_name

# Create User
db.createUser({
	user:"prasad",
	pwd:"prasad123",
	roles:["readWrite", "dbAdmin"]
})

# Create Collection:
db.createCollection('customers')

# List all collections:
show collections

# Insert Data(Document) into the Collection:
db.customers.insert({first_name:"Prasad", last_name:"Dalavi"})

# Insert Multiple Documents:
db.customers.insert([
	{first_name:"Dan", last_name:"Bader", Gender:"Male"},
	{first_name:"Bucky", last_name:"Roberts", Profession: "Awesome Teacher"}
])

# List of Documents in a Collection:
db.customers.find()
db.customers.find().pretty()

# Update Documents with new value:
db.customers.update(
  {
    first_name:"Dan"
  }, 
  {
    first_name:"Dan",
    last_name:"Bader",
    book: "Python Tricks"
})

# Output of Above Update Query:
{
        "_id" : ObjectId("5b94dfe5b8e7141162927c09"),
        "first_name" : "Dan",
        "last_name" : "Bader",
        "book" : "Python Tricks"
}

# Update without losing earlier details:
db.customers.update({first_name:"Dan"}, {$set:{gender:"Male"}})

# Output of above $set method
{
        "_id" : ObjectId("5b94dfe5b8e7141162927c09"),
        "first_name" : "Dan",
        "last_name" : "Bader",
        "book" : "Python Tricks",
        "gender" : "Male"
}

# Removing gender field:
db.customers.update({first_name:"Dan"}, {$unset:{gender:1}})

# Output of $unset method:
{
        "_id" : ObjectId("5b94dfe5b8e7141162927c09"),
        "first_name" : "Dan",
        "last_name" : "Bader",
        "book" : "Python Tricks"
}



```
