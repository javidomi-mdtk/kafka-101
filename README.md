Kafka:

- Stream History
- Scalable Consumption
- Immutable Data
- Highly Available
- Scalable
- Many Consumers

Open source, distributed message streaming platform
A set of components (deployables/libraries/APIs)

Core Kafka APIs:
- Producer API: publish a record to a topic.
- Consumer API: subscribe to one or more topics and process their records
- Streams API: helps to consume, transform and produce streams of record (lemonades)
- Connector API: allows to build consumers and producers that bring data from existing sources (DB, S3, MQ, etc) into Kafka and delivers data from kafka topics into other systems

![alt text](./pepe.png)
> This image is lacking Kafka Proxy and Zookeeper

Kafka cluster:
Zookeeper?
Brokers?
Key?

- Kafka doesn't care at all about key/record/message type/schema. You can send it pure bytes if you wanted (AVRO, ProtoBuff)

What's a topic?
- A topic is a category or feed name to which records/messages are published

What's a record in Kafka?
- Each record consists of a key, a value, and a timestamp.

What's the zookeeper? Why does kafka needs it?

- Kafka is run as a cluster on one or more servers that can span multiple datacenters.
- The Kafka cluster stores streams of records in categories called topics.

What's the retention period?

Publish and subscribe to streams of events
Store events in a durable way
Process streams of events as they occur

Replication:
- Fault Tolerance

Consumer Group:
- each record published to a topic is delivered to one consumer instance within each subscribing consumer group
- If all the consumer instances have the same consumer group, then the records will effectively be load balanced over the consumer instances.
- If all the consumer instances have different consumer groups, then each record will be broadcast to all the consumer processes.
Rebalancing:
- If new instances join the group they will take over some partitions from other members of the group; if an instance dies, its partitions will be distributed to the remaining instances.
Consumer Instance
- each instance is the exclusive consumer of a "fair share" of partitions at any point in time.
- each instance is assigned one or more partitions. A partition is not assigned to more than one instance

Partitions:
- Each partition is an ordered, immutable sequence of records that is continually appended to
- The records in the partitions are each assigned a sequential id number called the offset that uniquely identifies each record within the partition.
- Allow to distribute the data load/requests/storage across multiple brokers/servers
- Act as the unit of parallelism
- Each partition has one server which acts as the "leader" and zero or more servers which act as "followers". The leader handles all read and write requests for the partition while the followers passively replicate the leader. If the leader fails, one of the followers will automatically become the new leader. Each server acts as a leader for some of its partitions and a follower for others so load is well balanced within the cluster.

Producer:
- Publish records to one or more topics
- Responsible for choosing which record to assign to which partition within the topic
- If key is null then the partition is assigned in a round-robin fashion
- By default it picks a partition based on the key
What happens if you add one more partition to an already created topic?
- You should never do this because the message order is lost

Offset:
-  sequential id number that uniquely identifies each record within the partition.

Offset Commits

Comandos Utiles del CLI?
- Consumer
- Producir
- Crear topicos
- Describir consumer groups?

Docker compose to deploy Kafka cluster locally

Configure Java Producer
- links
Configure Java Consumer
- links