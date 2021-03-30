# Install Open Targets  to GCP

**GCP account** 

     **** [**ds5362165@gmail.com**](mailto:ds5362165@gmail.com)

**Install NVM** 

{% embed url="https://cloud.google.com/nodejs/docs/setup" %}

*  use node version 12~14, the latest has some issue with platform-app

**Install Yarn**

```text
sudo yum install -y make gcc*

curl --silent --location 
https://dl.yarnpkg.com/rpm/yarn.repo
 | sudo tee /etc/yum.repos.d/yarn.repo sudo rpm --import 
https://dl.yarnpkg.com/rpm/pubkey.gpg

sudo yum install yarn
```

**Install git**

```text
sudo yum install git
```

**Upload data files to Google VM**

```text
scp -r -i ~/.ssh/google_compute_engine /Users/jonkiky/Documents/work/openTarget/database/ ds5362165@34.86.72.36:/home/ds5362165/db
gcloud compute ssh ds5362165@open-target-backendgcloud
```

**Install ElasticSearch**

```text
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.2.0-linux-x86_64.tar.gz
```

```text
tar -xf elasticsearch-7.2.0-linux-x86_64.tar.gz
```

**git clone repos**

```text
git clone https://github.com/opentargets/platform-etl-backend.git
```

```text
git clone https://github.com/opentargets/platform-api-beta.git
```

**Install Java and Scala** 

Refer: [https://www.vultr.com/docs/how-to-install-scala-on-centos-7](https://www.vultr.com/docs/how-to-install-scala-on-centos-7) 

```text
sudo yum install java-1.8.0-openjdk
```

**Import data to clickhouse and ES**

**install pip** 

{% embed url="https://linuxize.com/post/how-to-install-pip-on-centos-7/" %}

**Install elasticsearch-loader**

```text
pip install elasticsearch-loader
```

**Run ES as de**

```text
nohup ./bin/elasticsearch & 
```

**How to delete all data in ES.** 

```text
curl -XDELETE localhost:9200/all
```

**Install  Clickhouse**

{% embed url="https://clickhouse.tech/docs/en/getting-started/install/" %}

**run Clickhouse**

```text
  sudo systemctl start clickhouse-server
  250  sudo systemctl start clickhouse-server
  251  sudo systemctl stop clickhouse-server
  
  
```

**Change Clickhouse default port**

```text
sudo vim /etc/clickhouse-server/config.xml
```

**install SBT**

```text
curl https://bintray.com/sbt/rpm/rpm | sudo tee /etc/yum.repos.d/bintray-sbt-rpm.repo
sudo yum install sbt
```

**run sbt as deamon**

```text
 setsid nohup sbt run &
```

**Check data in ES**

```text
curl -X GET "localhost:9200/_cat/indices/"

```

**visit :**

OTG:  http://34.121.72.138:3000 

OTP:   http://35.186.175.242:3000 

