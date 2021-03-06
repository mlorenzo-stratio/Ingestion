FLUME-INGESTION
===================


[![Build Status](https://github.com/Stratio/Ingestion)](https://github.com/Stratio/Ingestion)


Flume Ingestion started as a fork of Apache Flume (1.6), where you can find:

**Several bug fixes**

 - Some of them really important, such as unicode support

**Several enhancements of Flume's sources & sinks**

 - ElasticSearch mapper, for example

**Custom sources and sinks, developed by Stratio**

 - SNMP (v1, v2c and 3)
 - redis, Kafka (0.8.1.1)
 - MongoDB, JDBC, Cassandra and Druid
 - Stratio Decision (Complex Event Processing engine)
 - REST client, Flume agents stats
 
 You can find more documentation about us [here](http://docs.stratio.com/modules/flume-ingestion/development/)


Flume Ingestion components
----------------------------


* Data transporter and collector: [Apache Flume](http://flume.apache.org/)
* Data extractor and transformer: [Morphlines](http://kitesdk.org/docs/current/kite-morphlines/index.html)
* Custom sources types to read data from:
    - REST   com.stratio.ingestion.source.rest.RestSource
    - Redis FlumeStats   com.stratio.ingestion.source.redis.RedisSource
    - SNMPTraps   com.stratio.ingestion.source.snmptraps.SNMPSource
    - IRC   com.stratio.ingestion.source.irc.IRCSource
* Custom sinks types to write the data to:
    - Cassandra   com.stratio.ingestion.sink.cassandra.CassandraSink
    - MongoDB   com.stratio.ingestion.sink.mongodb.MongoSink
    - [Stratio Decision](https://github.com/Stratio/Decision)
    - JDBC   com.stratio.ingestion.sink.jdbc.JDBCsink
    - Kafka   com.stratio.ingestion.sink.kafka.KafkaSink
    - Druid   com.stratio.ingestion.sink.druid.DruidSink


What is Apache Flume?
--------------------------

Apache Flume is a distributed, reliable, and available system for efficiently collecting, aggregating and moving large amounts of log data from many different sources to a centralized data store.

Its use is not only designed for logs, in fact you can find a myriad of sources, sinks and transformations.

In addition, a sink could be a big data storage but also another real-time system (Apache Kafka, Spark Streaming).

Compile & Package
--------------------------

```
$ git submodule init
$ git submodule update
$ mvn install
$ cd stratio-ingestion-dist
$ mvn clean compile package -Ppackage
```

Distribution will be available at stratio-ingestion-dist/target/stratio-ingestion-0.6.0-SNAPSHOT-bin.tar.gz


Interesting facts about Flume-Ingestion
-----------------------------------------------

 * Flume Ingestion is Apache Flume "on steroids" :)
 
 * We are extensively using Kite SDK (morphlines) in order to do a better T from ETL, and so we have also developed a bunch of custom transformations.
 
 * Stratio ingestion is fully open source and we work very close to the Flume community.

Flume Ingestion FAQ
-------------------------


**Can I use Flume Ingestion for aggregating data (time-based rollups, for example)?**

*This is not a good idea from our experience, but you can use [Stratio Sparkta](https://github.com/Stratio/Sparkta) for real-time aggregation.

**Is Flume Ingestion multipersistence?**

*Yes, you can write data to JDBC sources, mongoDB, Apache Cassandra, ElasticSearch, Apache Kafka, among others.*


**Can I send data to decision-cep-engine?**

*Of course, we have developed a sink in order to send events from Flume to an existing stream in our CEP engine.  The sink will create the stream if it does not exist in the engine.* 

Changelog
---------

See the [changelog](CHANGELOG.md) for changes. 


