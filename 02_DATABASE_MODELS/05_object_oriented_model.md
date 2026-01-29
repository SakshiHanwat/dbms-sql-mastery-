# Object Oriented Data Model

---

## Need of Object Oriented Data Model

To represent the complex real world problems there was a need for a data model that is closely related to real world. Object Oriented Data Model represents the real world problems easily.

---

## Object Oriented Data Model

In Object Oriented Data Model, data and their relationships are contained in a single structure which is referred as object in this data model. In this, real world problems are represented as objects with different attributes. All objects have multiple relationships between them.

Basically, it is combination of Object Oriented programming and Relational Database Model as it is clear from the following figure:

**Object Oriented Data Model = Combination of Object Oriented Programming + Relational Database Model**

---

## Components of Object Oriented Data Model

*Click to enlarge*

**Basic Object Oriented Data Model**

---

### Objects

An object is an abstraction of a real world entity or we can say it is an instance of class. Objects encapsulates data and code into a single unit which provide data abstraction by hiding the implementation details from the user.

**Example:** Instances of student, doctor, engineer in above figure.

---

### Attribute

An attribute describes the properties of object.

**Example:** Object is STUDENT and its attribute are Roll no, Branch, Setmarks() in the Student class.

---

### Methods

Method represents the behavior of an object. Basically, it represents the real-world action.

**Example:** Finding a STUDENT marks in above figure as Setmarks().

---

### Class

A class is a collection of similar objects with shared structure i.e. attributes and behavior i.e. methods. An object is an instance of class.

**Example:** Person, Student, Doctor, Engineer in above figure.

```cpp
class student
{
    char Name[20];
    int roll_no;
    --
    --
    public:
    void search();
    void update();
}
```

In this example, **student** refers to class and **S1, S2** are the objects of class which can be created in main function.

---

### Inheritance

By using inheritance, new class can inherit the attributes and methods of the old class i.e. base class.

**Example:** Classes Student, Doctor and Engineer are inherited from the base class Person.

---

## Advantages of Object Oriented Data Model

* Codes can be reused due to inheritance.
* Easily understandable.
* Cost of maintenance can reduced due to reusability of attributes and functions because of inheritance.

---

## Disadvantages of Object Oriented Data Model

* It is not properly developed so not accepted by users easily.
