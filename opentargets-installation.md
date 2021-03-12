# OpenTargets Installation

## **Database** 

### **Clickhouse** 

[**https://clickhouse.tech/docs/en/getting-started/install/**](https://clickhouse.tech/docs/en/getting-started/install/)   
****

#### **System Requirements** 

**ClickHouse can run on any Linux, FreeBSD, or Mac OS X with x86\_64, AArch64, or PowerPC64LE CPU architecture.**

#### **Document**

**Install from source can be found here \(for Mac user\) :** 

**Windows users have to install the linux system in VB, in order to use the CH. will find it out later.  For Mac and linux users, the steps to install the CH are largely the same.** 

[**https://clickhouse.tech/docs/en/development/build-osx/**](https://clickhouse.tech/docs/en/development/build-osx/)  
****

#### **Support**

**Telegram  https://telegram.me/clickhouse\_en**  


#### **Command-line** 

**./clickhouse-server --config-file=/Users/jonkiky/Documents/work/openTarget/ClickHouse/programs/server/config.xml**  


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

\*\*\*\*

\*\*\*\*

\*\*\*\*

