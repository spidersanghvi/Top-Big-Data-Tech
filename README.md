# Top-Big-Data-Tech
A copy of Bossie Awards 2015 list related to Big Data and networking in a single page
  - [The best open source big data tools] (#the-best-open-source-big-data-tools) - [Article] (http://www.infoworld.com/article/2982429/open-source-tools/bossie-awards-2015-the-best-open-source-big-data-tools.html)
  - [The best open source data center and cloud software] (#the-best-open-source-data-center-and-cloud-software) - [Article] (http://www.infoworld.com/article/2982923/open-source-tools/bossie-awards-2015-the-best-open-source-data-center-and-cloud-software.html)
  - [The best open source networking and security software](#the-best-open-source-networking-and-security-software) - [Article] (http://www.infoworld.com/article/2982962/open-source-tools/bossie-awards-2015-the-best-open-source-networking-and-security-software.html)

## The best open source big data tools

How many Apache projects can sit on a pile of big data? Fire up your Hadoop cluster, and you might be able to count them. Among this year's Bossies in big data, you'll find the fastest, widest, and deepest newfangled solutions for large-scale SQL, stream processing, sort-of stream processing, and in-memory analytics, not to mention our favorite maturing members of the Hadoop ecosystem. It seems everyone has a nail to drive into MapReduce's coffin.

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
  - [Zeppelin](#zeppelin)

### Spark

With hundreds of contributors, [Spark] (https://spark.apache.org/) is one of the most active and fastest-growing Apache projects, and with heavyweights like IBM throwing their weight behind the project and major corporations bringing applications into large-scale production, the momentum shows no signs of letting up.

The sweet spot for Spark continues to be machine learning. Highlights since last year include the replacement of the SchemaRDD with a Dataframes API, similar to those found in R and Pandas, making data access much simpler than with the raw RDD interface. Also new are ML pipelines for building repeatable machine learning workflows, expanded and optimized support for various storage formats, simpler interfaces to machine learning algorithms, improvements in the display of cluster resources usage, and task tracking.

On by default in Spark 1.5 is the off-heap memory manager, Tungsten, which offers much faster processing by fine-tuning data structure layout in memory. Finally, the new website, [spark-packages.org] (http://spark-packages.org/), with more than 100 third-party libraries, adds many useful features from the community.

### Storm

[Apache Storm](https://storm.apache.org/) is a Clojure-based distributed computation framework primarily for streaming real-time analytics. Storm is based on the [disruptor pattern](https://lmax-exchange.github.io/disruptor/) for low-latency complex event processing created LMAX. Unlike Spark, Storm can do single events as opposed to “micro-batches,” and it has a lower memory footprint. In my experience, it scales better for streaming, especially when you’re mainly streaming to ingest data into other data sources.

Storm’s profile has been eclipsed by Spark, but Spark is inappropriate for many streaming applications. Storm is frequently used with Apache Kafka.

### H2O

[H2O](http://www.h2o.ai/product/) is a distributed, in-memory processing engine for machine learning that boasts an impressive array of algorithms. Previously only available for R users, version 3.0 adds Python and Java language bindings, as well as a Spark execution engine for the back end. The best way to view H20 is as a very large memory extension of your R environment. Instead of working directly on large data sets, the R extensions communicate via a REST API with the H2O cluster, where H2O does the heavy lifting.

Several useful R packages such as ddply have been wrapped, allowing you to use them on data sets larger than the amount of RAM on the local machine. You can run H2O on EC2, on a Hadoop/YARN cluster, and on Docker containers. With Sparkling Water (Spark plus H2O) you can access Spark RDDs on the cluster side by side to, for example, process a data frame with Spark before passing it to an H2O machine learning algorithm.

### Apex

[Apex](https://www.datatorrent.com/apex/) is an enterprise-grade, big data-in-motion platform that unifies stream processing as well as batch processing. A native YARN application, Apex processes streaming data in a scalable, fault-tolerant manner and provides all the common stream operators out of the box. One of the best things about Apex is that it natively supports the common event processing guarantees (exactly once, at least once, at most once). Formerly a commercial product by DataTorrent, Apex's roots show in the quality of the documentation, examples, code, and design. Devops and application development are cleanly separated, and user code generally doesn't have to be aware that it is running in a streaming cluster.

A related project, [Malhar](https://github.com/apache/incubator-apex-malhar), offers more than 300 commonly used operators and application templates that implement common business logic. The Malhar libraries significantly reduce the time it takes to develop an Apex application, and there are connectors (operators) for storage, file systems, messaging systems, databases, and nearly anything else you might want to connect to from an application. The operators can all be extended or customized to meet individual business's requirements. All Malhar components are available under the Apache license.

### Druid

[Druid](druid.io), which moved to a commercially friendly Apache license in February of this year, is best described as a hybrid, “event streams meet OLAP” solution. Originally developed to analyze online events for ad markets, Druid allows users to do arbitrary and interactive exploration of time series data. Some of the key features include low-latency ingest of events, fast aggregations, and approximate and exact calculations.

At the heart of Druid is a custom data store that uses specialized nodes to handle each part of the problem. Real-time ingest is managed by real-time nodes (JVMs) that eventually flush data to historical nodes that are responsible for data that has aged. Broker nodes direct queries in a scatter-gather fashion to both real-time and historical nodes to give the user a complete picture of events. Benchmarked at a sustained 500K events per second and 1 million events per second peak, Druid is ideal as a real-time dashboard for ad-tech, network traffic, and other activity streams

### Flink

At its core, [Flink](https://flink.apache.org/) is a data flow engine for event streams. Although superficially similar to Spark, Flink takes a different approach to in-memory processing. First, Flink was designed from the start as a stream processor. Batch is simply a special case of a stream with a beginning and an end, and Flink offers APIs for dealing with each case, the DataSet API (batch) and the DataStream API. Developers coming from the MapReduce world should feel right at home working with the DataSet API, and porting applications to Flink should be straightforward. In many ways Flink mirrors the simplicity and consistency that helped make Spark so popular. Like Spark, Flink is written in Scala.

The developers of Flink clearly thought out usage and operations too: Flink works natively with YARN and Tez, and it uses an off-heap memory management scheme to work around some of the JVM limitations. A peek at the Flink JIRA site shows a healthy pace of development, and you’ll find an active community on the mailing lists and on StackOverflow as well.

### Elasticsearch

[Elasticsearch](https://www.elastic.co/products/elasticsearch) is a distributed document search server based on [Apache Lucene](http://lucene.apache.org/). At its heart, Elasticsearch builds indices on JSON-formatted documents in nearly real time, enabling fast, full-text, schema-free queries. Combined with the open source Kibana dashboard, you can create impressive visualizations of your real-time data in a simple point-and-click fashion.

Elasticsearch is easy to set up and easy to scale, automatically making use of new hardware by rebalancing shards as required. The query syntax isn't at all SQL-like, but it is intuitive enough for anyone familiar with JSON. Most users won't be interacting at that level anyway. Developers can use the native JSON-over-HTTP interface or one of the several language bindings available, including Ruby, Python, PHP, Perl, .Net, Java, and JavaScript.

### SlamData

If you are seeking a user-friendly tool to visualize and understand your newfangled NoSQL data, take a look at [SlamData](http://slamdata.com/). SlamData allows you to query nested JSON data using familiar SQL syntax, without relocation or transformation.

One of the technology’s main features is its connectors. From MongoDB to HBase, Cassandra, and Apache Spark, SlamData taps external data sources with the industry's most advanced “pushdown” processing technology, performing transformations and analytics close to the data.

While you might ask, “Wouldn’t I be better off building a data lake or data warehouse?” consider the companies that were born in NoSQL. Skipping the ETL and simply connecting a visualization tool to a replica offers distinct advantages -- not only in terms of how up-to-date the data is, but in how many moving parts you have to maintain.

### Drill

[Drill](https://drill.apache.org/) is a distributed system for interactive analysis of large-scale data sets, inspired by Google's [Dremel](http://research.google.com/pubs/pub36632.html). Designed for low-latency analysis of nested data, Drill has a stated design goal of scaling to 10,000 servers and querying petabytes of data and trillions of records.

Nested data can be obtained from a variety of data sources (such as HDFS, HBase, Amazon S3, and Azure Blobs) and in multiple formats (including JSON, Avro, and protocol buffers), and you don't need to specify a schema up front (“schema on read”).

Drill uses ANSI SQL:2003 for its query language, so there's no learning curve for data engineers to overcome, and it allows you to join data across multiple data sources (for example, joining a table in HBase with logs in HDFS). Finally, Drill offers ODBC and JDBC interfaces to connect your favorite BI tools.

### HBase

[HBase](http://hbase.apache.org/) reached the 1.x milestone this year and continues to improve. Like other nonrelational distributed datastores, HBase excels at returning search results very quickly and for this reason is often used to back search engines, such as the ones at eBay, Bloomberg, and Yahoo. As a stable and mature software offering, HBase does not get fresh features as frequently as newer projects, but that's often good for enterprises.

Recent improvements include the addition of high-availability region servers, support for rolling upgrades, and YARN compatibility. Features in the works include scanner updates that promise to improve performance and the ability to use HBase as a persistent store for streaming applications like Storm and Spark. HBase can also be queried SQL style via the [Phoenix](http://phoenix.apache.org/) project, now out of incubation, whose SQL compatibility is steadily improving. Phoenix recently added a Spark connector and the ability to add custom user-defined functions.

### Hive

Although stable and mature for several years, [Hive](https://hive.apache.org/) reached the 1.0 version milestone this year and continues to be the best solution when really heavy SQL lifting (many petabytes) is required. The community continues to focus on improving the speed, scale, and SQL compliance of Hive. Currently at version 1.2, significant improvements since its last Bossie include full ACID semantics, cross-data center replication, and a cost-based optimizer.

Hive 1.2 also brought improved SQL compliance, making it easier for organizations to use it to off-load ETL jobs from their existing data warehouses. In the pipeline are speed improvements with an in-memory cache called LLAP (which, from the looks of the JIRAs, is about ready for release), the integration of Spark machine learning libraries, and improved SQL constructs like nonequi joins, interval types, and subqueries.

### Kylin

[Kylin](http://kylin.apache.org/) is an application developed at eBay for processing very large OLAP cubes via ANSI SQL, a task familiar to most data analysts. If you think about how many items are on sale now and in the past at eBay, and all the ways eBay might want to slice and dice data related to those items, you will begin to understand the types of queries Kylin was designed for.

Like most other analysis applications, Kylin supports multiple access methods, including JDBC, ODBC, and a REST API for programmatic access. Although Kylin is still in incubation at Apache, and the community nascent, the project is well documented and the developers are responsive and eager to understand customer use cases. Getting up and running with a starter cube was a snap. If you have a need for analysis of extremely large cubes, you should take a look at Kylin.

### CDAP

[CDAP](http://cdap.io/) (Cask Data Access Platform) is a framework running on top of Hadoop that abstracts away the complexity of building and running big data applications. CDAP is organized around two core abstractions: data and applications. CDAP Datasets are logical representations of data that behave uniformly regardless of the underlying storage layer; CDAP Streams provide similar support for real-time data.

Applications use CDAP services for things such as distributed transactions and service discovery to shield developers from the low-level details of Hadoop. CDAP comes with a data ingestion framework and a few prebuilt applications and “packs” for common tasks like ETL and website analytics, along with support for testing, debugging, and security. Like most formerly commercial (closed source) projects, CDAP benefits from good documentation, tutorials, and examples.

### Ranger

Security has long been a sore spot with Hadoop. It isn’t (as is frequently reported) that Hadoop is “insecure” or “has no security.” Rather, the truth was more that Hadoop had too much security, though not in a good way. I mean that every component had its own authentication and authorization implementation that wasn’t integrated with the rest of platform.

Hortonworks acquired XA/Secure in May, and a few renames later we have [Ranger](https://ranger.incubator.apache.org/). Ranger pulls many of the key components of Hadoop together under one security umbrella, allowing you to set a “policy” that ties your Hadoop security to your existing ACL-based Active Directory authentication and authorization. Ranger gives you one place to manage Hadoop access control, one place to audit, one place to manage the encryption, and a pretty Web page to do it from.

### Mesos

[Mesos](http://mesos.apache.org/), developed at the [AMPLab](https://amplab.cs.berkeley.edu/) at U.C. Berkeley that also brought us Spark, takes a different approach to managing cluster computing resources. The best way to describe Mesos is as a distributed microkernel for the data center. Mesos provides a minimal set of operating system mechanisms like inter-process communications, disk access, and memory to higher-level applications, called “frameworks” in Mesos-speak, that run in what is analogous to user space. Popular frameworks for Mesos include [Chronos](http://nerds.airbnb.com/introducing-chronos/) and [Aurora](http://aurora.apache.org/) for building ETL pipelines and job scheduling, and a few big data processing applications including Hadoop, Storm, and Spark, which have been ported to run as Mesos frameworks.

Mesos applications (frameworks) negotiate for cluster resources using a two-level scheduling mechanism, so writing a Mesos application is unlikely to feel like a familiar experience to most developers. Although Mesos is a young project, momentum is growing, and with Spark being an exceptionally good fit for Mesos, we're likely to see more from Mesos in the coming years.

### Nifi

[NiFi](http://nifi.apache.org/) is an incubating Apache project to automate the flow of data between systems. It doesn't operate in the traditional space that Kafka and Storm do, but rather in the space between external devices and the data center. NiFi was originally developed by the NSA and donated to the open source community in 2014. It has a strong community of developers and users within various government agencies.

NiFi isn't like anything else in the current big data ecosystem. It is much closer to a tradition EAI (enterprise application integration) tool than a data processing platform, although simple transformations are possible. One interesting feature is the ability to debug and change data flows in real time. Although not quite a REPL (read, eval, print loop), this kind of paradigm dramatically shortens the development cycle by not requiring a compile-deploy-test-debug workflow. Other interesting features include a strong “chain of custody,” where each piece of data can be tracked from beginning to end, along with any changes made along the way. You can also prioritize data flows so that time-sensitive information can be received as quickly as possible, bypassing less time-critical events.

### Kafka

[Kafka](https://kafka.apache.org/) has emerged as the de-facto standard for distributed publish-subscribe messaging in the big data space. Its design allows brokers to support thousands of clients at high rates of sustained message throughput, while maintaining durability through a distributed commit log.

High throughput comes from Kafka's intelligent partitioning of incoming data streams, which enables parallel reads and writes. These partitioned data streams are then copied to a configurable number of replicas, which in turn are written to disk, preventing data loss and enabling an ability to "replay" the history of the data stream.

When consumers want to read messages, Kafka looks up their offset in the central log and sends them. Because messages are not deleted immediately, adding consumers or replaying historical messages does not impose additional costs. Kafka has been benchmarked at 2 million writes per second by its developers at LinkedIn. Despite Kafka’s sub-1.0 version number, Kafka is a mature and stable product, in use in some of the largest clusters in the world.

### OpenTSDB

[OpenTSDB](http://opentsdb.net/) is a time series database built on HBase. It was designed specifically for analyzing data collected from applications, mobile devices, networking equipment, and other hardware devices. The custom HBase schema used to store the time series data has been designed for fast aggregations and minimal storage requirements.

By using HBase as the underlying storage layer, OpenTSDB gains the distributed and reliable characteristics of that system. Users don't interact with HBase directly; instead events are written to the system via the time series daemon (TSD), which can be scaled out as required to handle high-throughput situations. There are a number of prebuilt connectors to publish data to OpenTSDB, and clients to read data from Ruby, Python, and other languages. OpenTSDB isn't strong on creating interactive graphics, but several third-party tools fill that gap. If you are already using HBase and want a simple way to store event data, OpenTSDB might be just the thing.

### Jupyter

Everybody's favorite notebook application went generic. [Jupyter](http://jupyter.org/) is “the language-agnostic parts of IPython” spun out into an independent package. Although Jupyter itself is written in Python, the system is modular. Now you can have an IPython-like interface, along with notebooks for sharing code, documentation, and data visualizations, for nearly any language you like.

At least [50 language](https://github.com/ipython/ipython/wiki/IPython-kernels-for-other-languages) kernels are already supported, including LISP, R, Ruby, F#, Perl, and Scala. In fact, even IPython itself is simply a Python module for Jupyter. Communication with the language kernel is via a REPL (read, eval, print loop) protocol, similar to [nREPL](https://github.com/clojure/tools.nrepl) or [Slime](https://github.com/slime/slime). It is nice to see such a useful piece of software receiving significant nonprofit funding to further its development, such as parallel execution and multi-user notebooks. Behold, open source at its best.

### Zeppelin

While still in incubation, [Apache Zeppelin](https://zeppelin.incubator.apache.org/) is nevertheless stirring the data analytics and visualization pot. The Web-based notebook enables users to ingest, discover, analyze, and visualize their data. The notebook also allows you to collaborate with others to make data-driven, interactive documents incorporating a growing number of programming languages. 

This technology also boasts an integration with Spark and an interpreter concept allowing any language or data processing back end to be plugged into Zeppelin. Currently Zeppelin supports interpreters such as Scala, Python, SparkSQL, Hive, Markdown, and Shell. 

Zeppelin is still immature. I wanted to put a demo up but couldn’t find an easy way to disable “shell” as an execution option (among other things). However, it already looks better visually than IPython Notebook, which is the popular incumbent in this space. If you don’t want to spring for DataBricks Cloud or need something open source and extensible, this is the most promising distributed computing notebook around -- especially if you’re a Sparky type.


## The best open source data center and cloud software

You might have heard about this new thing called Docker containers. Developers love them because you can build them with a script, add services in layers, and push them right from your MacBook Pro to a server for testing. It works because they're superlightweight, unlike those now-archaic virtual machines. Containers -- and other lightweight approaches to deliver services -- are changing the shape of operating systems, applications, and the tools to manage them. Our Bossie winners in data center and cloud are leading the charge.

  - [Docker Machine, Compose, and Swarm](#docker-machine-compose-and-swarm)
  - [CoreOS and Rkt](#coreos-and-rkt)
  - [RancherOS](#rancheros)
  - [Kubernetes](#kubernetes)
  - [Mesos](#mesos-1)
  - [SmartOS and SmartDataCenter](#smartos-and-smartdatacenter)
  - [Sensu](#sensu)
  - [Prometheus](#prometheus)
  - [Elasticsearch, Logstash, and Kibana](#elasticsearch-logstash-and-kibana)
  - [Ansible](#ansible)
  - [Jenkins](#jenkins)
  - [Node.js and io.js](#nodejs-and-iojs)
  - [Seneca](#seneca)
  - [.Net Core and ASP.Net vNext](#net-core-and-aspnet-vnext)
  - [GlusterFS](#glusterfs)
 
### Docker Machine, Compose, and Swarm

Docker’s open source container technology has been adopted by the major public clouds and is being built into the next version of Windows Server. Allowing developers and operations teams to separate applications from infrastructure, Docker is a powerful data center automation tool.

However, containers are only part of the Docker story. Docker also provides a series of tools that allow you to use the Docker API to automate the entire container lifecycle, as well as handling application design and orchestration.

[Machine](https://www.docker.com/products/docker-machine) allows you to automate the provisioning of Docker Containers. Starting with a command line, you can use a single line of code to target one or more hosts, deploy the Docker engine, and even join it to a Swarm cluster. There’s support for most hypervisors and cloud platforms – all you need are your access credentials.

[Swarm](https://www.docker.com/products/docker-swarm) handles clustering and scheduling, and it can be integrated with Mesos for more advanced scheduling capabilities. You can use Swarm to build a pool of container hosts, allowing your apps to scale out as demand increases. Applications and all of their dependencies can be defined with [Compose](https://www.docker.com/products/docker-compose), which lets you link containers together into a distributed application and launch them as a group. Compose descriptions work across platforms, so you can take a developer configuration and quickly deploy in production.

### CoreOS and Rkt

A thin, lightweight server OS, [CoreOS](https://coreos.com/) is based on Google’s Chromium OS. Instead of using a package manager to install functions, it’s designed to be used with Linux containers. By using containers to extend a thin core, CoreOS allows you to quickly deploy applications, working well on cloud infrastructures.

CoreOS’s container management tooling, fleet, is designed to treat a cluster of CoreOS servers as a single unit, with tools for managing high availability and for deploying containers to the cluster based on resource availability. A cross-cluster key/value store, etcd, handles device management and supports service discovery. If a node fails, etcd can quickly restore state on a new replica, giving you a distributed configuration management platform that’s linked to CoreOS’s automated update service.

While CoreOS is perhaps best known for its Docker support, the CoreOS team is developing its own container runtime, rkt, with its own container format, the App Container Image. Also compatible with Docker containers, rkt has a modular architecture that allows different containerization systems (even hardware virtualization, in a proof of concept from Intel) to be plugged in. However, rkt is still in the early stages of development, so isn’t quite production ready.

### RancherOS

As we abstract more and more services away from the underlying operating system using containers, we can start thinking about what tomorrow’s operating system will look like. Similar to our applications, it’s going to be a modular set of services running on a thin kernel, self-configuring to offer only the services our applications need.

[RancherOS](http://rancher.com/rancher-os/) is a glimpse of what that OS might look like. Blending the Linux kernel with Docker, RancherOS is a minimal OS suitable for hosting container-based applications in cloud infrastructures. Instead of using standard Linux packaging techniques, RancherOS leverages Docker to host Linux user-space services and applications in separate container layers. A low-level Docker instance is first to boot, hosting system services in their own containers. Users' applications run in a higher-level Docker instance, separate from the system containers. If one of your containers crashes, the host keeps running.

RancherOS is only 20MB in size, so it's easy to replicate across a data center. It’s also designed to be managed using automation tools, not manually, with API-level access that works with Docker’s management tools as well as with Rancher Labs’ own cloud infrastructure and management tools.

### Kubernetes

Google’s [Kubernetes](http://kubernetes.io/) container orchestration system is designed to manage and run applications built in Docker and Rocket containers. Focused on managing microservice applications, Kubernetes lets you distribute your containers across a cluster of hosts, while handling scaling and ensuring managed services run reliably.

With containers providing an application abstraction layer, Kubernetes is an application-centric management service that supports many modern development paradigms, with a focus on user intent. That means you launch applications, and Kubernetes will manage the containers to run within the parameters you set, using the Kubernetes scheduler to make sure it gets the resources it needs. Containers are grouped into pods and managed by a replication engine that can recover failed containers or add more pods as applications scale.

Kubernetes powers Google’s own Container Engine, and it runs on a range of other cloud and data center services, including AWS and Azure, as well as vSphere and Mesos. Containers can be either loosely or tightly coupled, so applications not designed for cloud PaaS operations can be migrated to the cloud as a tightly coupled set of containers. Kubernetes also supports rapid deployment of applications to a cluster, giving you an endpoint for a continuous delivery process.

### Mesos

Turning a data center into a private or public cloud requires more than a hypervisor. It requires a new operating layer that can manage the data center resources as if they were a single computer, handling resources and scheduling. Described as a “distributed systems kernel,” [Apache Mesos](https://mesos.apache.org/) allows you to manage thousands of servers, using containers to host applications and APIs to support parallel application development.

At the heart of Mesos is a set of daemons that expose resources to a central scheduler. Tasks are distributed across nodes, taking advantage of available CPU and memory. One key approach is the ability for applications to reject offered resources if they don’t meet requirements. It’s an approach that works well for big data applications, and you can use Mesos to run Hadoop and Cassandra distributed databases, as well as Apache’s own Spark data processing engine. There’s also support for the Jenkins continuous integration server, allowing you to run build and test workers in parallel on a cluster of servers, dynamically adjusting the tasks depending on workload.

Designed to run on Linux and Mac OS X, Mesos has also recently been ported to Windows to support the development of scalable parallel applications on Azure.

### SmartOS and SmartDataCenter

Joyent’s [SmartDataCenter](https://github.com/joyent/sdc) is the software that runs its public cloud, adding a management platform on top of its [SmartOS](https://smartos.org/) thin server OS. A descendent of OpenSolaris that combines Zones containers and the KVM hypervisor, SmartOS is an in-memory operating system, quick to boot from a USB stick and run on bare-metal servers.

Using SmartOS, you can quickly deploy a set of lightweight servers that can be programmatically managed via a set of JSON APIs, with functionality delivered via virtual machines, downloaded by built-in image management tools. Through the use of VMs, all userland operations are isolated from the underlying OS, reducing the security exposure of both the host and guests.

SmartDataCenter runs on SmartOS servers, with one server running as a dedicated management node, and the rest of a cluster operating as compute nodes. You can get started with a Cloud On A Laptop build (available as a VMware virtual appliance) that lets you experiment with the management server. In a live data center, you’ll deploy SmartOS on your servers, using ZFS to handle storage – which includes your local image library. Services are deployed as images, with components stored in an object repository.

The combination of SmartDataCenter and SmartOS builds on the experience of Joyent’s public cloud, giving you a tried and tested set of tools that can help you bootstrap your own cloud data center. It’s an infrastructure focused on virtual machines today, but laying the groundwork for tomorrow. A related Joyent project, [sdc-docker](https://github.com/joyent/sdc-docker), exposes an entire SmartDataCenter cluster as a single Docker host, driven by native Docker commands.

### Sensu

Managing large-scale data centers isn’t about working with server GUIs, it’s about automating scripts based on information from monitoring tools and services, routing information from sensors and logs, and then delivering actions to applications. One tool that’s beginning to offer this functionality is [Sensu](https://sensuapp.org/), often described as a “monitoring router.”

Scripts running across your data center deliver information to Sensu, which then routes it to the appropriate handler, using a publish-and-subscribe architecture based on RabbitMQ. Servers can be distributed, delivering published check results to handler code. You might see results in email, or in a Slack room, or in Sensu’s own dashboards. Message formats are defined in JSON files, or mutators used to format data on the fly, and messages can be filtered to one or more event handlers.

Sensu is still a relatively young tool, but it’s one that shows a lot of promise. If you’re going to automate your data center, you’re going to need a tool like this not only to show you what’s happening, but to deliver that information where it’s most needed. A commercial option adds support for integration with third-party applications, but much of what you need to manage a data center is in the open source release.

### Prometheus

Managing a modern data center is a complex task. Racks of servers need to be treated like cattle rather than pets, and you need a monitoring system designed to handle hundreds and thousands of nodes. Monitoring applications presents special challenges, and that’s where [Prometheus](http://prometheus.io/) comes in to play. A service monitoring system designed to deliver alerts to operators, Prometheus can run on everything from a single laptop to a highly available cluster of monitoring servers.

Time series data is captured and stored, then compared against patterns to identify faults and problems. You’ll need to expose data on HTTP endpoints, using a YAML file to configure the server. A browser-based reporting tool handles displaying data, with an expression console where you can experiment with queries. Dashboards can be created with a GUI builder, or written using a series of templates, letting you deliver application consoles that can be managed using version control systems such as Git.

Captured data can be managed using expressions, which make it easy to aggregate data from several sources -- for example, letting you bring performance data from a series of Web endpoints into one store. An experimental alert manager module delivers alerts to common collaboration and devops tools, including Slack and PagerDuty. Official client libraries for common languages like Go and Java mean it’s easy to add Prometheus support to your applications and services, while third-party options extend Prometheus to Node.js and .Net.

### Elasticsearch, Logstash, and Kibana

Running a modern data center generates a lot of data, and it requires tools to get information out of that data. That’s where the combination of Elasticsearch, Logstash, and Kibana, often referred to as the ELK stack, comes into play.

Designed to handle scalable search across a mix of content types, including structured and unstructured documents, [Elasticsearch](https://www.elastic.co/products/elasticsearch) builds on Apache’s Lucene information retrieval tools, with a RESTful JSON API. It’s used to provide search for sites like Wikipedia and GitHub, using a distributed index with automated load balancing and routing.

Under the fabric of a modern cloud is a physical array of servers, running as VM hosts. Monitoring many thousands of servers needs centralized logs. [Logstash](https://www.elastic.co/products/logstash) harvests and filters the logs generated by those servers (and by the applications running on them), using a forwarder on each physical and virtual machine. Logstash-formatted data is then delivered to Elasticsearch, giving you a search index that can be quickly scaled as you add more servers.

At a higher level, [Kibana](https://www.elastic.co/products/kibana) adds a visualization layer to Elasticsearch, providing a Web dashboard for exploring and analyzing the data. Dashboards can be created around custom searches and shared with your team, providing a quick, easy-to-digest devops information feed.

### Ansible

Managing server configuration is a key element of any devops approach to managing a modern data center or a cloud infrastructure. Configuration management tooling that takes a desired state approach to simplifies systems management at cloud scale, using server and application descriptions to handle server and application deployment.

[Ansible](http://www.ansible.com/) offers a minimal management service, using SSH to manage Unix nodes and PowerShell to work with Windows servers, with no need to deploy agents. An Ansible Playbook describes the state of a server or service in YAML, deploying Ansible modules to servers that handle configuration and removing them once the service is running. You can use Playbooks to orchestrate tasks -- for example, deploying several Web endpoints with a single script.

It’s possible to make module creation and Playbook delivery part of a continuous delivery process, using build tools to deliver configurations and automate deployment. Ansible can pull in information from cloud service providers, simplifying management of virtual machines and networks. Monitoring tools in Ansible are able to trigger additional deployments automatically, helping manage and control cloud services, as well as working to manage resources used by large-scale data platforms like Hadoop.

### Jenkins

Getting continuous delivery right requires more than a structured way of handling development; it also requires tools for managing test and build. That’s where the [Jenkins](https://jenkins-ci.org/) continuous integration server comes in. Jenkins works with your choice of source control, your test harnesses, and your build server. It’s a flexible tool, initially designed for working with Java but now extended to support Web and mobile development and even to build Windows applications.

Jenkins is perhaps best thought of as a switching network, shunting files through a test and build process, and responding to signals from the various tools you’re using – thanks to a library of more than 1,000 plug-ins. These include tools for integrating Jenkins with both local Git instances and GitHub so that it's possible to extend a continuous development model into your build and delivery processes.

Using an automation tool like Jenkins is as much about adopting a philosophy as it is about implementing a build process. Once you commit to continuous integration as part of a continuous delivery model, you’ll be running test and build cycles as soon as code is delivered to your source control release branch – and delivering it to users as soon as it’s in the main branch.

### Node.js and io.js

Modern cloud applications are built using different design patterns from the familiar n-tier enterprise and Web apps. They’re distributed, event-driven collections of services that can be quickly scaled and can support many thousands of simultaneous users. One key technology in this new paradigm is [Node.js](https://nodejs.org/en/), used by many major cloud platforms and easy to install as part of a thin server or container on cloud infrastructure.

Key to the success of Node.js is the Npm package format, which allows you to quickly install extensions to the core Node.js service. These include frameworks like Express and Seneca, which help build scalable applications. A central registry handles package distribution, and dependencies are automatically installed.

While the [io.js](https://iojs.org/en/) fork exposed issues with project governance, it also allowed a group of developers to push forward adding ECMAScript 6 support to an Npm-compatible engine. After reconciliation between the two teams, the Node.js and io.js codebases have been merged, with new releases now coming from the io.js code repository.

Other forks, like Microsoft’s io.js fork to add support for its 64-bit Chakra JavaScript engine alongside Google’s V8, are likely to be merged back into the main branch over the next year, keeping the Node.js platform evolving and cementing its role as the preferred host for cloud-scale microservices.

### Seneca

The developers of the [Seneca](http://senecajs.org/) microservice framework have a motto: “Build it now, scale it later!” It’s an apt maxim for anyone thinking about developing microservices, as it allows you to start small, then add functionality as your service grows.

Seneca is at heart an implementation of the actor/message design pattern, focused on using Node.js as a switching engine that takes in messages, processes their contents, and sends an appropriate response, either to the message originator or to another service. By focusing on the message patterns that map to business use cases, it’s relatively easy to take Seneca and quickly build a minimum viable product for your application. A plug-in architecture makes it easy to integrate Seneca with other tools and to quickly add functionality to your services.

You can easily add new patterns to your codebase or break existing patterns into separate services as the needs of your application grow or change. One pattern can also call another, allowing quick code reuse. It’s also easy to add Seneca to a message bus, so you can use it as a framework for working with data from Internet of things devices, as all you need to do is define a listening port where JSON data is delivered.

Services may not be persistent, and Seneca gives you the option of using a built-in object relational mapping layer to handle data abstraction, with plug-ins for common databases.

### .Net Core and ASP.Net vNext

Microsoft’s open-sourcing of .Net is bringing much of the company’s Web platform into the open. The new [.Net Core](https://dotnet.github.io/) release runs on Windows, on OS X, and on Linux. Currently migrating from Microsoft’s Codeplex repository to GitHub, .Net Core offers a more modular approach to .Net, allowing you to install the functions you need as you need them.

Currently under development is [ASP.Net 5](http://www.asp.net/vnext), an open source version of the Web platform, which runs on .Net Core. You can work with it as the basis of Web apps using Microsoft’s MVC 6 framework. There’s also support for the new SignalR libraries, which add support for WebSockets and other real-time communications protocols.

If you’re planning on using Microsoft’s new Nano server, you’ll be writing code against .Net Core, as it’s designed for thin environments. The new DNX, the .Net Execution environment, simplifies deployment of ASP.Net applications on a wide range of platforms, with tools for packaging code and for booting a runtime on a host. Features are added using the NuGet package manager, letting you use only the libraries you want.

Microsoft’s open source .Net is still very young, but there’s a commitment in Redmond to ensure it’s successful. Support in Microsoft’s own next-generation server operating systems means it has a place in both the data center and the cloud.

### GlusterFS

[GlusterFS](http://www.gluster.org/) is a distributed file system. Gluster aggregates various storage servers into one large parallel network file system. You can [even use it in place of HDFS in a Hadoop cluster](http://www.gluster.org/community/documentation/index.php/Hadoop) or in place of an expensive SAN system -- or both. While HDFS is great for Hadoop, having a general-purpose distributed file system that doesn’t require you to transfer data to another location to analyze it is a key advantage.

In an era of commoditized hardware, commoditized computing, and increased performance and latency requirements, buying a big, fat expensive EMC SAN and hoping it fits all of your needs (it won’t) is no longer your sole viable option. GlusterFS was acquired by Red Hat in 2011.

## The best open source networking and security software

BIND, Sendmail, OpenSSH, Cacti, Nagios, Snort -- open source software seems to have been invented for networks, and many of the oldies and goodies are still going strong. Among our top picks in the category this year, you'll find a mix of stalwarts, mainstays, newcomers, and upstarts perfecting the arts of network management, security monitoring, vulnerability assessment, rootkit detection, and much more.
  - [Icinga 2](#icinga-2)
  - [Zenoss Core](#zenoss-core)
  - [OpenNMS](#opennms)
  - [Security Onion](#security-onion)
  - [Kali Linux](#kali-linux)
  - [OpenVAS](#openvas)
  - [OWASP](#owasp)
  - [BeEF](#beef)
  - [Unhide](#unhide)

### Icinga 2

Icinga began life as a fork of system monitoring application Nagios. [Icinga 2](https://www.icinga.org/icinga/icinga-2/) was completely rewritten to give users a modern interface, support for multiple databases, and an API to integrate numerous extensions. With out-of-the-box load balancing, notifications, and configuration, Icinga 2 shortens the time to installation for complex environments. Icinga 2 supports Graphite natively, giving administrators real-time performance graphing without any fuss. But what puts Icinga back on the radar this year is its release of Icinga Web 2, a graphical front end with drag-and-drop customizable dashboards and streamlined monitoring tools.

Administrators can view, filter, and prioritize problems, while keeping track of which actions have already been taken. A new matrix view lets administrators view hosts and services on one page. You can view events over a particular time period or filter incidents to understand which ones need immediate attention. Icinga Web 2 may boast a new interface and zippier performance, but all the usual commands from Icinga Classic and Icinga Web are still available. That means there is no downtime trying to learn a new version of the tool.

### Zenoss Core

Another open source stalwart, [Zenoss Core](https://www.zenoss.com/) gives network administrators a complete, one-stop solution for tracking and managing all of the applications, servers, storage, networking components, virtualization tools, and other elements of an enterprise infrastructure. Administrators can make sure the hardware is running efficiently and take advantage of the modular design to plug in ZenPacks for extended functionality.

Zenoss Core 5, released in February of this year, takes the already powerful tool and improves it further, with an enhanced user interface and expanded dashboard. The Web-based console and dashboards were already highly customizable and dynamic, and the new version now lets administrators mash up multiple component charts onto a single chart. Think of it as the tool for better root cause and cause/effect analysis.

Portlets give additional insights for network mapping, device issues, daemon processes, production states, watch lists, and event views, to name a few. And new HTML5 charts can be exported outside the tool. The Zenoss Control Center allows out-of-band management and monitoring of all Zenoss components. Zenoss Core has new tools for online backup and restore, snapshots and rollbacks, and multihost deployment. Even more important, deployments are faster with full Docker support.

### OpenNMS

An extremely flexible network management solution, [OpenNMS](http://www.opennms.org/) can handle any network management task, whether it's device management, application performance monitoring, inventory control, or events management. With IPv6 support, a robust alerts system, and the ability to record user scripts to test Web applications, OpenNMS has everything network administrators and testers need. OpenNMS has become, as now a mobile dashboard, called OpenNMS Compass, lets networking pros keep an eye on their network even when they're out and about.

The iOS version of the app, which is available on the iTunes App Store, displays outages, nodes, and alarms. The next version will offer additional event details, resource graphs, and information about IP and SNMP interfaces. The Android version, available on Google Play, displays network availability, outages, and alarms on the dashboard, as well as the ability to acknowledge, escalate, or clear alarms. The mobile clients are compatible with OpenNMS Horizon 1.12 or greater and OpenNMS Meridian 2015.1.0 or greater.

### Security Onion

Like an onion, network security monitoring is made of many layers. No single tool will give you visibility into every attack or show you every reconnaissance or foot-printing session on your company network. [Security Onion](https://security-onion-solutions.github.io/security-onion/) bundles scores of proven tools into one handy Ubuntu distro that will allow you to see who's inside your network and help keep the bad guys out.

Whether you're taking a proactive approach to network security monitoring or following up on a potential attack, Security Onion can assist. Consisting of sensor, server, and display layers, the Onion combines full network packet capture with network-based and host-based intrusion detection, and it serves up all of the various logs for inspection and analysis.

The star-studded network security toolchain includes Netsniff-NG for packet capture, Snort and Suricata for rules-based network intrusion detection, Bro for analysis-based network monitoring, OSSEC for host intrusion detection, and Sguil, Squert, Snorby, and ELSA (Enterprise Log Search and Archive) for display, analysis, and log management. It’s a carefully vetted collection of tools, all wrapped in a wizard-driven installer and backed by thorough documentation, that can help you get from zero to monitoring as fast as possible.

### Kali Linux

The team behind [Kali Linux](https://www.kali.org/) revamped the popular security Linux distribution this year to make it faster and even more versatile. Kali sports a new 4.0 kernel, improved hardware and wireless driver support, and a snappier interface. The most popular tools are easily accessible from a dock on the side of the screen. The biggest change? Kali Linux is now a rolling distribution, with a continuous stream of software updates. Kali's core system is based on Debian Jessie, and the team will pull packages continuously from Debian Testing, while continuing to add new Kali-flavored features on top.

The distribution still comes jam-packed with tools for penetration testing, vulnerability analysis, security forensics, Web application analysis, wireless networking and assessment, reverse engineering, and exploitation tools. Now the distribution has an upstream version checking system that will automatically notify users when updates are available for the individual tools. The distribution also features ARM images for a range of devices, including Raspberry Pi, Chromebook, and Odroids, as well as updates to the NetHunter penetration testing platform that runs on Android devices. There are other changes too: Metasploit Community/Pro is no longer included, because Kali 2.0 is not yet [officially supported by Rapid7](https://community.rapid7.com/community/metasploit/blog/2015/08/12/metasploit-on-kali-linux-20).

### OpenVAS

[OpenVAS](http://www.openvas.org/), the Open Vulnerability Assessment System, is a framework that combines multiple services and tools to offer vulnerability scanning and vulnerability management. The scanner is coupled with a weekly feed of network vulnerability tests, or you can use a feed from a commercial service. The framework includes a command-line interface (so it can be scripted) and an SSL-secured, browser-based interface via the [Greenbone Security Assistant](http://www.greenbone.net/). OpenVAS accommodates various plug-ins for additional functionality. Scans can be scheduled or run on-demand.

Multiple OpenVAS installations can be controlled through a single master, which makes this a scalable vulnerability assessment tool for enterprises. The project is as compatible with standards as can be: Scan results and configurations are stored in a SQL database, where they can be accessed easily by external reporting tools. Client tools access the OpenVAS Manager via the XML-based stateless OpenVAS Management Protocol, so security administrators can extend the functionality of the framework. The software can be installed from packages or source code to run on Windows or Linux, or downloaded as a virtual appliance.

### OWASP

[OWASP](https://www.owasp.org/index.php/Main_Page), the Open Web Application Security Project, is a nonprofit organization with worldwide chapters focused on improving software security. The community-driven organization provides test tools, documentation, training, and almost anything you could imagine that’s related to assessing software security and best practices for developing secure software. Several OWASP projects have become valuable components of many a security practitioner's toolkit:

[ZAP](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project), the Zed Attack Proxy Project, is a penetration test tool for finding vulnerabilities in Web applications. One of the design goals of ZAP was to make it easy to use so that developers and functional testers who aren't security experts can benefit from using it. ZAP provides automated scanners and a set of manual test tools.

The [Xenotix XSS Exploit Framework](https://www.owasp.org/index.php/OWASP_Xenotix_XSS_Exploit_Framework) is an advanced cross-site scripting vulnerability detection and exploitation framework that runs scans within browser engines to get real-world results. The Xenotix Scanner Module uses three intelligent fuzzers, and it can run through nearly 5,000 distinct XSS payloads. An API lets security administrators extend and customize the exploit toolkit.

[O-Saft](https://www.owasp.org/index.php/O-Saft), or the OWASP SSL advanced forensic tool, is an SSL auditing tool that shows detailed information about SSL certificates and tests SSL connections. This command-line tool can run online or offline to assess SSL security such as ciphers and configurations. O-Saft provides built-in checks for common vulnerabilities, and you can easily extend these through scripting. In May 2015 a simple GUI was added as an optional download.

[OWTF](https://www.owasp.org/index.php/OWASP_OWTF), the Offensive Web Testing Framework, is an automated test tool that follows OWASP testing guidelines and the NIST and PTES standards. The framework uses both a Web UI and a CLI, and it probes Web and application servers for common vulnerabilities such as improper configuration and unpatched software

### BeEF

The Web browser has become the most common vector for attacks against clients. [BeEF](http://www.beefproject.com/), the Browser Exploitation Framework Project, is a widely used penetration tool to assess Web browser security. BeEF helps you expose the security weaknesses of client systems using client-side attacks launched through the browser. BeEF sets up a malicious website, which security administrators visit from the browser they want to test. BeEF then sends commands to attack the Web browser and use it to plant software on the client machine. Administrators can then launch attacks on the client machine as if they were zombies.

BeEF comes with commonly used modules like a key logger, a port scanner, and a Web proxy, plus you can write your own modules or send commands directly to the zombified test machine. BeEF comes with a handful of demo Web pages to help you get started and makes it very easy to write additional Web pages and attack modules so you can customize testing to your environment. BeEF is a valuable test tool for assessing browser and endpoint security and for learning how browser-based attacks are launched. Use it to put together a demo to show your users how malware typically infects client devices.

### Unhide

[Unhide](http://www.unhide-forensics.info/) is a forensic tool that locates open TCP/UDP ports and hidden process on UNIX, Linux, and Windows. Hidden ports and processes can be the result of rootkit or LKM (loadable kernel module) activity. Rootkits can be difficult to find and remove because they are designed to be stealthy, hiding themselves from the OS and user. A rootkit can use LKMs to hide its processes or impersonate other processes, allowing it to run on machines undiscovered for a long time. Unhide can provide the assurance that administrators need to know their systems are clean.

Unhide is really two separate scripts: one for processes and one for ports. The tool interrogates running processes, threads, and open ports and compares this info to what's registered with the system as active, reporting discrepancies. Unhide and WinUnhide are extremely lightweight scripts that run from the command line to produce text output. They're not pretty, but they are extremely useful. Unhide is also included in the [Rootkit Hunter](https://rootkit.nl/projects/rootkit_hunter.html) project.
