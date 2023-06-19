# SQL

A transaction has four key properties called **ACID**:

- `Atomicity` - an operation finishes entirely or the database rolls back to the prior state.
- `Consistency` - only valid transaction is saved.
- `Isolation` - transactions do not affect each other.
- `Durability` - a successfully written transaction survives permanently.

## Ways To Scale Data

### Master-Slave Replication

![master-slave](./master-slave.png)

### Master-Master Replication

![master-master](./master-master.png)

Cons for Master-Master:

- Load balancer is required to decide which node to write.
- Loosly consistent (violating ACID)and higher latency due to synchronization.

Cons for replication:

- New data could be lost before master replicates to other nodes.
- Writes could block reads when there are too many.
- More read slaves could result in replication lag.
- Additional complexity.

### Federation

![federation](./federation.png)

Splits databases by function, improving performance as less read/write traffic and less replication.

Cons

- Not effective when functions/tables are huge.
- More application logic for determining which database to write.
- More complicated for joining databases.

### Denormalization

Improves read performance at the expense of write performance, avoiding joins by duplicating data.

Cons

- Duplicated data.
- Making maintaining consistency hard.
- Performance penalty under heavy write load.

### Sharding

Please see [data partitioning](../../theories/README.md#data-partitioning) for detail.

# NoSQL

NoSQL favours availability over consistency and follows **BASE**:

- `Basically Avaliable` - guarantees availability.
- `Soft state` - the state of the system may change over time, even without any input.
- `Eventually consistency` - the system will be consistent eventually.

## Types of NoSQL

Key-Value Store

- Using hashmap for BigO(1) performance
- Good for rapidly-changing data.
- The base of document & graph stores.
- Representations: Redis, Memcached.

Document Store

- For storing data like XML, JSON or binary etc.
- Provides query tool.
- Representations: MongoDB, CouchDB.

Wide Column Store

![wide-column](./wide-column.png)

- Good for big data.
- Representations: Bigtable, HBase, Cassandra.

Graph Store

![graph store](./graph-store.png)

- Good for data with complex relationships.
- Representations: Neo4j, FlockDB,

# SQL vs NoSQL

![sql vs nosql](./sql-vs-nosql.webp)

|                | SQL                    | NoSQL                     |
| -------------- | ---------------------- | ------------------------- |
| Data Structure | structured             | semi-structured           |
| Scheme         | strict                 | flexiable                 |
| Data Relations | relational             | non-relational            |
| Joins          | need for complex joins | no need for complex joins |

## Reasons to use SQL
- Need ACID compliance.
- Structured and unchanging data.

## Reasons to use NoSQL
<!-- - Good for big data, 
- Data intensive workload, 
- High IOPS(Input/Output Operation per Second) -->

- Ever-changing data structure. Especially for rapid development.
- Storing large volume of data.
- Taking advantage of cloud services.