# OpenTargets Installation

## **Database** 

### **Clickhouse** 

[**https://clickhouse.tech/docs/en/getting-started/install/**](https://clickhouse.tech/docs/en/getting-started/install/)   
****

#### **System Requirements** 

**ClickHouse can run on any Linux, FreeBSD, or Mac OS X with x86\_64, AArch64, or PowerPC64LE CPU architecture.**

#### **Document**

**Install from source can be found here \(for Mac user\) :** 

**Windows users have to install the linux system in VB.**

**For Mac and linux users, the steps to install the CH are largely the same.** 

[**https://clickhouse.tech/docs/en/development/build-osx/**](https://clickhouse.tech/docs/en/development/build-osx/)  
****

#### **Support**

**Telegram  https://telegram.me/clickhouse\_en**  


#### **Command-line** 

**./clickhouse-server --config-file=/Users/jonkiky/Documents/work/openTarget/ClickHouse/programs/server/config.xml**

\*\*\*\*

  
****

#### **Possible Issues** 

![](https://lh5.googleusercontent.com/2IpyormoZPisU-Z_eSWHZQ_Cuin8xkT8z430BKkY_lrblRQAiXZ2o-oVUoVb9UYxOt4SfodYvZ6rNXo_GbKzxmolxjnXjadtA2MW7R6v---6Zp_mhd1H43ixqimCbft17K4M6Ov7)

**Fails at  DB::Exception: ClickHouse server built without NuRaft library.**  


#### **Solution**

**Remove zookeeper settings and test zookeeper settings.**  

**Modify --ClickHouse/programs/server/config.d/zookeeper.xml**

![](https://lh5.googleusercontent.com/D02sDz_RuMapR9qdi9ktHGpTqD2dyaaosTXcVf2F9oIjuWx3D0RT0toYLJ8efL0SHwTbRMm5W6hXx4OCfckVKQ4Oytc639uRK4l4tbhhvbJRVocUPWfDl8xRo7cb_dIdIgUQJRQT)

**Delete -- ClickHouse/programs/server/config.d/**[**test\_keeper\_port.xml**](https://github.com/ClickHouse/ClickHouse/blob/master/programs/server/config.d/test_keeper_port.xml)

**Refers :** [**https://github.com/ClickHouse/ClickHouse/issues/4105**](https://github.com/ClickHouse/ClickHouse/issues/4105)

### **Elasticsearch**

**According to repo platform-api-beta\(** [**https://github.com/opentargets/platform-api-beta**](https://github.com/opentargets/platform-api-beta)**\), open target will use ES server 7.2, Port: 9200.** 

**CH uses Port 9000.   
Download link:** [**https://www.elastic.co/downloads/past-releases/elasticsearch-7-2-0**](https://www.elastic.co/downloads/past-releases/elasticsearch-7-2-0)  
**Github:** [**https://github.com/elastic/elasticsearch/tree/7.2**](https://github.com/elastic/elasticsearch/tree/7.2)   
****

#### **System Requirements** 

 **Java 11** 

**Use homebrew to install Java** 

[**https://devqa.io/brew-install-java/**](https://devqa.io/brew-install-java/)

[**https://github.com/Homebrew/homebrew-cask**](https://github.com/Homebrew/homebrew-cask)  
****

**Setup the java\_home** 

[**https://mkyong.com/java/how-to-set-java\_home-environment-variable-on-mac-os-x/**](https://mkyong.com/java/how-to-set-java_home-environment-variable-on-mac-os-x/)

#### **Document** 

\*\*\*\*[**https://www.elastic.co/guide/en/elasticsearch/reference/current/targz.html**](https://www.elastic.co/guide/en/elasticsearch/reference/current/targz.html)  
****

### **Scala 2.12.x** 

#### **Document**

**Official doc:**

{% embed url="https://docs.scala-lang.org/getting-started/index.html" %}

\*\*\*\*

**Homebrew install** 

{% embed url="https://formulae.brew.sh/formula/scala" %}

Install SDKMAN

{% embed url="https://sdkman.io/install" %}



install sbt by using SDKMAN

{% embed url="https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Mac.html" %}

\*\*\*\*

\*\*\*\*

**Run Front-end** 

1. **Clone code from** [**https://github.com/opentargets/platform-app**](https://github.com/opentargets/platform-app)\*\*\*\*
2.  **It is a react application, so run yarn install or yarn**
3. yarn start 
4. check localhost:3000 to test app is up or not. 

**Run API portal**

1. **Clone  Code from openTargets** [**https://github.com/opentargets/platform-api-beta**](https://github.com/opentargets/platform-api-beta)\*\*\*\*
2. **cd openTargets**
3. **Run sbt**
4. **in the console, run ~run.** 
5. check localhost:9000 to test app is up or not. 



Database import:

download data from FTP

Create Table:

```text
create database if not exists ot;
create table if not exists ot.associations_otf_log(\
    row_id String,\
    disease_id String,\
    target_id String,\
    disease_data Nullable(String),\
    target_data Nullable(String),\
    datasource_id String,\
    datatype_id String,\
    sourceId String,\
    row_score Float64\
) engine = Log;\
```

Import data:

```text
cat part-00* | ./clickhouse-client -h localhost --query="insert into ot.associations_otf_log format JSONEachRow "
```

Check database:

```text
9684736 rows in set. Elapsed: 3.671 sec. Processed 9.68 million rows, 2.51 GB (2.64 million rows/s., 684.65 MB/s.) 

Yizhens-MacBook-Pro.local :) select * from ot.associations_otf_log
```

Create table:

```text
create table if not exists ot.associations_otf_disease \
engine = MergeTree() \
order by (A, B, datasource_id) \
primary key (A) \
as select \
    row_id, \
    A, \
    B, \
    datatype_id, \
    datasource_id, \
    row_score, \
    A_search, \
    B_search  \
from (select  \
        row_id, \
        disease_id as A, \
        target_id as B, \
        datatype_id, \
        datasource_id, \
        row_score, \
        lower(disease_data) as A_search, \
        lower(target_data) as B_search \
    from ot.associations_otf_log); \

create table if not exists ot.associations_otf_target \
engine = MergeTree() \
order by (A, B, datasource_id) \
primary key (A) \
as select \
    row_id, \
    A, \
    B, \
    datatype_id, \
    datasource_id, \
    row_score, \
    A_search, \
    B_search \
from (select  \
        row_id, \
        disease_id as B, \
        target_id as A, \
        datatype_id, \
        datasource_id, \
        row_score, \
        lower(disease_data) as B_search, \
        lower(target_data) as A_search \
    from ot.associations_otf_log); \

```

Done !

For aotf data,  clickhouse needs 7.2 GB disk space. 







