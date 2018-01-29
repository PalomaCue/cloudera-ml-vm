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
* <a href="https://docs.anaconda.com/anaconda/user-guide/tasks/integration/cloudera" > Anaconda in Cloudera CDH </a> 

Anaconda empowers the entire data science team -  data engineers, data scientists, and business analysts - to analyze data in Hadoop and deliver high value, high impact predictive and machine learning solutions with Python.

Anaconda can be installed on a CDH cluster as a parcel.

* <a href="https://jupyterhub.readthedocs.io/en/latest/" > JupyterHub </a> 

With JupyterHub you can create a multi-user Hub which spawns, manages, and proxies multiple instances of the single-user Jupyter notebook server.

Project Jupyter created JupyterHub to support many users. The Hub can offer notebook servers to a class of students, a corporate data science workgroup, a scientific research project, or a high performance computing group.




## Instalation


### <a href="https://docs.anaconda.com/anaconda/user-guide/tasks/integration/cloudera"> Anaconda on Cloudera CDH </a>  

To install the Anaconda parcel:

1. In the Cloudera Manager Admin Console, in the top navigation bar, click the Parcels icon.

2. At the top right of the parcels page, click the Edit Settings button.

3. In the Remote Parcel Repository URLs section, click the plus symbol, and then add the following repository URL for the Anaconda parcel:

4. At the top of the page, click the Save Changes button.

5. In the top navigation bar, click the Parcels icon to return to the list of available parcels, where you should see the latest version of the Anaconda parcel that is available.

6. To the right of the Anaconda parcel listing, click the Download button.

7. After the parcel is downloaded, click the Distribute button to distribute the parcel to all of the cluster nodes.

8. After the parcel is distributed, click the Activate button to activate the parcel on all of the cluster nodes.

When prompted, confirm the activation.

After the parcel is activated, Anaconda is available on all of the cluster nodes.




## References & more info
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>
* <a href="https://www.cloudera.com/products/open-source/apache-hadoop/key-cdh-components.html">CDH Components</a>
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>


* <a href="https://www.anaconda.com/blog/developer-blog/using-anaconda-pyspark-distributed-language-processing-hadoop-cluster/">Using Anaconda with Pyspark for Distributed Language Processing on a Hadoop Cluster</a> (April 12th 2016)
* <a href="https://www.anaconda.com/blog/developer-blog/self-service-open-data-science-custom-anaconda-parcels-cloudera-cdh/">Custom Anaconda Parcels for Cloudera CDH</a> (October 31st 2016)

Pay attention to the versions, because these last two posts could be a little deprecated.
