# Awesome-Java-Extensibility-Runtime

## Top Java Extensibility & Runtime Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Java UDF Runtimes, Serverless Functions & Self-Hosted Native Compilation*  

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Java Extensibility & Runtime**. These tools enable organizations to execute Java code in managed environments—running UDFs inside databases, deploying serverless functions, and compiling native binaries—leveraging Java's type safety and JVM performance without managing the underlying infrastructure.



**Examples** include Snowflake Java UDFs, Apache Spark Java API, AWS Lambda Java, Google Cloud Functions Java, Azure Functions Java, GraalVM, Red Hat OpenShift Java, Spring Cloud, Quarkus, and Oracle Java SE Subscription (the category leaders).



**Open-source emphasis**: Java Extensibility & Runtime is a domain where open-source tooling is **exceptionally mature but bifurcated between managed runtimes and self-hosted frameworks**. **Quarkus** and **Spring Boot with GraalVM Native Image** are the leading open-source paths for building Java services—Quarkus offers fast startup and low memory footprint via native compilation, while Spring Boot's GraalVM support (verified with Spring MVC and embedded Tomcat) produces statically compiled native executables without a JVM . For serverless extensibility, **AWS Lambda Java** provides official libraries (`aws-lambda-java-core`, `aws-lambda-java-events`) on Maven Central , and **Snowflake Java UDFs** support both array and varargs parameter passing with SQL-Java type mapping . The critical caveat: **GraalVM's native image build is not a drop-in replacement**—it requires reachability metadata configuration and has limited dynamic feature support, though Spring Boot's AOT processing handles much of this automatically .



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Snowflake Java UDFs](https://docs.snowflake.com/en/developer-guide/udf/java/udf-java-designing)**  

  Write UDF handlers in Java and call from SQL. Supports SQL-Java type mapping, array parameters via Java arrays or varargs, and inherits the caller's timezone (IANA database 2025b). Handlers are called once per row; initialization (constructor) has a longer timeout than execution. Best for Snowflake users wanting Java logic in SQL queries .



- **[Apache Spark Java API](https://spark.apache.org/docs/latest/api/java/)**  

  Spark's primary language API is Scala, but Java API provides access to RDDs, DataFrames, and Spark SQL. Spark 4.1.0-preview3 Javadoc available. Best for distributed data processing with Java teams—but Scala remains the more idiomatic choice .



- **[AWS Lambda Java](https://docs.aws.amazon.com/lambda/latest/dg/lambda-java.html)**  

  Serverless compute for Java with runtimes including Java 25, 21, 17, 11, and 8. Handler is a method receiving event and context objects. Official libraries include `aws-lambda-java-core` (required), `aws-lambda-java-events` (event types), `aws-lambda-java-log4j2` (logging), and the Durable Execution SDK for multi-step workflows. Best for AWS-native serverless Java functions .



- **[Google Cloud Functions Java](https://cloud.google.com/functions/docs/concepts/java-runtime)**  

  Cloud Run functions support Java 25, 21, 17, and 11 (with Java 11 deprecated). Uses the Functions Framework for Java. Specify runtime with `--runtime` and entry point with `--entry-point` (fully qualified class name). Best for Google Cloud-native serverless functions .



- **[Azure Functions Java](https://learn.microsoft.com/en-us/azure/azure-functions/functions-reference-java)**  

  Java support for Azure Functions with annotations like `@FunctionName`, `@HttpTrigger`, `@TableInput`, and `@TableOutput`. Supports input/output bindings, POJO serialization, and `OutputBinding<T>` for multiple outputs. Best for Azure-native serverless functions with binding-based integration .



- **[GraalVM](https://www.graalvm.org/)**  

  Polyglot VM with **Native Image** compilation—ahead-of-time compilation of Java to native executables. Eliminates JVM startup overhead, reduces memory footprint, and produces statically linked binaries. Best for CLI tools, microservices, and serverless functions where startup time matters—but requires reachability metadata and has limited dynamic feature support .



- **[Red Hat OpenShift Java](https://www.redhat.com/en/technologies/cloud-computing/openshift)**  

  Enterprise Kubernetes platform with OpenJDK support. **Critical caveat**: default OpenJDK settings do not work in containers—JVM heap defaults to 1/4 of container memory, so explicit `-Xmx` or `-XX:+UseCGroupMemoryLimitForHeap` configuration is mandatory. Best for enterprises running Java on OpenShift .



- **[Spring Cloud](https://spring.io/projects/spring-cloud)**  

  Tools for distributed systems patterns: configuration management, service discovery, circuit breakers, intelligent routing, and distributed messaging. Version 2025.1.x (Oakwood) supports Spring Boot 4.0.x/4.1.x. Works on laptop, bare metal, or managed platforms. Best for Spring Boot teams building microservices .



- **[Quarkus](https://quarkus.io/)**  

  Kubernetes-native Java framework optimized for GraalVM and HotSpot. Fast startup, low memory footprint, and extensive extension ecosystem (Kafka, MongoDB, Redis, Elasticsearch, Cassandra, etc.). Best for cloud-native Java services wanting fast startup and native compilation .



- **[Oracle Java SE Subscription](https://www.oracle.com/java/technologies/javase-subscription.html)**  

  Commercial support for Oracle JDK including Java 8 (which reached end of public updates in April 2019). Provides Premier Support, security patches, and tools like Java Mission Control and Flight Recorder. Best for organizations requiring commercial support for legacy Java versions .



## Open-Source GitHub Projects



### Native Compilation & Cloud-Native Frameworks



- **[Quarkus](https://github.com/quarkusio/quarkus)**  

  The **leading open-source Kubernetes-native Java framework** (Apache 2.0). Optimized for GraalVM Native Image and HotSpot; features fast startup, low memory footprint, and 500+ extensions covering Kafka, MongoDB, Redis, Elasticsearch, Cassandra, and more. Dev Services auto-starts databases and message brokers in dev/test mode. **Best for cloud-native Java services** wanting native compilation and fast startup—but native image builds require reflection configuration for libraries not designed for GraalVM .



- **[Spring Boot](https://github.com/spring-projects/spring-boot)**  

  The most widely adopted Java framework (Apache 2.0) with **GraalVM Native Image support** via Spring AOT. Supports Cloud Native Buildpacks (Paketo Java Native Image buildpack) or GraalVM Native Build Tools. Spring MVC and embedded Tomcat are tested with native images. **Best for Spring ecosystem teams** wanting native compilation without leaving the Spring ecosystem—but native builds require more memory (8GB+ Docker allocation recommended on macOS) and have longer build times .



### Serverless Function Libraries (AWS Lambda)



- **[aws-lambda-java-libs](https://github.com/aws/aws-lambda-java-libs)**  

  Official AWS libraries for Java Lambda functions: **`aws-lambda-java-core`** (required—defines handler interface and context object), **`aws-lambda-java-events`** (event input types), **`aws-lambda-java-log4j2`** (logging appender adding request ID to logs). Available on Maven Central. **Best for AWS Lambda Java functions**—but they are Lambda-specific, not general-purpose runtime libraries .



### Additional Strong Open-Source Options



- **Apache Spark** — Open-source distributed compute engine (Apache 2.0) with Java API for RDDs, DataFrames, and Spark SQL. **Best for Java teams doing distributed data processing**—but Scala is the primary API and Java usage is secondary .

- **Apache Felix Atomos** — OSGi framework for Java modularity; supports dynamic layer addition/removal on Java 9+ and bundle installation from module path/class path. **Best for OSGi-based extensibility**—niche use case for plugin architectures .



**Frameworks for building custom systems**: For **cloud-native Java services with native compilation**, Quarkus or Spring Boot with GraalVM . For **AWS Lambda Java functions**, `aws-lambda-java-core` and related libraries . For **database UDFs**, Snowflake Java UDFs . For **containerized Java on Kubernetes**, configure explicit `-Xmx` or `-XX:+UseCGroupMemoryLimitForHeap` to override JVM heap defaults . No open-source project matches the **managed simplicity and per-second billing** of AWS Lambda Java or Google Cloud Functions Java—self-hosting means owning infrastructure and GraalVM build configuration.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Java runtime platforms handling production code must comply with organizational security policies; **self-hosted solutions place full responsibility for JVM tuning, dependency management, and patching on the operator**.

- **Java extensibility is mature at the framework and serverless layers**—Quarkus and Spring Boot provide production-grade native compilation , and AWS Lambda libraries provide serverless function primitives . However, **GraalVM native image builds are not drop-in replacements**—reachability metadata is required for reflection-heavy libraries, and build times are significantly longer . **Containerized Java requires explicit heap configuration**—OpenJDK's default 1/4 container memory allocation does not work in constrained environments .

- Verify license terms for commercial use; Quarkus and Spring Boot use Apache 2.0, and AWS Lambda libraries are Apache 2.0 .



---



**Made for Java developers, platform engineers, and organizations choosing their runtime and extensibility stack.**  

Let's make Java runtimes more open, but with clear eyes about the native compilation configuration and container heap tuning that self-hosting requires.
