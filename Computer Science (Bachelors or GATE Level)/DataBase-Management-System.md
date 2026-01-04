# Data Base Management Systems (DBMS)

## Bachelor Degree-Level DBMS Topics (foundational and intermediate)

### Introduction to Databases
  - Data, information, and database concepts
  - File systems vs. databases
  - DBMS architecture and components

### Data Models
  - Hierarchical, network, relational, object-oriented models
  - Entity-Relationship (ER) modeling
  - Enhanced ER models (EER)

### Relational Database Concepts
  - Relations, attributes, tuples, keys
  - Relational algebra and relational calculus
  - Normalization (1NF to BCNF, 4NF, 5NF)

### Structured Query Language (SQL)
  - DDL, DML, DCL, TCL commands
  - Joins, subqueries, views, indexes
  - Stored procedures and triggers

### Database Design
  - Conceptual, logical, and physical design
  - Functional dependencies
  - Schema refinement

### Transaction Management
  - ACID properties
    - Atomicity: All of transaction completes at once, or none applies. Incomplete transaction shall roll back upon failure.
    - Consistency: Ensures that a transaction brings the database from one valid state to another valid state. Rules, constraints, and integrity must always be preserved.
    - Isolation: Transactions occur independently without interference. Even if multiple transactions run at the same time, the final result is as if they were executed sequentially.
    - Durability: Once a transaction is committed, its changes are permanent, even if there's a system crash or power failure.
  - Concurrency control (locks, timestamps)
  - Deadlocks and recovery techniques

### Database Security
  - Authentication, authorization, and access control
  - SQL injection basics
  - Backup and recovery

### Distributed Databases (Introductory)
  - Client-server architecture
  - Replication basics
  - Fragmentation

### Emerging Topics (Introductory)
  - NoSQL basics (document, key-value, column, graph databases)
  - Cloud databases overview

## Master’s-Level DBMS Topics (advanced and research-oriented)
These emphasize advanced theory, optimization, and research directions:

### Advanced Data Models
  - Object-relational databases
  - Temporal and spatial databases
  - Multimedia databases

### Query Optimization
  - Cost-based query optimization
  - Heuristic optimization techniques
  - Indexing strategies (B-trees, hash indexes, bitmap indexes)

### Advanced Transaction Management
  - Distributed transactions
  - Two-phase commit protocol
  - Multiversion concurrency control (MVCC)

### Distributed and Parallel Databases
  - Data fragmentation and replication strategies
  - CAP theorem and consistency models
  - Parallel query processing

### Big Data and NoSQL Systems
  - MapReduce and Hadoop ecosystem
  - NewSQL systems
  - Graph databases (Neo4j, RDF, SPARQL)

### Database Security and Privacy
  - Advanced encryption techniques
  - Role-based and attribute-based access control
  - Privacy-preserving data publishing

### Data Warehousing and OLAP
  - Star and snowflake schemas
  - ETL processes
  - OLAP operations (slice, dice, roll-up, drill-down)

### Information Retrieval and Indexing
  - Full-text search
  - Inverted indexes
  - Relevance ranking

### Research-Oriented Topics
  - Semantic web and knowledge graphs
  - Blockchain databases
  - AI-driven query optimization
  - Federated databases and data integration

## References

1. [DBMS Notes by MRCET](https://mrcet.com/downloads/digital_notes/CSE/II%20Year/DBMS.pdf)
2. [DBMS Notes by KIIT](https://kp.kiit.ac.in/pdf_files/06/4th-Sem_CSE_Database-Management-System.pdf)

## Subject Topics (from [GATE 2026 CS](https://gate2026.iitg.ac.in/doc/GATE2026_Syllabus/CS_2026_Syllabus.pdf) syllabus)

ER‐model. Relational model: relational algebra, tuple calculus, SQL. Integrity constraints, normal forms. File organization, indexing (e.g., B and B+ trees). Transactions and concurrency control.