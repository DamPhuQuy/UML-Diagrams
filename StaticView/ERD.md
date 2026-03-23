## 5. Entity Relationship Diagram (ERD)

**What is ERD?**

Entity Relationship Diagram, also known as ERD, ER Diagram or ER model, is a type of structural diagram for use in database design.

An ERD contains different symbols and connectors that visualize two important information: The major entities within the system scope, and the inter-relationships among these entities.

### 5.1. ERD notations

#### 5.1.1. Entity

An ERD entity is a definable thing or concept within a system

<p align="center">
    <img src="images/03-an-erd-entity.png">
</p>

#### 5.1.2. Entity Attributes

Also known as a column, an attribute is a property or characteristic of the entity that holds it.

<p align="center">
    <img src="images/04-an-erd-entity-with-entities.png">
</p>

#### 5.1.3. Primary key

Also known as PK, a primary key is a special kind of entity attribute that uniquely defines a record in a database table.

<p align="center">
    <img src="images/05-concept-of-erd-primary-key.png">
</p>

#### 5.1.4. Foreign key

Also known as FK, a foreign key is a reference to a primary key in a table.

<p align="center">
    <img src="images/06-concept-of-erd-foreign-key.png">
</p>

#### 5.1.5. Relationship

Two entities are associated with each other somehow

**Cardinality**

Cardinality defines the possible number of occurrences in one entity which is associated with the number of occurrences in another.

**One to one**

<p align="center">
    <img src="images/07-erd-one-to-one-relationship-example.png">
</p>

**One to many**

<p align="center">
    <img src="images/08-erd-one-to-many-example.png">
</p>

**Many to many**

<p align="center">
    <img src="images/09-erd-many-to-many-example.png">
</p>

#### 5.1.6. Conceptual, Logical and Physical data models

**Conceptual data model**

Conceptual ERD models the business objects that should exist in a system and the relationships between them.

<p align="center">
    <img src="images/10-conceptual-data-model-example.png">
</p>

**Logical data model**

Logical ERD is a detailed version of a Conceptual ERD.

<p align="center">
    <img src="images/11-logical-data-model-example.png">
</p>

**Physical data model**

Physical ERD represents the actual design blueprint of a relational database.

<p align="center">
    <img src="images/12-physical-data-model-example.png">
</p>

### 5.2. Guidelines for Drawing an ERD

**1. Define the Purpose**

- Be clear why you are drawing the ERD:
- System Architecture View → High-level definition of business objects.
- Database Design View → A detailed ER model ready for database creation.
- The level of detail depends on your goal. (See Conceptual, Logical, and Physical Data Models.)

**2. Set the Scope**

- Clearly define what part of the system you are modeling.
- This prevents including unnecessary or redundant entities.

**3. Identify Major Entities**

- List the core business objects (e.g., Customer, Order, Product).
- These are usually nouns in the business domain.

**4. Define Attributes**

- Add columns (properties) to each entity.
- Ensure attributes are enough to describe the entity meaningfully.

**5. Review for Completeness**

- Check if your entities and attributes are sufficient to store the required data.
- Add more entities if needed (e.g., transactional, operational, or event entities).

**6. Define Relationships**

- Establish relationships between entities with correct cardinality:
  - One-to-One (1:1)
  - One-to-Many (1:N)
  - Many-to-Many (M:N)
- Example: Customer —1:N— Order.
- Orphan entities (not linked) are allowed, though uncommon.

**7. Normalize the Data**

- Apply database normalization to:
  - Reduce redundancy.
  - Improve data integrity.
- Example:
  - Initially, Product stores manufacturer details.
  - After normalization, split into Product and Manufacturer tables.
  - Use a foreign key to link Product → Manufacturer.
