# Telephone-Directory
CRUD operation
import pymongo

myclient = pymongo.MongoClient("mongodb://localhost:27017/")

#Creating a Database
db = myclient["mydatabase"]

#creating a collection
col = db["telephone"]
  
mydict = { "name": "John", "address": "Highway 37","telephone":12345 }

#Adding the data to collection
x = col.insert_one(mydict)

#to print the id for the inserted dict
print(x.inserted_id)
mydict = [{"name":"Jacob","city":"Banglore","telephone":234567},
           {"name":"Jones","city":"Chennai","telephone":345678},
           {"name":"James","city":"Hyderabad","telephone":456789},
           {"name":"Joel","city":"Goa","telephone":567890},
           {"name":"Joy","city":"Delhi","telephone":123456},
           {"name":"Jhancy","city":"Banglore","telephone":234567},
           {"name":"Jamam","city":"Chennai","telephone":13579},
           {"name":"Johnny","city":"Hyderabad","telephone":246801},
           {"name":"Janam","city":"Goa","telephone":357913},
           {"name":"Jabba","city":"Delhi","telephone":468013},
           {"name":"Jockey","city":"Hyderabad","telephone":579246},
           {"name":"Jack","city":"Goa","telephone":680134}
                     ]

x = mycol.insert_many(mydict)

#print list of the _id values of the inserted documents:
print(x.inserted_ids)

# to print all the data (retrive)

for x in mycol.find():
  print(x)
  
myquery = { "address": "Highway 37" }
newvalues = { "$set": { "city": "Bombay" } }

# Update
mycol.update_one(myquery, newvalues)

#print data after update
for x in mycol.find():
  print(x)
data = mycol.find({"city":"Bombay"})
print(data)
myquery = { "address": "Highway 37" }

# Delete
mycol.delete_one(myquery)

for x in mycol.find():
  print(x)
