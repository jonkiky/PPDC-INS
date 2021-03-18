# Open target in Google Cloud

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



Install git

```text
sudo yum install git
```

Upload files to Google VM

```text
scp -r -i ~/.ssh/google_compute_engine /Users/jonkiky/Documents/work/openTarget/database/ ds5362165@34.86.72.36:/home/ds5362165/db
gcloud compute ssh ds5362165@open-target-backendgcloud
```

Install ElasticSearch

```text
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.2.0-linux-x86_64.tar.gz
```

git clone repos

```text
git clone https://github.com/opentargets/platform-etl-backend.git
```

```text
git clone https://github.com/opentargets/platform-api-beta.git
```

Install Java and Scala 

Refer: [https://www.vultr.com/docs/how-to-install-scala-on-centos-7](https://www.vultr.com/docs/how-to-install-scala-on-centos-7) 

```text
sudo yum install java-1.8.0-openjdk
```



Import data to clickhouse and ES





Run ES 

