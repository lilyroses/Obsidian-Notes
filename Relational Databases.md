# Relational Databases

*See also: [[SQL]]*


---

## Terminology


- **Attributes:** (AKA **field**)
	- *Column names* that represent **entity** information
	- Examples: first name, last name, SSN, etc.

- **DBMS:** Database management system
	- Example DBMS: SQL Server, Oracle, Microsoft Access
	- Instance of a DBMS hosts a database
	- Guarantees data accuracy/availability

- **Entity:** (AKA **record**)
	- represents a *noun*, a collection of data elements
	- Examples: employee, payroll record, and department

- **ERD:** Entity relationship diagram

- **Field:** (AKA **attribute**)
	- *Column names* that represent **entity** information
	- Examples: first name, last name, SSN, etc.

- **[[Relational Databases#Normal Forms|Normal Forms]]:** series of table design specifications for organizing data in a database
	- 5 normal forms: "First Normal Form" .... "Fifth Normal Form"
	- The higher normal form number, the more *normalized* a database is

- **[[Relational Databases#Normalization|Normalization]]:** review of **entity**/**attribute** lists to ensure that **attributes** are located in the proper tables and data redundancy is avoided

- **Record:** (AKA **entity**)
	- A noun, a collection of data elements
	- Examples: employee, payroll record, and department

- **Transactions:** collection of *updates* to a database

---

### ACID Properties

ACID properties: Ensure ==data accuracy== & ==availability== of dbms and **transactions**

- **A**TOMICITY
- **C**ONSISTENCY
- **I**SOLATION
- **D**URABILITY

---

#### Atomicity

- "All or nothing" requirement for making updates to the database
- Either all updates work, or none are implemented

---

#### Consistency

- The database must always be in a valid state
	- **Transactions** take DB from ==valid state== to ==valid state==

- All updates must conform to/enforce **referential integrity** constraints

##### Referential Integrity

- Constraints that define/control any *one-to-many* relationships between tables

---

#### Isolation

- Isolation of updates:
	- Multiple users can access & update data simultaneously

- Updates are delayed until updater's commit point is made

---

#### Durability

- Updates made by **transaction** are backed up and logged to nonvolatile devices (a database log file) 
	- Database log file 

- Database can be completely recovered/rebuilt using the database backup and the database log 

---

## Table Relationships

- One-to-many
- Many-to-many

---

### Many-to-Many


- TABLE 1: one row --> TABLE 2: many rows
- Associates **one row** in the first table to **many rows** in the second table

E.G.

- Table `QUOTE` : primary key `quote_id`
- Table `CHARACTER` : primary key `character_id`

	- 1 QUOTE can have MANY SPEAKERS (character)
	- 1 CHARACTER (speaker) can have MANY QUOTES

| quote_id | `...` |
| ---- | ---- |
| `Q001` | `...` |
| `Q002` | `...` |
| `Q003` | `...` |


| character_id | `...` |
| ---- | ---- |
| `C001` | `...` |
| `C002` | `...` |
| `C003` | `...` |



---

## Database Design 

- Make table names singular

---
### Best Practices

- Each table should have a well-defined, clear role

- KEEP TABLES SMALL AND SPECIFIC
	- A few large, significant tables may reside at core of database
	- Many smaller, auxiliary tables w/ only 2/3 columns 
	- Some tables only contain references to other tables
*ASK YOURSELF*: 

==**"If this piece of data changes, how many different places will I need to change?"**== 

Correct answer: `1`

If the answer is `> 1`, chances are you're not in **Normal Form.**


- CREATE AN **[[Relational Databases#ERD|ERD]]**

---

### Normalization

- **Normalization:** process that involves:
	- Removing data duplication
	- More clearly defining table key relationships
	- Moving toward a more idealized *normal form*

- Normalization can act as a design guide
	- Provides set of *rules* and *conditions* that identify trouble spots
	- Provides possible solutions to data reorganization for cleaner/more consistent database

- Data integrity much easier to enforce

---

#### Normal Forms

- Normal forms are specifications for database normalization
- 5 levels 
	- First Normal Form (**1NF**)
	- Second Normal Form (**2NF**)
	- .... 
	- Fifth Normal Form (**5NF**)

- Tables in the same database can be at different normal form levels

- First Normal Form

---

##### First Normal Form

VALIDATES: *Proper Table Format*

3 CONDITIONS:

1. ORDERLESS ROWS
	- Rows are isolated, stand-alone records
	- Data values between rows are independent of each other
2. UNIQUENESS
	- Every 

---

### ERD

Entity Relationship Diagrams

- ID **entities**
- ID **relationships**
- Add **attributes**
- Complete diagram