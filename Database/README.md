# Cloud Databases

AWS manages the underlying service/compute layer (this includes patching, installing, backups etc) you are only charged for the usage of the database and not for the setting up of that database.

Security is the responsibility of the user that owns the database.


## Amazon Relational Tables

Generally structured tables (SQL), relational tables use schema to describe tables within the database. 

<img src="./pics/relationvsnonrelational.png" />


A non-relational database just stores the data. A relational database stores the data and provides a processing engine. Non-relational databases suit situations where you just need a fast, secure, highly available data store which can manage many different types of objects. Relational databases suit data storage requirements where you have complex relationships between tables that might require a processing engine within the database to manage the processing of queries and updates

# NoSQL

## Amazon DynamoDB

Amazon DynamoDB is a fully managed cloud native database, and it's designed for managing high volumes of records and transactions, without you needing to provision capacity up front. It supports both document and key store objects.

## Amazon Elasticache

This is a managed cache that can be used to support Amazon RDS and Non-RDS databases by storing data that is recently accessed.

A cache is a temporary copy of frequently read data and is used to reduce the load on a database.

Elasticache comes in 2 variations of database engines: Redis and Memcache. The difference; Memcache for simplicity and speed, redis for features.

<img  src="./pics/redisvsmemcache.png" />

## Amazon Neptune

This is a graph database optimized for storing data relationships and querying a graph (similar to Neo4j)

## Amazon RDS

Some advantages of amazon RDS:
- The ability to scale components 
- Automatic backs and patching
- High availability (run databases in multiple AZ's)
- Automatic failover and recovery

### Amazon RDS Services

Some key SQL databases offered by Amazon as a service

- MySQL
- Microsoft SQL Server
- Oracle Database
- MariaDB
- PostgreSQL
- Amazon Aurora

### When to use Amazon RDS

- No unfront cost to create the instance
- Highly available
- Only pay for the time used

### When to use Amazon NoSQL

- Throughput scaling
- Burst scaling

## Big table of use-cases:

<img src="./pics/awsdbusecases.png"/>

## When to use RDS Multi-AZ & Read Replicas

### RDS Multi-AZ
Multi-AZ or multiple availability zones will mean Amazon will create multiple instances of our service. When talking about an RDS Multi-AZ it will create replicas of our database in multiple zones.

The replication of the data between instances happens synchronously. RDS uses a failover mechanism, the failover mechanism is activated automatically by AWS when the primary instance fails and the secondary instance becomes master (DNS is configured). The is true for: Oracle, MySQL, MariaDB and PosgreSQL. 

When does a failover happen?
- Patching or maintenance
- Host failure
- AZ faulure
- Reboot
- DB instance class modified

SQL Server Multi-AZ is achieved by SQL server mirroring and since SQL instances all use the same DNS record the physical network address is updated on failover

Amazon Aurora DB clusters are fault tolerant, which is designed to maintain the data to withstand a complete failure of an availability zone. This is achieved within the cluster by copying and replicating data across different instances in different AZs within a single region. Should a failure occur of the primary instance, then Aurora can automatically provision and launch a new primary instance.


### Read Replicas
_Only availible for MariaDB, PosgreSQL and MySQL_

Read Replicas are snapshots of the database at a point in time traffic from the primary instance can be redirected to to an instance running the read-replica to help ease traffic on the primary instance.

- You can deploy multiple read replica instances
- It is possible to chain read-replicas (Only 4 Layers)

## DynamoDB

DynamoDB is a fully managed SQL database service, user are charged for the prevision throughput reserved and the amount of data stored. Prevision throughput refers to the level of read and write capacity reserved for your table.

Data can be looked by the primary key or the use of indexes, dynamodb tables are schema-less and the only requirement of data stored in the table is that it must contain a primary key.

- Fully managed by AWS
- Flexible Schema
- Designed for high availability (Automatically replicated over 3 AZ's) 
- Designed to be fast 
- "infinitely" scalable
- Data is only eventually consistent
- Non Flexible query language
- Limited data types (Strings, boolean, numbers and binary only. _**no date type**_)
- Limited to 400kb max record size
- Limited to 10 indexes per table
- Performance is limited to the set prevision throughput
