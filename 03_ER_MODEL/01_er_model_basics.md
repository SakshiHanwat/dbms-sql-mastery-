# Basic Concepts of ER Model in DBMS

As we described in the tutorial Database models, Entity-relationship model is a model used for design and representation of relationships between data.

The main data objects are termed as Entities, with their details defined as attributes, some of these attributes are important and are used to identity the entity, and different entities are related using relationships.

In short, to understand about the ER Model, we must understand about:

* Entity and Entity Set
* What are Attributes? And Types of Attributes.
* Keys
* Relationships

Let's take an example to explain everything. For a School Management Software, we will have to store Student information, Teacher information, Classes, Subjects taught in each class etc.

---

## ER Model: Entity and Entity Set

Considering the above example, Student is an entity, Teacher is an entity, similarly, Class, Subject etc are also entities.

An Entity is generally a real-world object which has characteristics and holds relationships in a DBMS.

If a Student is an Entity, then the complete dataset of all the students will be the Entity Set.

---

## ER Model: Attributes

If a Student is an Entity, then student's roll no., student's name, student's age, student's gender etc will be its attributes.

An attribute can be of many types, here are different types of attributes defined in ER database model:

* **Simple attribute**: The attributes with values that are atomic and cannot be broken down further are simple attributes. For example, student's age.
* **Composite attribute**: A composite attribute is made up of more than one simple attribute. For example, student's address will contain house no., street name, pincode etc.
* **Derived attribute**: These are the attributes which are not present in the whole database management system, but are derived using other attributes. For example, average age of students in a class.
* **Single-valued attribute**: As the name suggests, they have a single value.
* **Multi-valued attribute**: They can have multiple values.

---

## ER Model: Keys

If the attribute roll no. can uniquely identify a student entity, amongst all the students, then the attribute roll no. will be said to be a key.

Following are the types of Keys:

* Super Key
* Candidate Key
* Primary Key

We have covered Keys in details here in Database Keys tutorial.

---

## ER Model: Relationships

When an Entity is related to another Entity, they are said to have a relationship. For example, a Class Entity is related to Student entity, because students study in classes, hence this is a relationship.

Depending upon the number of entities involved, a degree is assigned to relationships.

For example, if 2 entities are involved, it is said to be Binary relationship, if 3 entities are involved, it is said to be Ternary relationship, and so on.

---

In the next tutorial, we will learn how to create ER diagrams and design databases using ER diagrams.
