# ETL

## Repos

[**platform-input-support**](https://github.com/opentargets/platform-input-support) ****- scripts that process and prepare data for our ETL pipelines 

[**platform-etl-backend**](https://github.com/opentargets/platform-etl-backend) ****- ETL pipelines to generate associations, evidence, and entity indices 

\*\*\*\*[**platform-etl-openfda-faers** ](https://github.com/opentargets/platform-etl-openfda-faers) ****- ETL pipeline to process OpenFDA adverse events data 

[**json\_schema**](https://github.com/opentargets/json_schema) - evidence object schema used by ETL pipelines for evidence and association scoring

\*\*\*\*[**data\_pipeline**](https://github.com/opentargets/data_pipeline)  ****to process different data files that provide evidence for the target-disease associations in the Open Targets Platform. ****

\*\*\*\*

## ETL Workflow

![](../.gitbook/assets/untitled-document-2-.png)

Config.file : [https://github.com/opentargets/platform-input-support/blob/master/config.yaml](https://github.com/opentargets/platform-input-support/blob/master/config.yaml)

Yaml.file : [https://storage.googleapis.com/open-targets-data-releases/21.02/templates/template.mrtarget.data.21.02.yml](https://storage.googleapis.com/open-targets-data-releases/21.02/templates/template.mrtarget.data.21.02.yml) 

## Data

### **Source**

the database dump files are available via FTP from [http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/). 

load the data, please use the following scripts: • ElasticSearch: [https://github.com/opentargets/platform-etl-backend/tree/21.02/elasticsearch](https://github.com/opentargets/platform-etl-backend/tree/21.02/elasticsearch) 

ClickHouse: [https://github.com/opentargets/platform-etl-backend/tree/21.02/clickhouse](https://github.com/opentargets/platform-etl-backend/tree/21.02/clickhouse)

### **Notes for data downloading**

**chemical\_probes, tep, known\_target\_safety data:** 

replace the gkey and gid with value given in the config file. [https://docs.google.com/spreadsheets/d/{gkey}/export?format=tsv&gid={gid}](https://docs.google.com/spreadsheets/d/{gkey}/export?format=tsv&gid={gid}) for example :

* gkey: 1VL3eHGpvJMaQ7LYp0Kp1plEo-NueP3CT7FUCrW0p2dg

  gid: 1686598114

  After replace the keys:

  [https://docs.google.com/spreadsheets/d/1VL3eHGpvJMaQ7LYp0Kp1plEo-NueP3CT7FUCrW0p2dg/export?format=tsv&gid=1686598114](https://docs.google.com/spreadsheets/d/1VL3eHGpvJMaQ7LYp0Kp1plEo-NueP3CT7FUCrW0p2dg/export?format=tsv&gid=1686598114)

**Annotations\_from\_buckets**

\*\*\*\*[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/annotation-files/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/annotation-files/)

**Ensembl:** 

mysql+mysqldb://anonymous@ensembldb.ensembl.org:3337/homo\_sapiens\_core\_102\_38

for drug: elastic search://hh-rke-wp-webadmin-04-worker-4.caas.ebi.ac.uk

**Evidences**

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files/)

**subset of evidences**

 [http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files-subsets/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files-subsets/)

**annotations\_qc:** [http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/other/qc\_annotations/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/other/qc_annotations/)





