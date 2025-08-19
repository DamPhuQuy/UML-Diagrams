# UML-Diagrams

# Note for learning UML diagrams

# Table of Contents

- [UML-Diagrams](#uml-diagrams)
- [Note for learning UML diagrams](#note-for-learning-uml-diagrams)
- [Table of Contents](#table-of-contents)
- [Diagrams to focus on](#diagrams-to-focus-on)
  - [1. Class Diagram (most important)](#1-class-diagram-most-important)
    - [1.1. Relationships](#11-relationships)
    - [1.2. Class Notation](#12-class-notation)
      - [1.2.1. Perspectives of class diagram](#121-perspectives-of-class-diagram)
    - [1.3. Class Diagram Example: Order System](#13-class-diagram-example-order-system)
  - [2. Use Case Diagram](#2-use-case-diagram)
    - [2.1. Key elements](#21-key-elements)
      - [2.1.1. Actor](#211-actor)
      - [2.1.2. Use Case](#212-use-case)
      - [2.1.3. Communication Link](#213-communication-link)
        - [a, Association](#a-association)
        - [b, Extends](#b-extends)
        - [c, Include](#c-include)
        - [d, Generalization (or Inheritance)](#d-generalization-or-inheritance)
      - [2.1.4. Boundary of system (or Boundary system)](#214-boundary-of-system-or-boundary-system)
- [Reference](#reference)

# Diagrams to focus on

## 1. Class Diagram (most important)

The class diagram is a central modeling technique that runs through nearly all object-oriented methods.

This diagram describes the types of objects in the system and various kinds of static relationships which exist between them.

### 1.1. Relationships

**There are three principal kinds of relationships which are important:**

- `Association`: represent relationships between instances of types (a person works for a company, a company has a number of offices.
- `Inheritance`: the most obvious addition to ER diagrams for use in OO. It has an immediate correspondence to inheritance in OO design.
- `Aggregation`: Aggregation, a form of object composition in object-oriented design.

**Others add more**

- `Composition`: often taught separately (even though technically it’s a strong form of aggregation).
- `Dependency`: important, but weaker → sometimes grouped as a subtype of “association” or omitted in beginner explanations.
- `Realization`: only appears with interfaces → some courses don’t include it in “principal” relationships.

<p align="center"> 
    <img src="images/classDiagramRelationship.png" >
</p>

**Quick Memory Hack**

- Dependency → "uses" (temporary).
- Association → "has-a" (permanent link).
- Aggregation → "has-a but independent".
- Composition → "has-a but dependent".
- Generalization → "is-a" (inheritance).
- Realization → "implements interface".

**Rate and Example:**

**1. Dependency**

- Meaning: Class A depends on B (A uses B temporarily, e.g., as a parameter, local variable).
- Strength: Weak, short-lived.
- Example:

```java
    class ReportService {
        void export(PdfExporter exporter) { ... }
        // ReportService depends on PdfExporter
    }
```

<p align="center"> 
    <img src="images/dependency.png">
</p>

**2. Association**

- Meaning: Class A has a reference to B (longer-term relationship).
- Strength: Stronger than dependency
- Example:

```java
    class Order {
        Customer customer;
        // association between Order and Customer
    }
```

**Cardinality:**

Cardinality is expressed in terms of:

- one to one
- one to many
- many to many

<p align="center"> 
    <img src="images/associations-cardinality.png">
</p>

**3. Aggregation**

- Meaning: "Has-a" relationship, but weak ownership
- Lifespan: The part can exist independently of the whole.
- Example:

```java
    class Team {
        List<Player> players;
        // Players can exist without Team
    }
```

<p align="center"> 
    <img src="images/aggregation.png">
</p>

**4. Composition**

- Meaning: “Has-a” relationship with strong ownership.
- Lifespan: If the whole is destroyed, the part is destroyed too.
- Example:

```java
    class House {
        Room[] rooms;
        // Rooms cannot exist without House
    }
```

<p align="center"> 
    <img src="images/composition.png">
</p>

**5. Generalization (or inheritance)**

- Meaning: Inheritance ("is-a" relationship).
- Example:

```java
    class Animal { }
    class Dog extends Animal { }  // Dog is an Animal
```

<p align="center"> 
    <img src="images/nheritance-in-class-diagram.png">
</p>

**6. Realization**

- Meaning: Interface implementation.
- Example:

```java
    interface Owner {
        void acquire(Property property);
        void dispose(Property property);
    }

    class Person implements Owner {
        private Property real;
        private Property tangible;
        private Property intangible;

        @Override
        public void acquire(Property property) {
            // implementation for a person
        }

        @Override
        public void dispose(Property property) {
            // implementation for a person
        }
    }

    class Corporation implements Owner {
        private Property current;
        private Property fixed;
        private Property longTerm;
        private Property intangible;

        @Override
        public void acquire(Property property) {
            // implementation for a corporation
        }

        @Override
        public void dispose(Property property) {
            // implementation for a corporation
        }
    }
```

<p align="center"> 
    <img src="images/realization.png">
</p>

### 1.2. Class Notation

**Visibility Notation:** indicate the access level of attributes and methods.

Common visibility notations include:

- `+` for public access modifier (visible to all classes)
- `-` for private access modifier (visible only within the class)
- `#` for protected access modifier (visible to subclasses)
- `~` for package or default visibility access modifier (visible to classes in the same package)

<p align="center">
    <img src="images/class-notation.png">
    <img src="images/class.png">
</p>

#### 1.2.1. Perspectives of class diagram

A diagram can be interpreted from various perspectives:

- `Conceptual`: represents the concepts in the domain
- `Specification`: focus is on the interfaces of Abstract Data Type (ADTs) in the software
- `Implementation`: describes how classes will implement their interfaces

<p align="center"> 
    <img src="images/perspective-of-class-diagram.png">
</p>

### 1.3. Class Diagram Example: Order System

<p align="center"> 
    <img src="images/class-diagram-example-order-system.png">
</p>

## 2. Use Case Diagram

- Shows how users (actors) interact with the system.
- Focus: What the system does (functional requirements), not how it does it.

<p align="center"> 
    <img src="images/use-case-diagram-annotated.png">
</p>

### 2.1. Key elements

- `Actor`: external entity (user, another system).
- `Use Case`: functionality (action) the system provides.
- `System boundary`: a box representing the system itself.
- `Relationships`:
  - `Association` (actor ↔ use case).
  - `«include»` (one use case always uses another).
  - `«extend»` (optional extension).

#### 2.1.1. Actor

- Someone interacts with use case (system function).
- Named by noun.
- Actor plays a role in the business
- Similar to the concept of user, but a user can play different roles
- For example:
  - A prof. can be instructor and also researcher
  - plays 2 roles with two systems
- Actor triggers use case(s).
- Actor has a responsibility toward the system (inputs), and Actor has expectations from the system (outputs).

<p align="center"> 
    <img src="images/actor.png">
</p>

#### 2.1.2. Use Case

- System function (process - automated or manual)
- Named by verb + Noun (or Noun Phrase).
- i.e. Do something
- Each Actor must be linked to a use case, while some use cases may not be linked to actors.

<p align="center"> 
    <img src="images/usecasebox.png">
</p>

#### 2.1.3. Communication Link

<p align="center"> 
    <img src="images/communication-links-use-case-diagram.png">
</p>

##### a, Association

- Actor ↔ Use Case connection (solid line).
- Shows communication between the actor and the system (sending/receiving messages).

##### b, Extends

- Optional/conditional behavior.
- Child use case extends the functionality of a base use case.
- Shown with a dashed arrow pointing to the base use case.
- Example: Login ← «extend» Invalid Password.

##### c, Include

- Mandatory reuse of functionality.
- Base use case always includes another use case as part of its flow.
- Shown with a dashed arrow pointing to the included (child) use case.
- Example: Checkout → «include» Payment Processing.

##### d, Generalization (or Inheritance)

- Parent-child relationship between use cases.
- Child use case is a specialized/enhanced version of the parent.
- Shown with a solid line and a hollow triangle pointing to the parent use case.

**Quick memory aid:**

- Association → actor communicates with use case.
- Extend → sometimes adds behavior.
- Include → always reuses behavior.
- Generalization → specialization of another use case.

#### 2.1.4. Boundary of system (or Boundary system)

- The system boundary represents what is inside (system functionality) vs. outside (actors).
- It usually covers the entire system as defined in the requirements.
- For large/complex systems, each module can be treated as its own system boundary.
- Example: In an ERP system, modules like Personnel, Payroll, Accounting each have their own boundary.
- The overall system boundary can also encompass all modules together to show the full system.

<p align="center"> 
    <img src="images/system-boundary.png">
</p>

# Reference

- <a href="https://www.visual-paradigm.com/guide/">Visual Paradigm</a>
- <a href="https://www.geeksforgeeks.org/system-design/unified-modeling-language-uml-introduction/">Geeks For Geeks</a>
