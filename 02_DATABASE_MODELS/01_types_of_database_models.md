# Types of Database Model

A Database model defines the logical design and structure of a database. It defines how data will be stored, accessed, and updated in a database management system.

As per your application's requirement, you can use a database model to define your database.

The database model sets the rule, relationships, constraints, etc. to define how data is stored in the database.

It's like creating a blueprint of your Database.

There are different types of Database models and each one has its own set of features.

You can define how you want to structure the application data using a database model.

In this tutorial you will learn about the 7 database model that are popularly used.

## Type of Database models

There are several different Database model types, some of them are old, while some of them are new, to cater to the new age requirements. Here is a list of the 7 popular Database models:

* Hierarchical Model
* Network Model
* Entity-relationship Model
* Relational Model
* Object-oriented Model
* NoSQL Model
* Graph Model

Let's learn about the different types of database models along with their main features and when should you use them.

## 1. Hierarchical Model

The hierarchical database model organizes data into a tree-like structure, with a single root, to which all the other data is linked.

The hierarchy starts from the Root data, and expands like a tree, adding child nodes to the parent nodes.

In this model, a child node will only have a single parent node.

This model efficiently describes many real-world relationships like the index of a book, etc.

IBM's Information Management System (IMS) is based on this model.

Data is organized into a tree-like structure with a one-to-many relationship between two different types of data, for example, one department can have many courses, many teachers, and of course many students(like shown in the diagram below).


![DBMS Components](images/Databases_and_SQL.svg)

### Advantages/Disadvantages of the Hierarchical Model

Here are a few points to mark the advantages and disadvantages of the Hierarchical database model:

* Because it has one-to-many relationships between different types of data so it is easier and fast to fetch the data.
* But the Hierarchical model is less flexible.
* And it doesn't support many-to-many relationships.

## 2. Network Model

The Network Model is an extension of the Hierarchical model.

In this model, data is organized more like a graph, and allowed to have more than one parent node.

In the network database model, data is more related as more relationships are established in this database model.

Also, as the data is more related, hence accessing the data is also easier and fast.

This database model uses many-to-many data relationships.

Integrated Data Store (IDS) is based on this database model.

This was the most widely used database model before Relational Model was introduced.

The implementation of the Network model is complex, and it's very difficult to maintain it.

The Network model is difficult to modify also.

You may want to explore this if you are developing some social networking applications, although the Graph Database model is new and is far better than the Network Database model.

![DBMS Components](images/network.png)


### Advantages of the Network Model

* It supports complex relationships
* It allows more flexibility

## 3. Entity-relationship Model

In this database model, relationships are created by dividing objects of interest into entities and their characteristics into attributes.

Different entities are related using relationships.

ER Models are defined to represent the relationships in pictorial form to make it easier for different stakeholders to understand.

This model is good to design a database, which can then be turned into tables in a relational model (explained below).

Let's take an example, If we have to design a School Database, then the Student will be an entity with attributes name, age, address, etc. As an Address is generally complex, it can be another entity with attributes street, pincode, city, etc, and there will be a relationship between them.

Relationships can also be of different types. You can learn about ER Diagrams in detail if you want to learn about entities and relationships.

### Advantages of the ER Model

* It is easy to understand and design.
* Using the ER model we can represent data structures easily.
* As the ER model cannot be directly implemented into a database model, it is just a step toward designing the relational database model.

## 4. Relational Model

In this model, data is organized in two-dimensional tables and the relationship is maintained by storing a common field.

This model was introduced by E.F Codd in 1970, and since then it has been the most widely used database model.

The basic structure of data in the relational model is tables. All the information related to a particular type is stored in rows of that table.

Hence, tables are also known as relations in the relational model.

You can design tables, normalize them to reduce data redundancy, and use Structured Query language or SQL to access data from the tables.

Some of the most popular databases are based on this database model. For example, Oracle, MySQL, etc.

![DBMS Components](images/relational_model.webp
)

### Advantages of the Relational Model

* It's simple and easy to implement.
* Poplar database software is available for this database model.
* It supports SQL using which you can easily query the data.

## 5. Object-oriented Model

In this model, data is stored in the form of objects.

The behavior of the object-oriented database model is just like object-oriented programming.

A very popular example of an Object Database management system or ODBMS is MongoDB which is also a NoSQL database.

This database model is not mature enough as compared to the relational database model.

### Advantages of the Object-oriented Model

* It can easily support complex data structures, with relationships.
* It also supports features like Inheritance, Encapsulation, etc.

## 6. NoSQL Model

The NoSQL database model supports an unstructured style of storing data.

Data is stored as documents.

The documents look more like JSON strings or Key-value based object representations.

It provides a flexible schema.

It does provide features like indexing, relationships between data, etc.

The support for data querying is limited in the NoSQL database model.

This database model is well-suited for Big data applications, real-time analytics, CMS (Content Management systems), etc.

### Advantages of the NoSQL Model

* This database model is scalable.
* This database model functions with high performance.
* The NoSQL database model can handle large volumes of data.

## 7. Graph Model

The Graph database model is based on more real-world like relationships.

Data is represented using Nodes or entities.

The nodes are related using edges.

The popular database Neo4j is based on the Graph database model.

If your application has simple data requirements, then you should not use the graph database model.

In modern applications like social networks, recommendation systems, etc. the graph database model is well-suited.

### Advantages of the Graph Model

* It handles complex relationships very well.
* In the modern world where there is so much data and the data has to be related in different ways, the graph database model is very useful.
