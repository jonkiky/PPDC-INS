---
description: >-
  for project index of NCI-funded Studies)    PPDC(Pediatric Preclinical Data
  Commons)
---

# OpenTargets & Bento Learning Material

## **OpenTargets&Bento Overview**

### **OpenTarget** 

#### **Introduction**

 **TBD**  


**The new version of open target:**  [**https://beta.targetvalidation.org/**](https://beta.targetvalidation.org/)

**The new version is expected to be released in Q1 2021.**   
  


#### **Repos**

 ****[**platform-app**](https://github.com/opentargets/platform-app) **- React UI**

[**platform-api-beta**](https://github.com/opentargets/platform-api-beta) **- GraphQL API**

[**platform-input-support**](https://github.com/opentargets/platform-input-support) **- scripts that process and prepare data for our ETL pipelines** 

[**platform-etl-backend**](https://github.com/opentargets/platform-etl-backend) **- ETL pipelines to generate associations, evidence, and entity indices** 

[**platform-etl-openfda-faers**](https://github.com/opentargets/platform-etl-openfda-faers) **- ETL pipeline to process OpenFDA adverse events data**

[**json\_schema**](https://github.com/opentargets/json_schema) **- evidence object schema used by ETL pipelines for evidence and association scoring**  
  


#### **Documentation** 

 **No docs are available at the moment.**   


#### **Support**

 **General: contact@opentargets.org &lt;**[**contact@opentargets.org**](mailto:contact@opentargets.org)**&gt;**

 **Got response from Andrew Hercules &lt;**[**ahercules@ebi.ac.uk**](mailto:ahercules@ebi.ac.uk)**&gt;**

#### **Observations**

**Front-end:** [**https://github.com/opentargets/platform-app**](https://github.com/opentargets/platform-app) ****

**It is a react application.  It can be set up and run locally easily.**  


**Back-end** [**https://github.com/opentargets/platform-api-beta**](https://github.com/opentargets/platform-api-beta)  ****

**Program:**

* **Scala and play framework.  → java & Spring** 
* **GraphQL:  They construct the graphql from scratch, we need to understand the concept of graphql.** 

**Database :  Clickhouse and Elasticsearch.**   


**Tech Stack**

* **Scala   https://www.scala-lang.org/**
* **PlayFramework : https://www.playframework.com/** 
* **Clickhouse  https://clickhouse.tech/**
* **Elasticsearch https://www.elastic.co/**
* **GraphQL** [**https://graphql.org/**](https://graphql.org/) ****[**https://www.howtographql.com/graphql-scala/0-introduction/**](https://www.howtographql.com/graphql-scala/0-introduction/) **https://graphql.org/community/** 
* **AKKA HTTP Server https://akka.io/**

**Others**

**Old Frontend:** [**https://github.com/opentargets/webapp**](https://github.com/opentargets/webapp)

**Old Backend:** [**https://github.com/opentargets/rest\_api**](https://github.com/opentargets/rest_api)

**Old Documentation:** [**https://docs.targetvalidation.org/faq/spin-your-own-instance**](https://docs.targetvalidation.org/faq/spin-your-own-instance)

**Old Version:** [**https://www.targetvalidation.org/**](https://www.targetvalidation.org/)

### **Bento**

#### **Introduction**

 **TBD**

#### **Repos**

[**https://github.com/CBIIT/bento-tools**](https://github.com/CBIIT/bento-tools)

[**https://github.com/CBIIT/bento-frontend**](https://github.com/CBIIT/bento-frontend)

[**https://github.com/CBIIT/bento-backend/tree/3.0.0**](https://github.com/CBIIT/bento-backend/tree/3.0.0)

#### **Documentation** 

 ****[**https://github.com/CBIIT/bento-docs**](https://github.com/CBIIT/bento-docs) ****

 ****[**https://cbiit.github.io/bento-docs/master/index.html**](https://cbiit.github.io/bento-docs/master/index.html)

#### **Support**

**Backend:  Ming ying**   [**ming.ying@nih.gov**](mailto:ming.ying@nih.gov) ****

**Front-end:  Sri kiran**   [**srikiran.chaparala@nih.gov**](mailto:srikiran.chaparala@nih.gov)

                      **Ajay**  [**ajay.doddapaneni@nih.gov**](mailto:ajay.doddapaneni@nih.gov)   
  
  
  
  
****

## **OpenTarget Installation**

### **Database** 

#### **Clickhouse** 

[**https://clickhouse.tech/docs/en/getting-started/install/**](https://clickhouse.tech/docs/en/getting-started/install/)   
****

**System Requirements** 

**ClickHouse can run on any Linux, FreeBSD, or Mac OS X with x86\_64, AArch64, or PowerPC64LE CPU architecture.**

**Document:**

**Install from source can be found here \(for Mac user\) :** 

**Windows users have to install the linux system in VB, in order to use the CH. will find it out later.  For Mac and linux users, the steps to install the CH are largely the same.** 

[**https://clickhouse.tech/docs/en/development/build-osx/**](https://clickhouse.tech/docs/en/development/build-osx/)  
****

**Support:**  

**Telegram  https://telegram.me/clickhouse\_en**  


**Command line** 

**./clickhouse-server --config-file=/Users/jonkiky/Documents/work/openTarget/ClickHouse/programs/server/config.xml**  


**Possible Issues :**

![](https://lh5.googleusercontent.com/2IpyormoZPisU-Z_eSWHZQ_Cuin8xkT8z430BKkY_lrblRQAiXZ2o-oVUoVb9UYxOt4SfodYvZ6rNXo_GbKzxmolxjnXjadtA2MW7R6v---6Zp_mhd1H43ixqimCbft17K4M6Ov7)

**Fails at  DB::Exception: ClickHouse server built without NuRaft library.**  


**Solution:**

**Remove zookeeper settings and test zookeeper settings.**  

**Modify --ClickHouse/programs/server/config.d/zookeeper.xml**

![](https://lh5.googleusercontent.com/D02sDz_RuMapR9qdi9ktHGpTqD2dyaaosTXcVf2F9oIjuWx3D0RT0toYLJ8efL0SHwTbRMm5W6hXx4OCfckVKQ4Oytc639uRK4l4tbhhvbJRVocUPWfDl8xRo7cb_dIdIgUQJRQT)

**Delete -- ClickHouse/programs/server/config.d/**[**test\_keeper\_port.xml**](https://github.com/ClickHouse/ClickHouse/blob/master/programs/server/config.d/test_keeper_port.xml)

**Refers :** [**https://github.com/ClickHouse/ClickHouse/issues/4105**](https://github.com/ClickHouse/ClickHouse/issues/4105)

#### **Elasticsearch**

**According to repo platform-api-beta\(** [**https://github.com/opentargets/platform-api-beta**](https://github.com/opentargets/platform-api-beta)**\), open target will use ES server 7.2, Port: 9200.** 

**CH uses Port 9000.**   


**Download link:** [**https://www.elastic.co/downloads/past-releases/elasticsearch-7-2-0**](https://www.elastic.co/downloads/past-releases/elasticsearch-7-2-0)  
****

**Github:** [**https://github.com/elastic/elasticsearch/tree/7.2**](https://github.com/elastic/elasticsearch/tree/7.2)   
****

**System Requirements** 

 **Java 11** 

**Use homebrew to install Java** 

[**https://devqa.io/brew-install-java/**](https://devqa.io/brew-install-java/)

[**https://github.com/Homebrew/homebrew-cask**](https://github.com/Homebrew/homebrew-cask)  
****

**Setup the java\_home** 

[**https://mkyong.com/java/how-to-set-java\_home-environment-variable-on-mac-os-x/**](https://mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/)

**Document** 

[**https://www.elastic.co/guide/en/elasticsearch/reference/current/targz.html**](https://www.elastic.co/guide/en/elasticsearch/reference/current/targz.html)  
  
****

#### **Scala 2.12.x** 



