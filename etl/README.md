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

## Platform-input-support:

Collect data from various sources, put them into GCP.   

List of available steps:

* annotations
* annotations\_qc
* annotations\_from\_buckets
* ChEMBL
* chemical\_probes
* drug
* eco
* efo
* ensembl
* evidences
* interactions
* known\_target\_safety
* tep

Each step is an individual way to collect data. 

The input data is a config file, which contains the data source:   
[https://github.com/opentargets/platform-input-support/blob/master/config.yaml](https://github.com/opentargets/platform-input-support/blob/master/config.yaml) 

The output data are stored in three folders:

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/annotation-files/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/annotation-files/)

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files/)

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files-subsets/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/input/evidence-files-subsets/)

The  mrtage yam file contains all the locations of collected data, is part of the output 

[https://storage.googleapis.com/open-targets-data-releases/21.02/templates/template.mrtarget.data.21.02.yml](https://storage.googleapis.com/open-targets-data-releases/21.02/templates/template.mrtarget.data.21.02.yml)  


\*\*\*\*\*\*\*\*\*Note

this is only part of the data, the data from FAERS  treat separately. 





### \*\*\*\*

![](../.gitbook/assets/platform-input-support.jpeg)



