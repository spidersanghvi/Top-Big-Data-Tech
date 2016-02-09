# Top-Big-Data-Tech
A copy of Bossie Awards 2015 list in a single page
  - [The best open source big data tools] (#The best open source big data tools)
  - [The best open source data center and cloud software] (http://www.infoworld.com/article/2982923/open-source-tools/bossie-awards-2015-the-best-open-source-data-center-and-cloud-software.html)
  - [The best open source big data tools] (http://www.infoworld.com/article/2982429/open-source-tools/bossie-awards-2015-the-best-open-source-big-data-tools.html)
  - [The best open source networking and security software] (http://www.infoworld.com/article/2982962/open-source-tools/bossie-awards-2015-the-best-open-source-networking-and-security-software.html)

## [The best open source big data tools] (http://www.infoworld.com/article/2982429/open-source-tools/bossie-awards-2015-the-best-open-source-big-data-tools.html)

  - [Spark](#spark)
  - [Storm](#storm)
  - [H2O](#h2o)
  - [Apex](#apex)
  - [Druid](#druid)
  - [Flink](#flink)
  - [Elasticsearch](#elasticsearch)
  - [SlamData](#slamdata)
  - [Drill](#drill)
  - [HBase](#hbase)
  - [Hive](#hive)
  - [Kylin](#kylin)
  - [CDAP](#cdap)
  - [Ranger](#ranger)
  - [Mesos](#mesos)
  - [Nifi](#nifi)
  - [Kafka](#kafka)
  - [OpenTSDB](#opentsdb)
  - [Jupyter](#jupyter)
  - [Zeppelin](#Zeppelin)

## Spark

With hundreds of contributors, [Spark] (https://spark.apache.org/) is one of the most active and fastest-growing Apache projects, and with heavyweights like IBM throwing their weight behind the project and major corporations bringing applications into large-scale production, the momentum shows no signs of letting up.

The sweet spot for Spark continues to be machine learning. Highlights since last year include the replacement of the SchemaRDD with a Dataframes API, similar to those found in R and Pandas, making data access much simpler than with the raw RDD interface. Also new are ML pipelines for building repeatable machine learning workflows, expanded and optimized support for various storage formats, simpler interfaces to machine learning algorithms, improvements in the display of cluster resources usage, and task tracking.

On by default in Spark 1.5 is the off-heap memory manager, Tungsten, which offers much faster processing by fine-tuning data structure layout in memory. Finally, the new website, [spark-packages.org] (http://spark-packages.org/), with more than 100 third-party libraries, adds many useful features from the community.

## Storm

[Apache Storm](https://storm.apache.org/) is a Clojure-based distributed computation framework primarily for streaming real-time analytics. Storm is based on the [disruptor pattern](https://lmax-exchange.github.io/disruptor/) for low-latency complex event processing created LMAX. Unlike Spark, Storm can do single events as opposed to “micro-batches,” and it has a lower memory footprint. In my experience, it scales better for streaming, especially when you’re mainly streaming to ingest data into other data sources.

Storm’s profile has been eclipsed by Spark, but Spark is inappropriate for many streaming applications. Storm is frequently used with Apache Kafka.

## H2O

[H2O](http://www.h2o.ai/product/) is a distributed, in-memory processing engine for machine learning that boasts an impressive array of algorithms. Previously only available for R users, version 3.0 adds Python and Java language bindings, as well as a Spark execution engine for the back end. The best way to view H20 is as a very large memory extension of your R environment. Instead of working directly on large data sets, the R extensions communicate via a REST API with the H2O cluster, where H2O does the heavy lifting.

Several useful R packages such as ddply have been wrapped, allowing you to use them on data sets larger than the amount of RAM on the local machine. You can run H2O on EC2, on a Hadoop/YARN cluster, and on Docker containers. With Sparkling Water (Spark plus H2O) you can access Spark RDDs on the cluster side by side to, for example, process a data frame with Spark before passing it to an H2O machine learning algorithm.

## Apex

[Apex](https://www.datatorrent.com/apex/) is an enterprise-grade, big data-in-motion platform that unifies stream processing as well as batch processing. A native YARN application, Apex processes streaming data in a scalable, fault-tolerant manner and provides all the common stream operators out of the box. One of the best things about Apex is that it natively supports the common event processing guarantees (exactly once, at least once, at most once). Formerly a commercial product by DataTorrent, Apex's roots show in the quality of the documentation, examples, code, and design. Devops and application development are cleanly separated, and user code generally doesn't have to be aware that it is running in a streaming cluster.

A related project, [Malhar](https://github.com/apache/incubator-apex-malhar), offers more than 300 commonly used operators and application templates that implement common business logic. The Malhar libraries significantly reduce the time it takes to develop an Apex application, and there are connectors (operators) for storage, file systems, messaging systems, databases, and nearly anything else you might want to connect to from an application. The operators can all be extended or customized to meet individual business's requirements. All Malhar components are available under the Apache license.

## Druid

[Druid](druid.io), which moved to a commercially friendly Apache license in February of this year, is best described as a hybrid, “event streams meet OLAP” solution. Originally developed to analyze online events for ad markets, Druid allows users to do arbitrary and interactive exploration of time series data. Some of the key features include low-latency ingest of events, fast aggregations, and approximate and exact calculations.

At the heart of Druid is a custom data store that uses specialized nodes to handle each part of the problem. Real-time ingest is managed by real-time nodes (JVMs) that eventually flush data to historical nodes that are responsible for data that has aged. Broker nodes direct queries in a scatter-gather fashion to both real-time and historical nodes to give the user a complete picture of events. Benchmarked at a sustained 500K events per second and 1 million events per second peak, Druid is ideal as a real-time dashboard for ad-tech, network traffic, and other activity streams

## Flink

At its core, [Flink](https://flink.apache.org/) is a data flow engine for event streams. Although superficially similar to Spark, Flink takes a different approach to in-memory processing. First, Flink was designed from the start as a stream processor. Batch is simply a special case of a stream with a beginning and an end, and Flink offers APIs for dealing with each case, the DataSet API (batch) and the DataStream API. Developers coming from the MapReduce world should feel right at home working with the DataSet API, and porting applications to Flink should be straightforward. In many ways Flink mirrors the simplicity and consistency that helped make Spark so popular. Like Spark, Flink is written in Scala.

The developers of Flink clearly thought out usage and operations too: Flink works natively with YARN and Tez, and it uses an off-heap memory management scheme to work around some of the JVM limitations. A peek at the Flink JIRA site shows a healthy pace of development, and you’ll find an active community on the mailing lists and on StackOverflow as well.

## Elasticsearch

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a distributed document search server based on [Apache Lucene](http://lucene.apache.org/). At its heart, Elasticsearch builds indices on JSON-formatted documents in nearly real time, enabling fast, full-text, schema-free queries. Combined with the open source Kibana dashboard, you can create impressive visualizations of your real-time data in a simple point-and-click fashion.

Elasticsearch is easy to set up and easy to scale, automatically making use of new hardware by rebalancing shards as required. The query syntax isn't at all SQL-like, but it is intuitive enough for anyone familiar with JSON. Most users won't be interacting at that level anyway. Developers can use the native JSON-over-HTTP interface or one of the several language bindings available, including Ruby, Python, PHP, Perl, .Net, Java, and JavaScript.

## SlamData

If you are seeking a user-friendly tool to visualize and understand your newfangled NoSQL data, take a look at [SlamData](http://slamdata.com/). SlamData allows you to query nested JSON data using familiar SQL syntax, without relocation or transformation.

One of the technology’s main features is its connectors. From MongoDB to HBase, Cassandra, and Apache Spark, SlamData taps external data sources with the industry's most advanced “pushdown” processing technology, performing transformations and analytics close to the data.

While you might ask, “Wouldn’t I be better off building a data lake or data warehouse?” consider the companies that were born in NoSQL. Skipping the ETL and simply connecting a visualization tool to a replica offers distinct advantages -- not only in terms of how up-to-date the data is, but in how many moving parts you have to maintain.

## Drill

[Drill](https://drill.apache.org/) is a distributed system for interactive analysis of large-scale data sets, inspired by Google's [Dremel](http://research.google.com/pubs/pub36632.html). Designed for low-latency analysis of nested data, Drill has a stated design goal of scaling to 10,000 servers and querying petabytes of data and trillions of records.

Nested data can be obtained from a variety of data sources (such as HDFS, HBase, Amazon S3, and Azure Blobs) and in multiple formats (including JSON, Avro, and protocol buffers), and you don't need to specify a schema up front (“schema on read”).

Drill uses ANSI SQL:2003 for its query language, so there's no learning curve for data engineers to overcome, and it allows you to join data across multiple data sources (for example, joining a table in HBase with logs in HDFS). Finally, Drill offers ODBC and JDBC interfaces to connect your favorite BI tools.

## HBase

[HBase](http://hbase.apache.org/) reached the 1.x milestone this year and continues to improve. Like other nonrelational distributed datastores, HBase excels at returning search results very quickly and for this reason is often used to back search engines, such as the ones at eBay, Bloomberg, and Yahoo. As a stable and mature software offering, HBase does not get fresh features as frequently as newer projects, but that's often good for enterprises.

Recent improvements include the addition of high-availability region servers, support for rolling upgrades, and YARN compatibility. Features in the works include scanner updates that promise to improve performance and the ability to use HBase as a persistent store for streaming applications like Storm and Spark. HBase can also be queried SQL style via the [Phoenix](http://phoenix.apache.org/) project, now out of incubation, whose SQL compatibility is steadily improving. Phoenix recently added a Spark connector and the ability to add custom user-defined functions.

## Hive


## Kylin


## CDAP


## Ranger


## Mesos


## Nifi


## Kafka


## OpenTSDB


## Jupyter


## Zeppelin

