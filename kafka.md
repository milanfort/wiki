# Apache Kafka

## Installation (Single Development Machine, Two Brokers)

1. Download and extract the kafka distribution (e.g. `kafka_2.11-0.10.0.1.tgz`).

2. Copy/rename the extracted directory to the following two directories:
    * `kafka1`
    * `kafka2`
    
3. In each of the _kafka*_ directories, create a directory `data`.

4. In directory `kafka1/config` edit the file `server.properties`. Set the following values:
```
    broker.id=1
    listeners=PLAINTEXT://:9093
    log.dirs=data    
    zookeeper.connect=localhost:2181,localhost:3181,localhost:4181
```

5. Analogously, in directory `kafka2/config` edit the file `server.properties`. Set the following values:
```
    broker.id=2
    listeners=PLAINTEXT://:9094
    log.dirs=data
    zookeeper.connect=localhost:2181,localhost:3181,localhost:4181
```


## Running Kafka Cluster

1. Start ZooKeeper Ensemble. See [ZooKeeper Wiki](zookeeper.md) for details.

2. In both _kafka*_ directories, run the following command:  
`bin/kafka-server-start.sh config/server.properties &`

3. To stop kafka, run the following command in both directories:
`bin/kafka-server-stop.sh` 


## Creating New Topic

* To create a new topic named _foobar_, with 2 partitions and replication factor 2, run the following command:
`bin/kafka-topics.sh --create --if-not-exists --zookeeper localhost:2181,localhost:3181,localhost:4181 --replication-factor 2 --partitions 2 --topic foobar`


## List All Existing Topics

* `bin/kafka-topics.sh --list --zookeeper localhost:2181,localhost:3181,localhost:4181`


## Describe an Existing Topic

* To print information about the topic _foobar_, run the following command:

`bin/kafka-topics.sh --describe --zookeeper localhost:2181,localhost:3181,localhost:4181 --topic foobar`


## Use Console Producer and Consumer

* `bin/kafka-console-producer.sh --broker-list localhost:9093,localhost:9094 --topic foobar`

* `bin/kafka-console-consumer.sh --zookeeper localhost:2181,localhost:3181,localhost:4181 --from-beginning --topic foobar`
