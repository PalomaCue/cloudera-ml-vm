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
* <a href="https://www.cloudera.com/documentation/kafka/latest/topics/kafka_installing.html#concept_m2t_d45_4r" >Kafka 3.0.0 </a>
* <a href="https://github.com/mbalassi/flink-parcel" >Apache Flink 1.0.3 </a>
* Apache Flume
* <a href="https://www.cloudera.com/documentation/enterprise/5-3-x/topics/cdh_cm_upgrading_to_jdk8.html" > Java 1.8 </a>
* ...



## About
* <a href="https://docs.anaconda.com/anaconda/user-guide/tasks/integration/cloudera" > Anaconda in Cloudera CDH </a> 

Anaconda empowers the entire data science team -  data engineers, data scientists, and business analysts - to analyze data in Hadoop and deliver high value, high impact predictive and machine learning solutions with Python.

Anaconda can be installed on a CDH cluster as a parcel.

* <a href="https://jupyterhub.readthedocs.io/en/latest/" > JupyterHub </a> 

With JupyterHub you can create a multi-user Hub which spawns, manages, and proxies multiple instances of the single-user Jupyter notebook server.

Project Jupyter created JupyterHub to support many users. The Hub can offer notebook servers to a class of students, a corporate data science workgroup, a scientific research project, or a high performance computing group.

* <a href="https://www.python.org/download/releases/3.4.3/" > Python 3.4.3 </a> 




## Instalation


### <a href="https://docs.anaconda.com/anaconda/user-guide/tasks/integration/cloudera"> Anaconda on Cloudera CDH </a>  

There are two methods of using Anaconda on an existing cluster with Cloudera CDH, Cloudera’s distribution including Apache Hadoop:

* Use the Anaconda parcel for Cloudera CDH. The following procedure describes how to install the Anaconda parcel on a CDH cluster using Cloudera Manager. The Anaconda parcel provides a static installation of Anaconda, based on Python 2.7, that can be used with Python and PySpark jobs on the cluster.
* Use Anaconda Scale, which provides additional functionality, including the ability to manage multiple conda environments and packages, including Python and R, alongside an existing CDH cluster. For more information, see Using Anaconda with Cloudera CDH.

<i> I am going to use the first method. Basically because is open source, althought we have several limitations that I will try to solve.</i>

To install the Anaconda parcel:

1. In the Cloudera Manager Admin Console, in the top navigation bar, click the Parcels icon.
2. At the top right of the parcels page, click the Edit Settings button.
3. In the Remote Parcel Repository URLs section, click the plus symbol, and then add the following repository URL for the Anaconda parcel:
4. At the top of the page, click the Save Changes button.
5. In the top navigation bar, click the Parcels icon to return to the list of available parcels, where you should see the latest version of the Anaconda parcel that is available.
6. To the right of the Anaconda parcel listing, click the Download button.
7. After the parcel is downloaded, click the Distribute button to distribute the parcel to all of the cluster nodes.
8. After the parcel is distributed, click the Activate button to activate the parcel on all of the cluster nodes.
9. When prompted, confirm the activation.

After the parcel is activated, Anaconda is available on all of the cluster nodes.

You can submit Spark jobs along with the `PYSPARK_PYTHON` environment variable that refers to the location of Anaconda. For example, enter the following command all on one line:

    PYSPARK_PYTHON=/opt/cloudera/parcels/Anaconda/bin/python spark-submit pyspark_script.py


NOTE: The line break in the example above is for readability only. Enter the command all on one line.

NOTE: The repository URL shown above installs the most recent version of the Anaconda parcel. To install an older version of the Anaconda parcel, add the following repository URL to the Remote Parcel Repository URLs in Cloudera manager, and then follow the above steps with your desired version of the Anaconda parcel.

<i> Anaconda builds new Cloudera parcels at least once a year each spring and also offers custom parcel creation for our enterprise customers. The Anaconda parcel provided at the repository URL shown above is based on Python 2.7.</i>


### <a href="https://www.cloudera.com/documentation/spark2/latest/topics/spark2_installing.html"> Installing Apache Spark 2 on Cloudera CDH </a>  

I followed the steps to install Spark 2:

1. See <a href="https://www.cloudera.com/documentation/spark2/latest/topics/spark2_requirements.html#scala_version"> Spark 2 Requirements </a> and check them.

2. Install the Spark 2 CSD into Cloudera Manager. 

Log on to the Cloudera Manager Server host, and place the Spark 2 CSD file in the location configured for CSD files. Set the file ownership of the CSD file to `cloudera-scm:cloudera-scm` with permission 644. Or what is the same, a little more slowly:

 a. Download <a href="https://www.cloudera.com/documentation/spark2/latest/topics/spark2_packaging.html#versions"> the Spark 2 CSD </a>.   I choose the last version (version 2.2, relase 2).
 
 b. Upload the CSD to `/opt/cloudera/csd` in the Cloudera Manager server.
 
 c. Change the owner and group for the JAR:
 
     sudo chown cloudera-scm:cloudera-scm /opt/cloudera/csd/SPARK2_ON_YARN-2.2.0.cloudera2.jar
 
 d. Update the permissions on the file:
 
      sudo chmod 644 /opt/cloudera/csd/SPARK2_ON_YARN-2.2.0.cloudera2.jar
 
 e. Restart the Cloudera Manager server:
    As the root user on the Cloudera Manager server, run 
    
       sudo service cloudera-scm-server restart
    
   Log in to the Cloudera Manager Admin Console and restart the Cloudera Manager Service with:
    
       sudo service cloudera-scm-agent restart
 
 f. Check whether the CSD successfully installed in http://quickstart.cloudera:7180/cmf/csd/refresh. Search for the following entry:


    {
    "csdName":"SPARK2_ON_YARN-2.2.0.cloudera2",
    "serviceType":"SPARK2_ON_YARN",
    "source":"/opt/cloudera/csd/SPARK2_ON_YARN-2.2.0.cloudera2.jar",
    "isInstalled":true
    }
 
 g. Restart the Cloudera Manager Server with the following command:
         
      sudo service cloudera-scm-server restart

3. In the Cloudera Manager Admin Console, add the <a href="https://www.cloudera.com/documentation/spark2/latest/topics/spark2_packaging.html#packaging"> Spark2 parcel repository </a> to the Remote Parcel Repository URLs in Parcel Settings as described in <a href="https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_parcels.html#cmug_topic_7_11_5__section_sd4_bzx_bm"> remote repository URLs.</a>

4. Download the Spark 2 parcel, distribute the parcel to the hosts in your cluster, and activate the parcel. See <a href="https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_parcels.html#concept_vwq_421_yk"> Managing Parcels. </a>

5. Add the Spark 2 service to your cluster.

 a. In the step #1, select a dependency option:
 
  *  HDFS, YARN, ZooKeeper: Choose this option if you do not need access to a Hive service.

  *  HDFS, Hive, YARN, ZooKeeper: Hive is an optional dependency for the Spark service. If you have a Hive service and want to access Hive tables from your Spark applications, choose this option to include Hive as a dependency and have the Hive client configurations always available to Spark applications.
  
  I chose the second option. Without Hive dependencies.
   
  b. In the step #2, when customizing the role assignments for Spark 2, DO NOT ADD the <a href="https://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_managing_roles.html"> gateway role </a> to every host. Inf fact, in our case is not needed. We do not have a NODO FRONTERA, because we do not have a "real" cluster. Thas why the only ...

  c. Note that the History Server port is 18089 instead of the usual 18088.  ***CHECK IT***

  d. Complete the steps to add the Spark 2 service.

  e.  Return to the Home page by clicking the Cloudera Manager logo.
  
  f.  Click  to restart the cluster.
  
  
  
## Installing Java 8 (Oracle JDK)
------------------------
FAILED
In order to install Oracle Java 8 JDK, I will need to go to the Oracle Java 8 JDK Downloads Page, accept the license agreement, and copy the download link of the appropriate Linux .rpm package. Substitute the copied download link in place of the highlighted part of the wget command.

I have changed to my home directory and downloaded the Oracle Java 8 JDK RPM with these commands:

    $ cd ~
    $ wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://link_copied_from_site"
--------------------------------

The Oracle JDK installer is available both as an RPM-based installer for RPM-based systems, and as a binary installer for other systems.

1. Download the `.tar.gz` file for one of the supported versions of the Oracle JDK from Java SE 8 Downloads.

2. Extract the JDK to `/usr/java/jdk.1.8.`

3. Set JAVA_HOME to the directory where the JDK is installed. Add the following line to the specified files:

    export JAVA_HOME=/usr/java/jdk.1.7.0_nn

 - Cloudera Manager Server host: /etc/default/cloudera-scm-server. This affects only the Cloudera Manager Server process, and does not affect the Cloudera Management Service roles.

- All hosts in an unmanaged deployment (!!): `/etc/default/bigtop-utils`. You do not need to do this for clusters managed by Cloudera Manager.

4. Follow the instructions in Configuring a Custom Java Home Location. This change affects all CDH processes and Cloudera Management Service roles in the cluster.

## References & more info
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>
* <a href="https://www.cloudera.com/products/open-source/apache-hadoop/key-cdh-components.html">CDH Components</a>
* <a href="https://docs.anaconda.com/anaconda-scale/spark">Using Anaconda with Spark</a>
* <a href="https://docs.anaconda.com/anaconda/packages/pkg-docs"> Anaconda Packages included by default </a> 
* <a href="https://jupyterhub.readthedocs.io/en/latest/quickstart.html#prerequisites"> Installing JupyterHub </a> 
* <a href="https://docs.anaconda.com/anaconda/packages/py3.5_linux-64"> Packages for 64-bit Linux with Python 3.5 </a> 
* <a href="https://www.cloudera.com/documentation/enterprise/5-6-x/topics/spark_python.html"> Running Spark Python Applications </a> 
* <a href="https://www.cloudera.com/documentation/enterprise/5-7-x/topics/spark_ipython.html#ipython"> Running Spark Applications Using IPython and Jupyter Notebooks </a> 
 


* <a href="https://www.anaconda.com/blog/developer-blog/using-anaconda-pyspark-distributed-language-processing-hadoop-cluster/">Using Anaconda with Pyspark for Distributed Language Processing on a Hadoop Cluster</a> (April 12th 2016)
* <a href="https://www.anaconda.com/blog/developer-blog/self-service-open-data-science-custom-anaconda-parcels-cloudera-cdh/">Custom Anaconda Parcels for Cloudera CDH</a> (October 31st 2016)
* <a href="http://blog.cloudera.com/blog/2016/02/making-python-on-apache-hadoop-easier-with-anaconda-and-cdh/"> Making Python on Apache Hadoop Easier with Anaconda and CDH </a> 

Pay attention to the versions, because these last three posts could be a little deprecated. 

*  <a href="https://www.cloudera.com/documentation/enterprise/release-notes/topics/rn_consolidated_pcm.html"> CDH 5 and Cloudera Manager 5 Requirements and Supported Versions </a>

## Even more
* <a href="http://recordservice.io/installOnCluster/"> Installing RecordService on Your CDH Cluster </a>
* <a href="https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_parcels.html#concept_vwq_421_yk"> Managing Parcels. </a>
* <a href="https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora"> How To Install Java on CentOS and Fedora </a>




<i> The main point we should take care would be a matter of versions, specially with Python. To sum up, I could suggest a parcial solution could be install Python 3 manually. One installation per node. We aim to work and visualize notebooks on a mutli-user environment with Jupyther Hub.</i>




## Checking versions:

#### Centos Version

    $ rpm --query centos-release
    
or...
    
    $ lsb_release -d
    
    
<a href="https://linuxconfig.org/how-to-check-centos-version"> See more </a>.

#### Java version

    java -version
    
    

    


