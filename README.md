# Mongo Database Cheat Sheet
-- MongoDB is a NoSQL Database

-- Default Server URL: localhost:27017


## Mongo Database Commands:
```bash
# List all database:
show databases
show dbs

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

# Find required 
db.customers.find({$or:[{first_name: "Prasad"}, {first_name: "Dan"}]}).  # OR condition
db.customers.find({age: {$lt:40}})					 # age less than 40
db.customers.find().sort({last_name: 1})                                 # sort names asc (if -1 then desc)

db.customers.find({first_name: "prasad"}).count()		 	 # Number of docs

# Note
db.customers.find({"address.city": "Pune"})				 # To find data in object

# Update Documents with new value (which will actually replace the existing record):
db.customers.update(
  {
    first_name:"Dan"
  }, 
  {
    first_name:"Dan",
    last_name:"Bader",
    book: "Python Tricks"
})

# Update/add for matched doc, without losing earlier details (without replacing):
db.customers.update({first_name:"Dan"}, {$set:{gender:"Male"}})  

# Increment operator (increments age value by 1)
db.customers.update({first_name:"Prasad"}, {$inc:{age:1}})  

# Removing gender field:
db.customers.update({first_name:"Dan"}, {$unset:{gender:1}})

# Remove document
db.customers.remove({first_name:"Prasad"})

```
