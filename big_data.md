# Big Data

Key architecture layers:

![Big Data](https://github.com/rkq/docs/blob/master/pics/big_data.jpg)

* File Systems - Distributed file systems which provide storage, fault tolerance, scalability, reliability, and availability.
* Data Stores - Evolution of application databases into Polyglot storage with application specific databases instead of one size fits all. Common ones are Key-Value, Document, Column and Graph.
* Resource Managers - provide resource management capabilities and support schedulers for high utilization and throughput.
* Coordination - systems that manage state, distributed coordination, consensus and lock management.
* Computational Frameworks - a lot of work is happening at this layer with highly specialized compute frameworks for Streaming, Interactive, Real Time, Batch and Iterative Graph (BSP) processing. Powering these are complete computation runtimes like BDAS (Spark) & Flink.
* DataAnalytics – Analytical (consumption) tools and libraries, which support exploratory, descriptive, predictive, statistical analysis and machine learning.
* Data Integration – these include not only the orchestration tools for managing pipelines but also metadata management.
* Operational Frameworks – these provide scalable frameworks for monitoring & benchmarking.