## What is Hbase ?

HBase is an open-source, column-oriented distributed database system in a Hadoop environment. Initially, it was Google Big Table, afterward, it was re-named as HBase and is primarily written in Java.  Apache HBase is needed for real-time Big Data applications.

### HBase Unique Features

1. HBase is built for low latency operations
2. HBase is used extensively for random read and write operations
3. HBase stores a large amount of data in terms of tables
4. Provides linear and modular scalability over cluster environment
5. Strictly consistent to read and write operations
6. Automatic and configurable sharding of tables
7. Automatic failover supports between Region Servers
8. Convenient base classes for backing Hadoop MapReduce jobs in HBase tables
9. Easy to use Java API for client access
10. Block cache and Bloom Filters for real-time queries
11. Query predicate pushes down via server-side filters.

### Hbase Architecture

HBase is a column-oriented database and data is stored in tables. The tables are sorted by RowId.

#### Storage Mechanism in Hbase

Coming to HBase the following are the key terms representing table schema

Table: Collection of rows present.
Row: Collection of column families.
Column Family: Collection of columns.
Column: Collection of key-value pairs.
Namespace: Logical grouping of tables.
Cell: A {row, column, version} tuple exactly specifies a cell definition in HBase.

Each table must have an element defined as Primary Key.
Row key acts as a Primary key in HBase.
Any access to HBase tables uses this Primary Key



