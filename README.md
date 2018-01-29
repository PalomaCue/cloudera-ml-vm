# Cloudera Machine Learning Virtual Machine
Cloudera Quickstart 5.12 Virtual Machine provisioned with Machine Learning and streaming tools. 
 
This instance shows how to provide the CDH virtual machine with any other tools that could be required for Machine Learning purposes. 

I aim to train with a unique machine in a pseudodistributed cluster, the first step Cloudera proposes, just for educational use. 

## Contents of Cloudera distribution of Apache Hadoop (CDH).
The <a href="https://www.cloudera.com/downloads/quickstart_vms/5-12.html" >Cloudera Quickstart 5.12 Virtual Machine</a> includes:
* Apache HBase
* Apache Hive & Hive on Spark
* Apache Impala
* Apache Oozie
* Apache Solr
* Apache Spark
* Apache Squoop 1 & 2
* Apache YARN
* Apache Zookeper
* HDFS
* Hue 4
* ...
Other open source available applications are:
* Cloudera Manager
* Cloudera Navigator
* Cloudera Search



## Contents of CDH4ML
Based on CDH 5.12.0, I have added this tools:
* <a href="https://docs.anaconda.com/anaconda/user-guide/tasks/integration/cloudera" >Anaconda 4.3.1 distribution</a> 
* <a href="https://github.com/jupyterhub/jupyterhub" > JupyterHub </a>
* Apache Kafka 
* Apache Flink
* Apache Flume
* ...



## About
* <a href="https://jupyterhub.readthedocs.io/en/latest/" > JupyterHub </a> 

With JupyterHub you can create a multi-user Hub which spawns, manages, and proxies multiple instances of the single-user Jupyter notebook server.

Project Jupyter created JupyterHub to support many users. The Hub can offer notebook servers to a class of students, a corporate data science workgroup, a scientific research project, or a high performance computing group.




## Instalation





## References & more info
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>
* <a href="https://www.cloudera.com/products/open-source/apache-hadoop/key-cdh-components.html">CDH Components</a>
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>


* <a href="https://www.anaconda.com/blog/developer-blog/using-anaconda-pyspark-distributed-language-processing-hadoop-cluster/">Using Anaconda with Pyspark for Distributed Language Processing on a Hadoop Cluster</a> (April 12th 2016)
* <a href="https://www.anaconda.com/blog/developer-blog/self-service-open-data-science-custom-anaconda-parcels-cloudera-cdh/">Custom Anaconda Parcels for Cloudera CDH</a> (October 31st 2016)

Pay attention to the versions, because these last two posts could be a little deprecated.
