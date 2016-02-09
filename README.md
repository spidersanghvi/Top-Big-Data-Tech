# Top-Big-Data-Tech
a copy of [Bossie awards 2015] (http://www.infoworld.com/article/2982429/open-source-tools/bossie-awards-2015-the-best-open-source-big-data-tools.html) list in a single page

- Tech list
  - [Spark](#spark)
  - [Storm](#storm)

## Spark

With hundreds of contributors, [Spark] (https://spark.apache.org/) is one of the most active and fastest-growing Apache projects, and with heavyweights like IBM throwing their weight behind the project and major corporations bringing applications into large-scale production, the momentum shows no signs of letting up.

The sweet spot for Spark continues to be machine learning. Highlights since last year include the replacement of the SchemaRDD with a Dataframes API, similar to those found in R and Pandas, making data access much simpler than with the raw RDD interface. Also new are ML pipelines for building repeatable machine learning workflows, expanded and optimized support for various storage formats, simpler interfaces to machine learning algorithms, improvements in the display of cluster resources usage, and task tracking.

On by default in Spark 1.5 is the off-heap memory manager, Tungsten, which offers much faster processing by fine-tuning data structure layout in memory. Finally, the new website, [spark-packages.org] (http://spark-packages.org/), with more than 100 third-party libraries, adds many useful features from the community.

## Storm

[Apache Storm](https://storm.apache.org/) is a Clojure-based distributed computation framework primarily for streaming real-time analytics. Storm is based on the [disruptor pattern](https://lmax-exchange.github.io/disruptor/) for low-latency complex event processing created LMAX. Unlike Spark, Storm can do single events as opposed to “micro-batches,” and it has a lower memory footprint. In my experience, it scales better for streaming, especially when you’re mainly streaming to ingest data into other data sources.

Storm’s profile has been eclipsed by Spark, but Spark is inappropriate for many streaming applications. Storm is frequently used with Apache Kafka.
