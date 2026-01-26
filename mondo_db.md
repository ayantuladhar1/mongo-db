# Mongo DB
MongoDB is a cross-platform, document oriented database that provides, high performance, high availability, and easy scalability. MongoDB works on concept of collection and document.

## Database
Database is a physical container for collections. Each database gets its own set of files on the file system. A single MongoDB server typically has multiple databases.

## Collection
Collection is a group of MongoDB documents. It is the equivalent of an RDBMS table. A collection exists within a single database. Collections do not enforce a schema. Documents within a collection can have different fields. Typically, all documents in a collection are of similar or related purpose.

## Document
A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection's documents may hold different types of data.

## RDBMS vs MongoDB
|RDBMS|MongoDB|
|-----|-------|
|Database|Database|
|Table|Collection|
|Tuple/Row|Document|
|Column|Field|
|Table Join| Embedded Documents|
|Primary Key| Primary Key (Default key _id provided by MongoDB itself)|

## Sample Document
Following example shows the document structure of a blog site, which is simply a comma separated key value pair.
```json
{
   _id: ObjectId(7df78ad8902c)
   title: 'MongoDB Overview', 
   description: 'MongoDB is no sql database',
    tags: ['mongodb', 'database', 'NoSQL'],
   likes: 100, 
   comments: [	
      {
         user:'user1',
         message: 'My first comment',
         dateCreated: new Date(2011,1,20,2,15),
         like: 0 
      },
      {
         user:'user2',
         message: 'My second comments',
         dateCreated: new Date(2011,1,25,7,45),
         like: 5
      }
   ]
}
```
_id is a 12 bytes hexadecimal number which assures the uniqueness of every document. You can provide _id while inserting the document. If you don’t provide then MongoDB provides a unique id for every document. These 12 bytes first 4 bytes for the current timestamp, next 3 bytes for machine id, next 2 bytes for process id of MongoDB server and remaining 3 bytes are simple incremental VALUE.

## Advantages of MongoDB over RDBMS
Any relational database has a typical schema design that shows number of tables and the relationship between these tables. While in MongoDB, there is no concept of relationship.
* Schema less − MongoDB is a document database in which one collection holds different documents. Number of fields, content and size of the document can differ from one document to another.
* Structure of a single object is clear.
* No complex joins.
* Deep query-ability. MongoDB supports dynamic queries on documents using a document-based query language that's nearly as powerful as SQL.
* Tuning.
* Ease of scale-out − MongoDB is easy to scale.
* Conversion/mapping of application objects to database objects not needed.

## Why Use MongoDB?
* Document Oriented Storage − Data is stored in the form of JSON style documents.
* Index on any attribute
* Replication and high availability
* Auto-Sharding
* Rich queries
* Fast in-place updates

## Where to Use MongoDB?
* Big Data
* Content Management and Delivery
* Mobile and Social Infrastructure
* User Data Management
* Data Hub

## Data Modeling
Data in MongoDB has a flexible schema.documents in the same collection. They do not need to have the same set of fields or structure Common fields in a collection’s documents may hold different types of data.

## Data Model Design
MongoDB provides two types of data models: — Embedded data model and Normalized data model. Based on the requirement, you can use either of the models while preparing your document.

## Embedded Data Model
In this model, you can have (embed) all the related data in a single document, it is also known as de-normalized data model.
For example, assume we are getting the details of employees in three different documents namely, Personal_details, Contact and, Address, you can embed all the three documents in a single one as shown below −
```json
{
	_id: ,
	Emp_ID: "10025AE336"
	Personal_details:{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26"
	},
	Contact: {
		e-mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	},
	Address: {
		city: "Hyderabad",
		Area: "Madapur",
		State: "Telangana"
	}
}
```

## Normalized Data Model
In this model, you can refer the sub documents in the original document, using references. For example, you can re-write the above document in the normalized model as:
```json
Employee:
{
	_id: <ObjectId101>,
	Emp_ID: "10025AE336"
}
Personal_details:
{
	_id: <ObjectId102>,
	empDocID: " ObjectId101",
	First_Name: "Radhika",
	Last_Name: "Sharma",
	Date_Of_Birth: "1995-09-26"
}
Contact:
{
	_id: <ObjectId103>,
	empDocID: " ObjectId101",
	e-mail: "radhika_sharma.123@gmail.com",
	phone: "9848022338"
}
Address:
{
	_id: <ObjectId104>,
	empDocID: " ObjectId101",
	city: "Hyderabad",
	Area: "Madapur",
	State: "Telangana"
}
```

## Data Types
* String − This is the most commonly used datatype to store the data. String in MongoDB must be UTF-8 valid.
* Integer − This type is used to store a numerical value. Integer can be 32 bit or 64 bit depending upon your server.
* Boolean − This type is used to store a boolean (true/ false) value.
* Double − This type is used to store floating point values.
* Min/ Max keys − This type is used to compare a value against the lowest and highest BSON elements.
* Arrays − This type is used to store arrays or list or multiple values into one key.
* Timestamp − timestamp. This can be handy for recording when a document has been modified or added.
* Object − This datatype is used for embedded documents.
* Null − This type is used to store a Null value.
* Date − This datatype is used to store the current date or time in UNIX time format. You can specify your own date time by creating object of Date and passing day, month, year into it.
* Object ID − This datatype is used to store the document’s ID.
