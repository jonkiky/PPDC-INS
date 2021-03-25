# OpenTarget  Processed Data

## AOT-ClickHouse

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/aotf/clickhouse/" %}



```text
{
   "row_id":"000389a2cabf4a82e3c8176d7a100c8bdf8b280f",
   "disease_id":"EFO_1001950",
   "disease_data":"EFO_1001950 colon carcinoma",
   "target_id":"ENSG00000149948",
   "target_data":"ENSG00000149948 high mobility group AT-hook 2 HMGA2",
   "datasource_id":"europepmc",
   "datatype_id":"literature",
   "sourceId":"europepmc",
   "row_score":0.14800000000000002
}
{
   "row_id":"00043c3312f4c24f0716e65e5da5ca7be75ac0c3",
   "disease_id":"EFO_0001073",
   "disease_data":"EFO_0001073 obesity",
   "target_id":"ENSG00000164129",
   "target_data":"ENSG00000164129 neuropeptide Y receptor Y5 NPY5R",
   "datasource_id":"europepmc",
   "datatype_id":"literature",
   "sourceId":"europepmc",
   "row_score":0.052000000000000005
   }
```

## AOT-Elasticsearch 

-- load script ./load\_evidences\_aotf.sh

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/aotf/elasticsearch/" %}



```text
{
   "row_id":"000389a2cabf4a82e3c8176d7a100c8bdf8b280f",
   "disease_id":"EFO_1001950",
   "disease_data":"EFO_1001950 colon carcinoma",
   "target_id":"ENSG00000149948",
   "target_data":"ENSG00000149948 high mobility group AT-hook 2 HMGA2",
   "datasource_id":"europepmc",
   "datatype_id":"literature",
   "sourceId":"europepmc",
   "row_score":0.14800000000000002
}{
   "row_id":"00043c3312f4c24f0716e65e5da5ca7be75ac0c3",
   "disease_id":"EFO_0001073",
   "disease_data":"EFO_0001073 obesity",
   "target_id":"ENSG00000164129",
   "target_data":"ENSG00000164129 neuropeptide Y receptor Y5 NPY5R",
   "datasource_id":"europepmc",
   "datatype_id":"literature",
   "sourceId":"europepmc",
   "row_score":0.052000000000000005
   }
```



## associations  

no\_load script 

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/associations/direct/byOverall/" %}



```text
{
   "diseaseId":"DOID_0050890",
   "targetId":"ENSG00000005381",
   "diseaseLabel":"synucleinopathy",
   "targetName":"myeloperoxidase",
   "targetSymbol":"MPO",
   "overallDatasourceHarmonicScore":0.005026286023711945,
   "overallDatatypeHarmonicScore":0.025131430118559724,
   "overallDatasourceHarmonicVector":[
      {
         "datasourceId":"europepmc",
         "datasourceHarmonicScore":0.04133929423759024,
         "datasourceEvidenceCount":1,
         "weight":0.2
      }
   ],
   "overallDatatypeHarmonicVector":[
      {
         "datatypeId":"literature",
         "datatypeHarmonicScore":0.04133929423759024,
         "datatypeEvidenceCount":1,
         "weight":1.0
      }
   ],
   "overallDatasourceEvidenceCount":1.0,
   "overallDatatypeEvidenceCount":1.0
}
```

## cancerBiomarkers

load\_cancerbiomarker.sh

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/cancerBiomarkers/" %}

```text
{
   "drugName":"Dasatinib (BCR-ABL inhibitor 2nd gen)",
   "target":"ENSG00000097007",
   "disease":"EFO_0000339",
   "evidenceLevel":"FDA guidelines",
   "associationType":"Responsive",
   "sourcesOther":[
      {
         "description":"Food and Drug Administration guidelines",
         "link":"https://www.fda.gov/RegulatoryInformation/Guidances/default.htm",
         "name":"FDA"
      }
   ],
   "id":"ABL1-BCR fusion"
}
```

## disease\_hpo

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/disease\_hpo/" %}

```text
{
   "disease":"EFO_0000182",
   "phenotype":"HP_0001413",
   "evidence":[
      {
         "aspect":"P",
         "bioCuration":"HPO:probinson[2009-02-17]",
         "diseaseFromSourceId":"OMIM:114550",
         "diseaseFromSource":"HEPATOCELLULAR CARCINOMA",
         "diseaseName":"hepatocellular carcinoma",
         "evidenceType":"TAS",
         "qualifierNot":false,
         "references":[
            "OMIM:114550"
         ],
         "resource":"HPO"
      }
   ]
}
```

## diseases

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/diseases/" %}

```text
{
   "id":"DOID_0050890",
   "children":[
      "EFO_0002508",
      "EFO_0006792",
      "EFO_1001050"
   ],
   "code":"http://purl.obolibrary.org/obo/DOID_0050890",
   "dbXRefs":[
      "MONDO:0000510"
   ],
   "description":"A neurodegenerative disease that is characterized by the abnormal accumulation of aggregates of alpha-synuclein protein in neurons, nerve fibres or glial cells. [url:http://en.wikipedia.org/wiki/Synucleinopathies ]",
   "name":"synucleinopathy",
   "ontology":{
      "isTherapeuticArea":false,
      "leaf":false,
      "sources":{
         "name":"DOID_0050890",
         "url":"http://purl.obolibrary.org/obo/DOID_0050890"
      }
   },
   "parents":[
      "EFO_0005772"
   ],
   "synonyms":{
      "hasExactSynonym":[
         "synucleinopathy",
         "alpha Synucleinopathies"
      ],
      "hasRelatedSynonym":[
         "alpha synucleinopathies",
         "synucleinopathies"
      ]
   },
   "therapeuticAreas":[
      "EFO_0000618"
   ],
   "ancestors":[
      "EFO_0000618",
      "EFO_0009386",
      "EFO_0005772"
   ],
   "descendants":[
      "MONDO_0010796",
      "Orphanet_2828",
      "Orphanet_411602",
      "MONDO_0014889",
      "EFO_0002508",
      "MONDO_0008199",
      "MONDO_0000828",
      "EFO_0006792",
      "MONDO_0003122",
      "Orphanet_225154",
      "Orphanet_314632",
      "EFO_1001050",
      "Orphanet_171695",
      "EFO_1001175",
      "Orphanet_228169",
      "Orphanet_1576",
      "EFO_1001402",
      "Orphanet_306674",
      "MONDO_0000211",
      "Orphanet_199351",
      "Orphanet_225147"
   ]
}
```

## drug

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/drugs/drug/" %}

```text
{
   "id":"CHEMBL10118",
   "canonicalSmiles":"C[C@@]1(c2ccc(Oc3ccccc3)cc2)OC(=O)N(Nc2ccccc2)C1=O",
   "drugType":"Small molecule",
   "blackBoxWarning":false,
   "name":"FAMOXADONE",
   "maximumClinicalTrialPhase":0,
   "hasBeenWithdrawn":false,
   "isApproved":false,
   "tradeNames":[
      
   ],
   "synonyms":[
      
   ],
   "crossReferences":{
      "drugbank":[
         "DB07778"
      ],
      "chEBI":[
         "106738"
      ]
   },
   "description":"Small molecule drug with a maximum clinical trial phase of I."
}
```



## eco

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/eco/" %}

```text
{
   "code":"http://purl.obolibrary.org/obo/ECO_0001146",
   "label":"allograft transplantation phenotypic evidence used in manual assertion",
   "path":[
      [
         {
            "label":"evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000000"
         },
         {
            "label":"experimental evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000006"
         },
         {
            "label":"experimental evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000269"
         },
         {
            "label":"experimental phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0007634"
         },
         {
            "label":"allograft transplantation phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0001146"
         }
      ],
      [
         {
            "label":"evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000000"
         },
         {
            "label":"experimental evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000006"
         },
         {
            "label":"experimental phenotypic evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000059"
         },
         {
            "label":"experimental phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0007634"
         },
         {
            "label":"allograft transplantation phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0001146"
         }
      ],
      [
         {
            "label":"evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000000"
         },
         {
            "label":"experimental evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000006"
         },
         {
            "label":"experimental phenotypic evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000059"
         },
         {
            "label":"anatomical perturbation phenotypic evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000240"
         },
         {
            "label":"allograft transplantation phenotypic evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0001009"
         },
         {
            "label":"allograft transplantation phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0001146"
         }
      ],
      [
         {
            "label":"evidence",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000000"
         },
         {
            "label":"evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000352"
         },
         {
            "label":"experimental evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0000269"
         },
         {
            "label":"experimental phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0007634"
         },
         {
            "label":"allograft transplantation phenotypic evidence used in manual assertion",
            "uri":"http://purl.obolibrary.org/obo/ECO_0001146"
         }
      ]
   ],
   "path_codes":[
      [
         "ECO_0000000",
         "ECO_0000006",
         "ECO_0000269",
         "ECO_0007634",
         "ECO_0001146"
      ],
      [
         "ECO_0000000",
         "ECO_0000006",
         "ECO_0000059",
         "ECO_0007634",
         "ECO_0001146"
      ],
      [
         "ECO_0000000",
         "ECO_0000006",
         "ECO_0000059",
         "ECO_0000240",
         "ECO_0001009",
         "ECO_0001146"
      ],
      [
         "ECO_0000000",
         "ECO_0000352",
         "ECO_0000269",
         "ECO_0007634",
         "ECO_0001146"
      ]
   ],
   "path_labels":[
      [
         "evidence",
         "experimental evidence",
         "experimental evidence used in manual assertion",
         "experimental phenotypic evidence used in manual assertion",
         "allograft transplantation phenotypic evidence used in manual assertion"
      ],
      [
         "evidence",
         "experimental evidence",
         "experimental phenotypic evidence",
         "experimental phenotypic evidence used in manual assertion",
         "allograft transplantation phenotypic evidence used in manual assertion"
      ],
      [
         "evidence",
         "experimental evidence",
         "experimental phenotypic evidence",
         "anatomical perturbation phenotypic evidence",
         "allograft transplantation phenotypic evidence",
         "allograft transplantation phenotypic evidence used in manual assertion"
      ],
      [
         "evidence",
         "evidence used in manual assertion",
         "experimental evidence used in manual assertion",
         "experimental phenotypic evidence used in manual assertion",
         "allograft transplantation phenotypic evidence used in manual assertion"
      ]
   ],
   "id":"ECO_0001146"
}
```



## evidences

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/evidences/succeeded/sourceId%3Dcancer\_gene\_census/" %}

### sourceId=cancer\_gene\_census/

```text
{
   "datasourceId":"cancer_gene_census",
   "targetId":"ENSG00000162733",
   "diseaseFromSourceId":"EFO_0002618",
   "mutatedSamples":[
      {
         "functionalConsequenceId":"SO_0001059",
         "numberMutatedSamples":12,
         "numberSamplesTested":114,
         "numberSamplesWithMutationType":11
      },
      {
         "functionalConsequenceId":"SO_0001583",
         "numberMutatedSamples":12,
         "numberSamplesTested":114,
         "numberSamplesWithMutationType":1
      }
   ],
   "resourceScore":0.75,
   "targetFromSourceId":"ENSG00000162733",
   "datatypeId":"somatic_mutation",
   "diseaseId":"EFO_0002618",
   "studyId":"analysis?ln=DDR2",
   "targetSymbol":"DDR2",
   "targetName":"discoidin domain receptor tyrosine kinase 2",
   "diseaseLabel":"pancreatic carcinoma",
   "id":"014b2f93a47a0fbd42db7066c5f79ef4440bf52f",
   "score":0.75
}
```

```text
{
   "datasourceId":"chembl",
   "targetId":"ENSG00000137869",
   "diseaseFromSourceId":"MONDO_0011962",
   "clinicalStatus":"Completed",
   "drugId":"CHEMBL1444",
   "urls":[
      {
         "niceName":"Clinical Trials Information",
         "url":"https://clinicaltrials.gov/search?id=%22NCT00171808%22"
      }
   ],
   "clinicalPhase":2,
   "targetFromSourceId":"P11511",
   "datatypeId":"known_drug",
   "diseaseId":"MONDO_0011962",
   "targetSymbol":"CYP19A1",
   "targetName":"cytochrome P450 family 19 subfamily A member 1",
   "diseaseLabel":"endometrial cancer",
   "id":"0007aa2f70b8dcecab341b28f75976fc79020a09",
   "score":0.2
}
```

