# Network Model in DBMS

The Network Model in a Database Management System (DBMS) is a data model that allows the representation of many-to-many relationships in a more flexible and complex structure compared to the Hierarchical Model. It uses a graph structure consisting of nodes (entities) and edges (relationships) to organize data, enabling more efficient and direct access paths.

## What is Network Model?

This model was formalized by the Database Task group in the 1960s. This model is the generalization of the hierarchical model. This model can consist of multiple parent segments and these segments are grouped as levels but there exists a logical association between the segments belonging to any level. Mostly, there exists a many-to-many logical association between any of the two segments. We called graphs the logical associations between the segments. Therefore, this model replaces the hierarchical tree with a graph-like structure, and with that, there can more general connections among different nodes. It can have M: N relations i.e, many-to-many which allows a record to have more than one parent segment. Here, a relationship is called a set, and each set is made up of at least 2 types of record which are given below:

* An owner record that is the same as of parent in the hierarchical model.
* A member record that is the same as of child in the hierarchical model.

## Structure of a Network Model

A Network data model

A Network data model

In the above figure, member TWO has only one owner 'ONE' whereas member FIVE has two owners i.e, TWO and THREE. Here, each link between the two record types represents 1 : M relationship between them. This model consists of both lateral and top-down connections between the nodes. Therefore, it allows 1: 1, 1 : M, M : N relationships among the given entities which helps in avoiding data redundancy problems as it supports multiple paths to the same record. There are various examples such as TOTAL by Cincom Systems Inc., EDMS by Xerox Corp., etc.

## Example : Network model for a Finance Department

Below we have designed the network model for a Finance Department:

Network model of Finance Department.

Network model of Finance Department.

So, in a network model, a one-to-many (1: N) relationship has a link between two record types. Now, in the above figure, SALES-MAN, CUSTOMER, PRODUCT, INVOICE, PAYMENT, INVOICE-LINE are the types of records for the sales of a company. Now, as you can see in the given figure, INVOICE-LINE is owned by PRODUCT & INVOICE. INVOICE has also two owners SALES-MAN & CUSTOMER.

Let's see another example, in which we have two segments, Faculty and Student. Say that student John takes courses both in CS and EE departments. Now, find how many instances will be there?

For the above example, a student's instance can have at least 2 parent instances therefore, there exist relations between the instances of students and faculty segment. The model can be very complex as if we use other segments say Courses and logical associations like Student-Enroll and Faculty-course. So, in this model, a student can be logically associated with various instances of Faculties and Courses.

## Advantages of Network Model

* This model is very simple and easy to design like the hierarchical data model.
* This model is capable of handling multiple types of relationships which can help in modeling real-life applications, for example, 1: 1, 1: M, M: N relationships.
* In this model, we can access the data easily, and also there is a chance that the application can access the owner's and the member's records within a set.
* This network does not allow a member to exist without an owner which leads to the concept of Data integrity.
* Like a hierarchical model, this model also does not have any database standard,
* This model allows to represent multi parent relationships.

## Disadvantages of Network Model

* The schema or the structure of this database is very complex in nature as all the records are maintained by the use of pointers.
* There's an existence of operational anomalies as there is a use of pointers for navigation which further leads to complex implementation.
* The design or the structure of this model is not user-friendly.
* This model does not have any scope of automated query optimization.
* This model fails in achieving structural independence even though the network database model is capable of achieving data independence.

## Features of Network Model in DBMS

* **Data Relationship Representation:** The network model uses a graph structure to represent data relationships. It allows many-to-many relationships, providing greater flexibility in how data is connected.
* **Records and Sets:** Data in a network model is organized into records and sets. Records are similar to rows in a relational table, and sets are used to define relationships between records, akin to links in a graph.
* **Owner-Member Relationships:** The network model defines data relationships using owner-member pairs. An owner record can be linked to multiple member records, and a member record can belong to multiple owner records, facilitating complex relationships.
* **Navigational Access:** The network model supports navigational data access, where records are accessed through predefined paths. This is different from relational models, which use declarative query languages like SQL.
* **Hierarchical and Non-Hierarchical Structures:** The network model can represent both hierarchical (tree-like) and non-hierarchical (graph-like) structures, providing flexibility in data modeling.

## Operations on Network Model in DBMS

* **Insertion:** Adding new records and establishing owner-member relationships.
* **Deletion:** Removing records and maintaining data integrity by handling related records and relationships.
* **Update:** Modifying existing records and relationships between records.
* **Traversal:** Navigating through the network structure to access related records using predefined paths.
* **Search:** Retrieving specific records based on criteria by navigating the network structure.

## Difference Between the Network Model and the Hierarchical Model

| Feature        | Hierarchical Model                                | Network Model                                        |
| -------------- | ------------------------------------------------- | ---------------------------------------------------- |
| Structure      | Tree-like structure                               | Graph structure                                      |
| Relationships  | One-to-many (single parent, multiple children)    | Many-to-many (multiple parents and children)         |
| Flexibility    | Less flexible                                     | More flexible                                        |
| Data Access    | Single access path                                | Multiple access paths                                |
| Redundancy     | Higher redundancy due to rigid hierarchy          | Lower redundancy due to shared relationships         |
| Complexity     | Simpler to design and implement                   | More complex to design and manage                    |
| Usage Scenario | Suitable for simple, hierarchical data structures | Suitable for complex, interconnected data structures |
| Efficiency     | Efficient for hierarchical traversal              | Efficient for complex queries and data retrieval     |
| Example        | Organizational chart                              | Telecommunications network                           |

## Conclusion

The network model in DBMS offers a flexible way to represent complex data relationships through its graph-based structure. While it allows for many-to-many relationships and more intricate data connections compared to the hierarchical model, it also requires more sophisticated navigational access methods. Understanding its features and operations helps in leveraging its capabilities for scenarios that involve complex data interactions.
