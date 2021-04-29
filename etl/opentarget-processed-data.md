# ETL processed data

## Data

**Data after ETL process \(20\)**

aotf/-&gt;  clickhouse \| elasticsearch  
associations/  
cancerBiomarkers/  
disease\_hpo/  
diseases/  
drugs/  
eco/  
evidences/  
expression/  
hpo/  
interactions/  
interactions\_evidence/  
knownDrugs/  
mousePhenotypes/  
openfda-faers/  
otar\_projects/  
reactome/  
search/  
so/  
targets/

## AOT for ClickHouse

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

```

## AOT for Elasticsearch 

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



## evidence stats

```text
{
   "sourceId":"europepmc",
   "#resolvedTarget-false":859652,
   "#resolvedDisease-false":79996,
   "#markedDuplicate-true":362431,
   "#nullifiedScore-true":0,
   "#excludedBiotype-true":0,
   "#targetId":10909,
   "#diseaseId":29,
   "#counts":1256180
}
```



## evidence **Succeeded**



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

### sourceId=chembl/

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

### sourceId=clingen/

```text
{
   "datasourceId":"clingen",
   "targetId":"ENSG00000198668",
   "diseaseFromSourceId":"HP_0001657",
   "confidence":"Definitive",
   "targetFromSourceId":"ENSG00000198668",
   "datatypeId":"genetic_literature",
   "diseaseFromSource":"long QT syndrome",
   "allelicRequirements":[
      "Autosomal Dominant"
   ],
   "diseaseId":"HP_0001657",
   "studyId":"4a150cd9-e16b-4992-8cc7-5ccec44b4d6b--2018-09-25T16:00:00",
   "targetSymbol":"CALM1",
   "targetName":"calmodulin 1",
   "diseaseLabel":"Prolonged QT interval",
   "id":"373c02866feccc6f9e98cbaf1888bc18ba7131b0",
   "score":1.0
}
```

###  sourceId=crispr/

```text
{
   "datasourceId":"crispr",
   "targetId":"ENSG00000182197",
   "diseaseFromSourceId":"EFO_0000178",
   "resourceScore":0.528333,
   "literature":[
      "30971826"
   ],
   "targetFromSourceId":"ENSG00000182197",
   "datatypeId":"affected_pathway",
   "diseaseFromSource":"Gastric Carcinoma",
   "diseaseCellLines":[
      "23132-87",
      "HGC-27",
      "HSC-39",
      "KATOIII",
      "MKN28",
      "NCI-N87",
      "NUGC-3",
      "SNU-1",
      "SNU-16",
      "TMK-1",
      "AGS",
      "RERF-GC-1B",
      "SCH",
      "IM-95",
      "GCIY",
      "MKN1",
      "Hs-746T",
      "TGBC11TKB"
   ],
   "diseaseId":"EFO_0000178",
   "targetSymbol":"EXT1",
   "targetName":"exostosin glycosyltransferase 1",
   "diseaseLabel":"gastric carcinoma",
   "id":"082844530297bc16233b43cd10dd779860f8a34c",
   "score":0.528333
}
```

###  sourceId=europepmc/

```text
{
   "datasourceId":"europepmc",
   "targetId":"ENSG00000185664",
   "diseaseFromSourceId":"Orphanet_104",
   "resourceScore":5.2,
   "literature":[
      "29996615"
   ],
   "textMiningSentences":[
      {
         "dEnd":78,
         "dStart":75,
         "section":"abstract",
         "tEnd":42,
         "tStart":39,
         "text":"Compared to carriers, the amplitude of P100 was obviously decreased in the LHON patients[ (5.6Â±2.6) Î¼V vs. (15.6Â±9.6) Î¼V, t=2.880, P=0.006]."
      }
   ],
   "targetFromSourceId":"P40967",
   "datatypeId":"literature",
   "diseaseFromSource":"LHON",
   "diseaseId":"Orphanet_104",
   "targetSymbol":"PMEL",
   "targetName":"premelanosome protein",
   "diseaseLabel":"Leber hereditary optic neuropathy",
   "id":"000066f3a6dbe79960c194206775655ed6e8dc08",
   "score":0.052000000000000005
}
```

###  sourceId=eva/

```text
{
   "datasourceId":"eva",
   "targetId":"ENSG00000185920",
   "diseaseFromSourceId":"Orphanet_377",
   "variantFunctionalConsequenceId":"SO_0001574",
   "literature":[
      "15604628",
      "20301330",
      "21304560",
      "25394175"
   ],
   "confidence":"criteria provided, single submitter",
   "targetFromSourceId":"ENSG00000185920",
   "clinicalSignificances":[
      "likely pathogenic"
   ],
   "datatypeId":"genetic_association",
   "diseaseFromSource":"gorlin syndrome",
   "diseaseId":"Orphanet_377",
   "studyId":"RCV001209501",
   "targetSymbol":"PTCH1",
   "targetName":"patched 1",
   "diseaseLabel":"Gorlin syndrome",
   "id":"000cc3016d89e387a0681abeb02d3df05878ff2c",
   "score":1.02
}
```

###  sourceId=eva\_somatic/

```text
{
   "datasourceId":"eva_somatic",
   "targetId":"ENSG00000168036",
   "diseaseFromSourceId":"EFO_0001416",
   "confidence":"no assertion criteria provided",
   "targetFromSourceId":"ENSG00000168036",
   "clinicalSignificances":[
      "likely pathogenic"
   ],
   "datatypeId":"somatic_mutation",
   "diseaseFromSource":"uterine cervical neoplasms",
   "allelicRequirements":[
      "Somatic mutation"
   ],
   "variantRsId":"rs28931588",
   "diseaseId":"EFO_0001416",
   "studyId":"RCV000422380",
   "targetSymbol":"CTNNB1",
   "targetName":"catenin beta 1",
   "diseaseLabel":"cervical adenocarcinoma",
   "id":"01eff59074ab7201937a59728685a47e86f56879",
   "score":1.0
}
```

###  sourceId=expression\_atlas/

```text
{
   "datasourceId":"expression_atlas",
   "targetId":"ENSG00000167900",
   "diseaseFromSourceId":"EFO_0000676",
   "resourceScore":0.00457,
   "log2FoldChangeValue":1.2,
   "log2FoldChangePercentileRank":95,
   "targetFromSourceId":"ENSG00000167900",
   "datatypeId":"rna_expression",
   "diseaseFromSource":"lesional",
   "contrast":"'psoriasis lesional skin' vs 'psoriasis non-lesional skin'",
   "studyOverview":"Gene expression in psoriasis lesions and uninvolved skin",
   "diseaseId":"EFO_0000676",
   "studyId":"E-GEOD-50790",
   "targetSymbol":"TK1",
   "targetName":"thymidine kinase 1",
   "diseaseLabel":"psoriasis",
   "id":"003fa408f0139acbe3ba752aeb04fdf9954902a7",
   "score":0.026676955319203704
}
```

###  sourceId=gene2phenotype/

```text
{
   "datasourceId":"gene2phenotype",
   "targetId":"ENSG00000101115",
   "diseaseFromSourceId":"Orphanet_93293",
   "confidence":"confirmed",
   "targetFromSourceId":"ENSG00000101115",
   "datatypeId":"genetic_literature",
   "diseaseFromSource":"DUANE-RADIAL RAY SYNDROME",
   "allelicRequirements":[
      "monoallelic"
   ],
   "diseaseId":"Orphanet_93293",
   "studyId":"DD",
   "targetSymbol":"SALL4",
   "targetName":"spalt like transcription factor 4",
   "diseaseLabel":"Okihiro syndrome",
   "id":"0937c5305c24c6fc25bfdff158bd2138c091824a",
   "score":1.0
}
```

###  sourceId=genomics\_england/

```text
{
   "datasourceId":"genomics_england",
   "targetId":"ENSG00000159921",
   "diseaseFromSourceId":"Orphanet_602",
   "cohortPhenotypes":[
      "Sialuria, 269921",
      "Nonaka myopathy, 605820"
   ],
   "literature":[
      "30847515"
   ],
   "confidence":"green",
   "targetFromSourceId":"ENSG00000159921",
   "datatypeId":"genetic_literature",
   "diseaseFromSource":"Nonaka myopathy",
   "allelicRequirements":[
      "BOTH monoallelic and biallelic, autosomal or pseudoautosomal"
   ],
   "studyOverview":"Severe Paediatric Disorders",
   "diseaseId":"Orphanet_602",
   "studyId":"921",
   "targetSymbol":"GNE",
   "targetName":"glucosamine (UDP-N-acetyl)-2-epimerase/N-acetylmannosamine kinase",
   "diseaseLabel":"Distal myopathy, Nonaka type",
   "id":"0166fb703e0625a1d7cf6d29bdd6a36785622573",
   "score":1.0
}
```

###  sourceId=intogen/

```text
{
   "datasourceId":"intogen",
   "targetId":"ENSG00000081237",
   "diseaseFromSourceId":"MONDO_0001879",
   "mutatedSamples":[
      {
         "numberMutatedSamples":2,
         "numberSamplesTested":17
      }
   ],
   "resourceScore":7.587043749655777E-4,
   "cohortShortName":"ANUS_CANCER_HARTWIG",
   "cohortId":"HARTWIG_ANUS",
   "targetFromSourceId":"ENSG00000081237",
   "significantDriverMethods":[
      "combination"
   ],
   "datatypeId":"somatic_mutation",
   "diseaseFromSource":"Anus cancer ",
   "cohortDescription":"Anus cancer data from Hartwig Medical Foundation",
   "diseaseId":"MONDO_0001879",
   "studyId":"search?gene=PTPRC&cohort=HARTWIG_ANUS",
   "targetSymbol":"PTPRC",
   "targetName":"protein tyrosine phosphatase receptor type C",
   "diseaseLabel":"anus cancer",
   "id":"0a4406a3d9ebe32e0b6746a2ef0f2468e3d9abfc",
   "score":0.4266606176357214
}
```

###  sourceId=ot\_genetics\_portal/

```text
{
   "datasourceId":"ot_genetics_portal",
   "targetId":"ENSG00000170035",
   "variantId":"2_181121038_A_T",
   "diseaseFromSourceId":"EFO_0004587",
   "variantFunctionalConsequenceId":"SO_0001628",
   "publicationYear":2018,
   "resourceScore":0.7239869236946106,
   "literature":[
      "29403010"
   ],
   "publicationFirstAuthor":"Kanai M",
   "pValueExponent":-8,
   "pValueMantissa":3,
   "targetFromSourceId":"ENSG00000170035",
   "datatypeId":"genetic_association",
   "diseaseFromSource":"Lymphocyte counts",
   "variantRsId":"rs13011751",
   "diseaseId":"EFO_0004587",
   "studyId":"GCST005997",
   "studySampleSize":62076,
   "targetSymbol":"UBE2E3",
   "targetName":"ubiquitin conjugating enzyme E2 E3",
   "diseaseLabel":"lymphocyte count",
   "id":"0003e80ee060765321d7a9742f4a42b15df152b5",
   "score":0.7239869236946106
}
```

###  sourceId=phenodigm/

```text
{
   "datasourceId":"phenodigm",
   "targetId":"ENSG00000049130",
   "biologicalModelAllelicComposition":"Kitl<Sl-31R>/Kitl<+>",
   "diseaseFromSourceId":"OMIM:612527",
   "diseaseModelAssociatedModelPhenotypes":[
      {
         "id":"MP:0002811",
         "label":"macrocytic anemia"
      },
      {
         "id":"MP:0002590",
         "label":"increased mean corpuscular volume"
      },
      {
         "id":"MP:0005561",
         "label":"increased mean corpuscular hemoglobin"
      },
      {
         "id":"MP:0002939",
         "label":"head spot"
      },
      {
         "id":"MP:0008237",
         "label":"abnormal ventral coat pigmentation"
      }
   ],
   "resourceScore":0.9115000000000001,
   "diseaseModelAssociatedHumanPhenotypes":[
      {
         "id":"HP:0012133",
         "label":"Erythroid hypoplasia"
      },
      {
         "id":"HP:0001972",
         "label":"Macrocytic anemia"
      },
      {
         "id":"HP:0001896",
         "label":"Reticulocytopenia"
      }
   ],
   "targetFromSourceId":"ENSG00000049130",
   "datatypeId":"animal_model",
   "biologicalModelGeneticBackground":"C3H-Kitl<Sl-31R>",
   "diseaseFromSource":"Diamond-Blackfan Anemia 4",
   "targetInModel":"ENSMUSG00000019966",
   "diseaseId":"Orphanet_124",
   "targetSymbol":"KITLG",
   "targetName":"KIT ligand",
   "diseaseLabel":"Blackfan-Diamond anemia",
   "id":"00098065d7c6ecf5748ff329042c01a00e7766c3",
   "score":0.9115000000000001
}
```

###  sourceId=phewas\_catalog/

```text
{
   "datasourceId":"phewas_catalog",
   "targetId":"ENSG00000154654",
   "variantId":"21_21537795_C_T",
   "diseaseFromSourceId":"EFO_0003777",
   "variantFunctionalConsequenceId":"SO_0001627",
   "resourceScore":0.03319,
   "oddsRatio":0.9197,
   "targetFromSourceId":"ENSG00000154654",
   "datatypeId":"genetic_association",
   "diseaseFromSource":"Ill-defined descriptions and complications of heart disease [429]",
   "variantRsId":"rs2826891",
   "studyCases":1847,
   "diseaseId":"EFO_0003777",
   "targetSymbol":"NCAM2",
   "targetName":"neural cell adhesion molecule 2",
   "diseaseLabel":"heart disease",
   "id":"003c37a79181247ada87f3d2e5d0e4c74181b7cb",
   "score":0.010010065944358213
}
```

###  sourceId=progeny/

```text
{
   "datasourceId":"progeny",
   "targetId":"ENSG00000121858",
   "diseaseFromSourceId":"EFO_0000503",
   "resourceScore":0.760546748134336,
   "pathwayId":"R-HSA-123456",
   "targetFromSourceId":"ENSG00000121858",
   "datatypeId":"affected_pathway",
   "diseaseFromSource":"stomach adenocarcinoma",
   "pathwayName":"XXX Pathway desc to be updated",
   "diseaseId":"EFO_0000503",
   "targetSymbol":"TNFSF10",
   "targetName":"TNF superfamily member 10",
   "diseaseLabel":"gastric adenocarcinoma",
   "id":"bc39786e91915e0ac934e8c80e0cd7877c723803",
   "score":0.5
}
```

###  sourceId=reactome/

```text
{
   "datasourceId":"reactome",
   "targetId":"ENSG00000146648",
   "diseaseFromSourceId":"EFO_0000311",
   "variantAminoacidDescriptions":[
      
   ],
   "targetModulation":"up_or_down",
   "pathwayId":"R-HSA-5638303",
   "literature":[
      "15269313",
      "15837620",
      "16314626"
   ],
   "targetFromSourceId":"P00533",
   "reactionId":"R-HSA-1248677",
   "datatypeId":"affected_pathway",
   "diseaseFromSource":"cancer",
   "pathwayName":"Inhibition of Signaling by Overexpressed EGFR",
   "diseaseId":"EFO_0000311",
   "targetSymbol":"EGFR",
   "targetName":"epidermal growth factor receptor",
   "diseaseLabel":"cancer",
   "id":"08aee3a7d66d4620bfa6cb97a3771cf5c4356255",
   "score":1.0
}
```

###  sourceId=slapenrich/

```text
{
   "datasourceId":"slapenrich",
   "targetId":"ENSG00000068971",
   "diseaseFromSourceId":"EFO_0000519",
   "resourceScore":5.2E-15,
   "pathwayId":"R-HSA-2682334",
   "targetFromSourceId":"ENSG00000068971",
   "datatypeId":"affected_pathway",
   "diseaseFromSource":"glioblastoma multiforme",
   "pathwayName":"FCERI mediated MAPK activation",
   "diseaseId":"EFO_0000519",
   "targetSymbol":"PPP2R5B",
   "targetName":"protein phosphatase 2 regulatory subunit B'beta",
   "diseaseLabel":"glioblastoma multiforme",
   "id":"01aecca7023521664e07ab335b162005653d718e",
   "score":1.0
}
```

###  sourceId=sysbio/

```text
{
   "datasourceId":"sysbio",
   "targetId":"ENSG00000000938",
   "diseaseFromSourceId":"EFO_0003767",
   "resourceScore":0.6571,
   "literature":[
      "28892060"
   ],
   "targetFromSourceId":"ENSG00000000938",
   "datatypeId":"affected_pathway",
   "studyOverview":"Genomic (GWAS, eQTL and cis-regulatory elements associated with IBD), transcriptomic (gene co-expression network) and clinical data from three groups of patients with IBD (treatment naive pediatric patients, patients refractory to anti-TNF therapy and patients with advanced IBD) was integrated to model the network of genes that regulate IBD. A core Immune Activation Module (IAM, a set of immune genes conserved across IBD populations) was used to build patient group specific Bayesian networks of the IBD conserved immune component (CIC) and to identify 133 key driver genes (KDGs). Genes from a macrophage-specific gene signature (MSG) were projected onto the CERTIFI IBD network (patients refractory to anti-TNF therapy) to identify a macrophage-specific component of the IBD network. 133 KDGs were identified.",
   "pathwayName":"Macrophage-specific Key Driver Genes",
   "diseaseId":"EFO_0003767",
   "targetSymbol":"FGR",
   "targetName":"FGR proto-oncogene, Src family tyrosine kinase",
   "diseaseLabel":"inflammatory bowel disease",
   "id":"6877b6415a189320a6d2491af06e05efd718434d",
   "score":0.6571
}
```

###  sourceId=uniprot\_literature/

```text
{
   "datasourceId":"uniprot_literature",
   "targetId":"ENSG00000095002",
   "diseaseFromSourceId":"Orphanet_144",
   "resourceScore":1.0,
   "literature":[
      "12658575",
      "15870828",
      "9559627",
      "17128465",
      "22102614",
      "16451135",
      "22371642",
      "9889267",
      "9419403",
      "12124176",
      "18561205",
      "15365995",
      "12112654",
      "10386556",
      "18951462",
      "12200596",
      "11726306",
      "8797773",
      "9048925",
      "11920458",
      "10528862",
      "18781619",
      "12362047",
      "15300854",
      "15896463",
      "10777691",
      "12132870",
      "12655568",
      "9718327",
      "10829038",
      "18822302",
      "8872463",
      "12655564",
      "15991316",
      "11870161",
      "10375096",
      "15613555",
      "9298827",
      "14635101",
      "15342696",
      "9621522",
      "12373605",
      "15996210",
      "15046096",
      "7874129",
      "17101317",
      "8700523",
      "10573010",
      "21120944",
      "18625694",
      "9240418",
      "9311737",
      "10612836",
      "8261515"
   ],
   "targetFromSourceId":"P43246",
   "datatypeId":"genetic_literature",
   "diseaseFromSource":"Hereditary non-polyposis colorectal cancer 1",
   "diseaseId":"Orphanet_144",
   "studyId":"P43246#pathology_and_biotech",
   "targetSymbol":"MSH2",
   "targetName":"mutS homolog 2",
   "diseaseLabel":"Lynch syndrome",
   "id":"06a79afa00b3ff2193b1a1a01ba2ca9e986ce5a1",
   "score":1.0
}
```



HPO

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/hpo/" %}

```text
{
   "id":"BFO_0000019",
   "name":"quality",
   "namespace":[
      "bfo"
   ],
   "parents":[
      "b25363",
      "BFO_0000020"
   ]
}

{
   "description":"An independent continuant that is spatially extended whose identity is independent of that of other entities and can be maintained through time.",
   "id":"BFO_0000040",
   "name":"material entity",
   "namespace":[
      "bfo"
   ],
   "parents":[
      "BFO_0000004"
   ]
}

{
   "dbXRefs":[
      "Reaxys:5736650",
      "Beilstein:5736650",
      "MetaCyc:2-HYDROXYGLUTARIC_ACID"
   ],
   "description":"A dicarboxylic acid dianion resulting from the removal of a proton from both of the carboxylic acid groups of 2-hydroxyglutaric acid.",
   "id":"CHEBI_11596",
   "name":"2-hydroxyglutarate(2-)",
   "namespace":[
      "chebi_ontology"
   ],
   "parents":[
      "b62449",
      "b62450",
      "CHEBI_28965",
      "CHEBI_132941"
   ]
}
```



## interactions

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/interactions/" %}



```text
{
   "sourceDatabase":"intact",
   "targetA":"ENSG00000104055",
   "intA":"O43548",
   "intABiologicalRole":"unspecified role",
   "targetB":"ENSG00000141738",
   "intB":"Q14451-3",
   "intBBiologicalRole":"unspecified role",
   "speciesA":{
      "mnemonic":"human",
      "scientific_name":"Homo sapiens",
      "taxon_id":9606
   },
   "speciesB":{
      "mnemonic":"human",
      "scientific_name":"Homo sapiens",
      "taxon_id":9606
   },
   "count":3,
   "scoring":0.56
}
```



## interactions\_evidence

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/interactions\_evidence/" %}

```text
{
   "causalInteraction":false,
   "targetB":"ENSG00000005381",
   "evidenceScore":0.195,
   "intBBiologicalRole":"unspecified role",
   "interactionResources":{
      "databaseVersion":"11",
      "sourceDatabase":"string"
   },
   "interactionDetectionMethodShortName":"textmining",
   "intA":"ENSP00000000412",
   "intBSource":"ensembl_protein",
   "speciesB":{
      "mnemonic":"human",
      "scientificName":"Homo sapiens",
      "taxonId":9606
   },
   "speciesA":{
      "mnemonic":"human",
      "scientificName":"Homo sapiens",
      "taxonId":9606
   },
   "intASource":"ensembl_protein",
   "intB":"ENSP00000225275",
   "intABiologicalRole":"unspecified role",
   "interactionScore":0.195,
   "targetA":"ENSG00000003056",
   "interactionDetectionMethodMiIdentifier":"MI:0110"
}
```

## knownDrugs

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/knownDrugs/" %}



```text
{
   "drugId":"CHEMBL1096882",
   "targetId":"ENSG00000148229",
   "diseaseId":"EFO_0000094",
   "phase":1,
   "status":"Recruiting",
   "urls":[
      {
         "niceName":"Clinical Trials Information",
         "url":"https://clinicaltrials.gov/search?id=%22NCT03666000%22"
      },
      {
         "niceName":"Clinical Trials Information",
         "url":"https://clinicaltrials.gov/search?id=%22NCT03467256%22"
      }
   ],
   "ancestors":[
      "EFO_0005803",
      "MONDO_0002334",
      "MONDO_0005374",
      "EFO_0000565",
      "EFO_0004289",
      "EFO_0000220",
      "EFO_0009119",
      "EFO_1000068",
      "MONDO_0044881",
      "EFO_0001642",
      "EFO_0000574",
      "MONDO_0004095",
      "EFO_1001938",
      "EFO_0005952",
      "EFO_0002425",
      "Orphanet_322126",
      "MONDO_0015757",
      "MONDO_0003225",
      "MONDO_0004805",
      "EFO_0007352",
      "OTAR_0000006",
      "EFO_0009676",
      "EFO_0002461",
      "EFO_0000540",
      "MONDO_0044986",
      "OTAR_0000018",
      "EFO_0000508",
      "Orphanet_68336",
      "MONDO_0045024",
      "MONDO_0023370",
      "EFO_0000616",
      "EFO_0000311"
   ],
   "label":"B-cell acute lymphoblastic leukemia",
   "approvedSymbol":"POLE3",
   "approvedName":"DNA polymerase epsilon 3, accessory subunit",
   "prefName":"FLUDARABINE PHOSPHATE",
   "tradeNames":[
      "Fludara",
      "Fludarabine Phosphate",
      "Oforta"
   ],
   "synonyms":[
      "Fludarabine",
      "Fludarabine 5'-monophosphate",
      "Fludarabine Phosphate",
      "NSC-312887",
      "NSC-328002"
   ],
   "drugType":"Small molecule",
   "mechanismOfAction":"DNA polymerase (alpha/delta/epsilon) inhibitor",
   "references":[
      {
         "ids":[
            "23115527"
         ],
         "source":"PubMed",
         "urls":[
            "http://europepmc.org/abstract/MED/23115527"
         ]
      },
      {
         "ids":[
            "label/2011/022137s003lbl.pdf",
            "label/2011/022137s003lbl.pdf"
         ],
         "source":"FDA",
         "urls":[
            "http://www.accessdata.fda.gov/drugsatfda_docs/label/2011/022137s003lbl.pdf",
            "http://www.accessdata.fda.gov/drugsatfda_docs/label/2011/022137s003lbl.pdf"
         ]
      }
   ],
   "targetName":"DNA polymerase (alpha/delta/epsilon)"
}
```



## mousePhenotypes

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/mousePhenotypes/" %}

```text
{
   "id":"ENSG00000094914",
   "phenotypes":[
      {
         "mouse_gene_id":"MGI:2443767",
         "mouse_gene_symbol":"Aaas",
         "phenotypes":[
            {
               "category_mp_identifier":"MP:0005386",
               "category_mp_label":"behavior/neurological phenotype",
               "genotype_phenotype":[
                  {
                     "mp_identifier":"MP:0001516",
                     "mp_label":"abnormal motor coordination/balance",
                     "pmid":"16479006",
                     "subject_allelic_composition":"Aaas<tm1Ahue>/Aaas<tm1Ahue>",
                     "subject_background":"involves: 129P2/OlaHsd * C57BL/6"
                  },
                  {
                     "mp_identifier":"MP:0001402",
                     "mp_label":"hypoactivity",
                     "pmid":"16479006",
                     "subject_allelic_composition":"Aaas<tm1Ahue>/Aaas<tm1Ahue>",
                     "subject_background":"involves: 129P2/OlaHsd * C57BL/6"
                  },
                  {
                     "mp_identifier":"MP:0001417",
                     "mp_label":"decreased exploration in new environment",
                     "pmid":"16479006",
                     "subject_allelic_composition":"Aaas<tm1Ahue>/Aaas<tm1Ahue>",
                     "subject_background":"involves: 129P2/OlaHsd * C57BL/6"
                  }
               ]
            },
            {
               "category_mp_identifier":"MP:0005375",
               "category_mp_label":"adipose tissue phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005385",
               "category_mp_label":"cardiovascular system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005384",
               "category_mp_label":"cellular phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005382",
               "category_mp_label":"craniofacial phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005381",
               "category_mp_label":"digestive/alimentary phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005380",
               "category_mp_label":"embryo phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005379",
               "category_mp_label":"endocrine/exocrine phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005378",
               "category_mp_label":"growth/size/body region phenotype",
               "genotype_phenotype":[
                  {
                     "mp_identifier":"MP:0001262",
                     "mp_label":"decreased body weight",
                     "pmid":"16479006",
                     "subject_allelic_composition":"Aaas<tm1Ahue>/Aaas<tm1Ahue>",
                     "subject_background":"involves: 129P2/OlaHsd * C57BL/6"
                  }
               ]
            },
            {
               "category_mp_identifier":"MP:0005377",
               "category_mp_label":"hearing/vestibular/ear phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005397",
               "category_mp_label":"hematopoietic system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005376",
               "category_mp_label":"homeostasis/metabolism phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005387",
               "category_mp_label":"immune system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0010771",
               "category_mp_label":"integument phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005371",
               "category_mp_label":"limbs/digits/tail phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005370",
               "category_mp_label":"liver/biliary system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0010768",
               "category_mp_label":"mortality/aging",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005369",
               "category_mp_label":"muscle phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0002006",
               "category_mp_label":"neoplasm",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0003631",
               "category_mp_label":"nervous system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0002873",
               "category_mp_label":"normal phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0001186",
               "category_mp_label":"pigmentation phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005367",
               "category_mp_label":"renal/urinary system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005389",
               "category_mp_label":"reproductive system phenotype",
               "genotype_phenotype":[
                  {
                     "mp_identifier":"MP:0001926",
                     "mp_label":"female infertility",
                     "pmid":"16479006",
                     "subject_allelic_composition":"Aaas<tm1Ahue>/Aaas<tm1Ahue>",
                     "subject_background":"involves: 129P2/OlaHsd * C57BL/6"
                  }
               ]
            },
            {
               "category_mp_identifier":"MP:0005388",
               "category_mp_label":"respiratory system phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005390",
               "category_mp_label":"skeleton phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005394",
               "category_mp_label":"taste/olfaction phenotype",
               "genotype_phenotype":[
                  
               ]
            },
            {
               "category_mp_identifier":"MP:0005391",
               "category_mp_label":"vision/eye phenotype",
               "genotype_phenotype":[
                  
               ]
            }
         ]
      }
   ]
}
```

## openfda-faers

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/openfda-faers/agg\_by\_chembl/" %}



```text
{
   "chembl_id":"CHEMBL1200632",
   "reaction_reactionmeddrapt":"abasia",
   "uniq_report_ids_by_reaction":6690,
   "uniq_report_ids_by_drug":963,
   "A":2,
   "C":961,
   "B":6688,
   "D":4523171,
   "aterm":-16.23044394512466,
   "cterm":-8127.140371043927,
   "acterm":-8143.475186685734,
   "llr":0.10437169668239221,
   "meddraCode":"10049460"
}
```

## otar\_projects

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/otar\_projects/](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/otar_projects/)

```text
{
   "efo_id":"MONDO_0021193",
   "projects":[
      {
         "otar_code":"OTAR041",
         "status":"Active",
         "project_name":"CELLector",
         "reference":"http://home.opentargets.org/OTAR041"
      },
      {
         "otar_code":"OTAR015",
         "status":"Active",
         "project_name":"CRISPR-Cas9 Target ID",
         "reference":"http://home.opentargets.org/OTAR015"
      },
      {
         "otar_code":"OTAR016",
         "status":"Closed",
         "project_name":"Cancer Functional Genomics",
         "reference":"http://home.opentargets.org/OTAR016"
      },
      {
         "otar_code":"OTAR2055",
         "status":"Active",
         "project_name":"Prediction of Oncology Targets and in Silico Drug Prescriptions",
         "reference":"http://home.opentargets.org/OTAR2055"
      }
   ]
}
```

## reactome

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/reactome/" %}

```text
{
   "ancestors":[
      "R-HSA-382556",
      "root",
      "R-HSA-382551"
   ],
   "children":[
      "R-HSA-1369007",
      "R-HSA-1369062"
   ],
   "id":"R-HSA-382556",
   "is_root":false,
   "label":"ABC-family proteins mediated transport",
   "parents":[
      "R-HSA-382551"
   ],
   "path":[
      [
         "root",
         "R-HSA-382551",
         "R-HSA-382556"
      ]
   ]
}
```

## Search /diseaseIndex

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/search/diseaseIndex/" %}

```text
{
   "id":"DOID_7551",
   "name":"gonorrhea",
   "description":"A primary bacterial infectious disease that is a sexually transmitted infection, located_in uterus, located_in fallopian tube, located_in urethra, located_in mouth, located_in throat, located_in eye or located_in anus, has_material_basis_in Neisseria gonorrhoeae, which is transmitted_by contact with the penis, vagina, mouth, or anus or transmitted_by congenitally from mother to baby during delivery. The infection has_symptom burning sensation during urination, has_symptom discharge from the penis, has_symptom increased vaginal discharge, or has_symptom vaginal bleeding between periods.",
   "entity":"disease",
   "category":[
      "infectious disease",
      "urinary system disease",
      "reproductive system or breast disease"
   ],
   "keywords":[
      "gonorrhea",
      "DOID_7551",
      "chronic gonococcal infectious disease of upper genitourinary tract",
      "chronic gonococcal infectious disease of lower genitourinary tract.",
      "GC",
      "Neisseria gonorrhoeae infection",
      "chronic gonococcal infectious disease of lower genitourinary tract",
      "acrodermatitis infantile lichenoid",
      "Gianotti Crosti syndrome",
      "infections Neisseria gonorrhoeae",
      "PAC",
      "papular acrodermatitis of childhood",
      "PAS",
      "Crosti-gianotti syndrome",
      "acrodermatitis papular infantile"
   ],
   "prefixes":[
      "gonorrhea",
      "chronic gonococcal infectious disease of upper genitourinary tract",
      "chronic gonococcal infectious disease of lower genitourinary tract.",
      "GC",
      "Neisseria gonorrhoeae infection",
      "chronic gonococcal infectious disease of lower genitourinary tract",
      "acrodermatitis infantile lichenoid",
      "Gianotti Crosti syndrome",
      "infections Neisseria gonorrhoeae",
      "PAC",
      "papular acrodermatitis of childhood",
      "PAS",
      "Crosti-gianotti syndrome",
      "acrodermatitis papular infantile"
   ],
   "ngrams":[
      "gonorrhea",
      "chronic gonococcal infectious disease of upper genitourinary tract",
      "chronic gonococcal infectious disease of lower genitourinary tract.",
      "GC",
      "Neisseria gonorrhoeae infection",
      "chronic gonococcal infectious disease of lower genitourinary tract",
      "acrodermatitis infantile lichenoid",
      "Gianotti Crosti syndrome",
      "infections Neisseria gonorrhoeae",
      "PAC",
      "papular acrodermatitis of childhood",
      "PAS",
      "Crosti-gianotti syndrome",
      "acrodermatitis papular infantile"
   ],
   "terms":[
      "DHEA-ST",
      "HST",
      "STD",
      "ST2",
      "Bile salt sulfotransferase",
      "Dehydroepiandrosterone sulfotransferase",
      "SULT2A3",
      "2.8.2.14",
      "Hydroxysteroid Sulfotransferase",
      "Sulfotransferase 2A1",
      "2.8.2.2",
      "DHEA-ST8",
      "ST2A1",
      "sulfotransferase family 2A member 1",
      "SULT2A1",
      "IB1099",
      "ETL1",
      "EPITEMPIN",
      "EPT",
      "Epitempin-1",
      "Leucine-rich glioma-inactivated protein 1",
      "leucine rich glioma inactivated 1",
      "LGI1",
      "C4BP",
      "PRP",
      "C4bp",
      "Proline-rich protein",
      "C4b-binding protein alpha chain",
      "complement component 4 binding protein alpha",
      "C4BPA",
      "MDP",
      "RDP",
      "Dehydropeptidase-I",
      "Beta-lactamase",
      "Renal dipeptidase",
      "3.4.13.19",
      "Microsomal dipeptidase",
      "hRDP",
      "Dipeptidase 1",
      "3.5.2.6",
      "dipeptidase 1",
      "DPEP1",
      "A3GALNT",
      "A3GALT1",
      "ABO alpha 1-3-N-acetylgalactosaminyltransferase and alpha 1-3-galactosyltransferase",
      "ABO",
      "MTA1-L1",
      "MTA1L1",
      "PID",
      "Metastasis-associated protein MTA2",
      "MTA1-L1 protein",
      "p53 target protein in deacetylase complex",
      "Metastasis-associated 1-like 1",
      "metastasis associated 1 family member 2",
      "MTA2",
      "TMP",
      "CL-20",
      "B4B",
      "Epithelial membrane protein 1",
      "Protein B4B",
      "EMP-1",
      "Tumor-associated membrane protein",
      "epithelial membrane protein 1",
      "EMP1",
      "HLF2",
      "GIG12",
      "LF",
      "Growth-inhibiting protein 12",
      "Talalactoferrin",
      "Lactotransferrin",
      "3.4.21.-",
      "Lactoferrin",
      "lactotransferrin",
      "LTF",
      "CD66e",
      "CEA",
      "Carcinoembryonic antigen-related cell adhesion molecule 5",
      "Carcinoembryonic antigen",
      "Meconium antigen 100",
      "CEA cell adhesion molecule 5",
      "CEACAM5",
      "ANX4",
      "P32.5",
      "Annexin A4",
      "35-beta calcimedin",
      "Endonexin I",
      "Lipocortin IV",
      "Placental anticoagulant protein II",
      "Chromobindin-4",
      "Annexin IV",
      "PP4-X",
      "Carbohydrate-binding protein p33/p41",
      "Protein II",
      "Annexin-4",
      "PAP-II",
      "annexin A4",
      "ANXA4",
      "PRO1557",
      "PRO2086",
      "Beta-1 metal-binding globulin",
      "serotransferrin",
      "Serotransferrin",
      "Siderophilin",
      "Transferrin",
      "transferrin",
      "TF",
      "Activating transcription factor 3",
      "Cyclic AMP-dependent transcription factor ATF-3",
      "cAMP-dependent transcription factor ATF-3",
      "activating transcription factor 3",
      "ATF3",
      "SERS",
      "SARS",
      "Seryl-tRNA(Ser/Sec) synthetase",
      "Serine--tRNA ligase cytoplasmic",
      "serine tRNA ligase 1 cytoplasmic",
      "Seryl-tRNA synthetase",
      "SerRS",
      "6.1.1.11",
      "seryl-tRNA synthetase 1",
      "SARS1",
      "AREGB",
      "SDGF",
      "CRDGF",
      "Colorectum cell-derived growth factor",
      "AR",
      "Amphiregulin",
      "amphiregulin",
      "AREG",
      "MDA-5",
      "Hlcd",
      "MDA5",
      "IDDM19",
      "RH116",
      "Helicase with 2 CARD domains",
      "3.6.4.13",
      "CADM-140 autoantigen",
      "Clinically amyopathic dermatomyositis autoantigen 140 kDa",
      "melanoma differentiation-associated gene 5",
      "Interferon-induced with helicase C domain protein 1",
      "RNA helicase-DEAD box protein 116",
      "RLR-2",
      "Interferon-induced helicase C domain-containing protein 1",
      "helicard",
      "Murabutide down-regulated protein",
      "Helicard",
      "RIG-I-like receptor 2",
      "Melanoma differentiation-associated protein 5",
      "interferon induced with helicase C domain 1",
      "IFIH1",
      "IL-6",
      "BSF2",
      "HGF",
      "HSF",
      "IFNB2",
      "Interleukin-6",
      "interferon beta 2",
      "Hybridoma growth factor",
      "BSF-2",
      "IFN-beta-2",
      "CDF",
      "CTL differentiation factor",
      "B-cell stimulatory factor 2",
      "Interferon beta-2",
      "interleukin 6",
      "IL6",
      "BLAU",
      "CD",
      "PSORAS1",
      "CLR16.3",
      "NLRC2",
      "CARD15",
      "IBD1",
      "Caspase recruitment domain-containing protein 15",
      "nucleotide-binding oligomerization domain leucine rich repeat and CARD domain containing 2",
      "NLR family CARD domain containing 2",
      "Inflammatory bowel disease protein 1",
      "Nucleotide-binding oligomerization domain-containing protein 2",
      "NOD-like receptor C2",
      "nucleotide binding oligomerization domain containing 2",
      "NOD2",
      "RIG-I",
      "FLJ13599",
      "DKFZp434J1111",
      "RIG-1",
      "RIG1",
      "Retinoic acid-inducible gene 1 protein",
      "DEAD box protein 58",
      "Antiviral innate immune response receptor RIG-I",
      "Retinoic acid-inducible gene I protein",
      "Probable ATP-dependent RNA helicase DDX58",
      "retinoic acid inducible gene I",
      "RIG-I-like receptor 1",
      "RLR-1",
      "RNA helicase RIG-I",
      "DExD/H-box helicase 58",
      "DDX58",
      "P21",
      "CIP1",
      "WAF1",
      "SDI1",
      "CAP20",
      "p21CIP1",
      "p21Cip1/Waf1",
      "p21",
      "CDKN1",
      "MDA6",
      "PIC1",
      "MDA-6",
      "CDK-interacting protein 1",
      "Melanoma differentiation-associated protein 6",
      "Cyclin-dependent kinase inhibitor 1",
      "cyclin dependent kinase inhibitor 1A",
      "CDKN1A",
      "IL-2",
      "TCGF",
      "T cell growth factor",
      "T-cell growth factor",
      "Interleukin-2",
      "interleukin 2",
      "IL2",
      "NLRC1",
      "CLR7.1",
      "CARD4",
      "NLR family CARD domain containing 1",
      "Nucleotide-binding oligomerization domain-containing protein 1",
      "nucleotide-binding oligomerization domain leucine rich repeat and CARD domain containing 1",
      "Caspase recruitment domain-containing protein 4",
      "nucleotide binding oligomerization domain containing 1",
      "NOD1",
      "CMP",
      "CRTM",
      "Matrilin-1",
      "Cartilage matrix protein",
      "matrilin 1",
      "MATN1",
      "PCD",
      "DCOH",
      "PCBD",
      "PHS",
      "pterin-4-alpha carbinolamine dehydratase",
      "Pterin-4a-carbinolamine dehydratase (dimerization cofactor of hepatic nuclear factor 1-alpha)",
      "dimerizing cofactor for HNF1",
      "4.2.1.96",
      "DCoH",
      "Phenylalanine hydroxylase-stimulating protein",
      "Pterin-4-alpha-carbinolamine dehydratase",
      "Dimerization cofactor of hepatocyte nuclear factor 1-alpha",
      "Dimerization cofactor of HNF1",
      "4-alpha-hydroxy-tetrahydropterin dehydratase",
      "Pterin carbinolamine dehydratase",
      "pterin-4 alpha-carbinolamine dehydratase 1",
      "PCBD1",
      "1.16.3.1",
      "Ceruloplasmin",
      "ferroxidase",
      "Ferroxidase",
      "ceruloplasmin",
      "CP",
      "CDHF4",
      "Pemphigus foliaceus antigen",
      "DG1",
      "Cadherin family member 4",
      "Desmoglein-1",
      "DGI",
      "Desmosomal glycoprotein 1",
      "desmoglein 1",
      "DSG1",
      "HC2",
      "NU",
      "PROS30",
      "MGC14542",
      "MGC14575",
      "MGC14751",
      "MGC1667",
      "MGC21459",
      "MGC22853",
      "MGC23915",
      "PSC2",
      "Multicatalytic endopeptidase complex subunit C2",
      "PROS-30",
      "Proteasome nu chain",
      "30 kDa prosomal protein",
      "Macropain subunit C2",
      "Proteasome component C2",
      "Proteasome subunit alpha type-1",
      "proteasome subunit α6",
      "proteasome 20S subunit alpha 1",
      "PSMA1",
      "Olfactory marker protein",
      "Olfactory neuronal-specific protein",
      "olfactory marker protein",
      "OMP",
      "CD66d",
      "CD66D",
      "CGM1",
      "Carcinoembryonic antigen-related cell adhesion molecule 3",
      "Carcinoembryonic antigen CGM1",
      "CEA cell adhesion molecule 3",
      "CEACAM3",
      "AST",
      "SD",
      "ISSD",
      "NSD",
      "SIALIN",
      "SLD",
      "Solute carrier family 17 member 5",
      "H(+)/sialic acid cotransporter",
      "Sialin",
      "Vesicular H(+)/Aspartate-glutamate cotransporter",
      "Membrane glycoprotein HP59",
      "H(+)/nitrate cotransporter",
      "solute carrier family 17 member 5",
      "SLC17A5",
      "sej",
      "Se2",
      "SEC2",
      "Secretor blood group alpha-2-fucosyltransferase",
      "alpha(12)FT2",
      "Type 2 galactoside alpha-(12)-fucosyltransferase FUT2",
      "Galactoside alpha-(12)-fucosyltransferase 2",
      "GDP-L-fucose:beta-D-galactoside 2-alpha-L-fucosyltransferase 2",
      "secretor factor",
      "Fucosyltransferase 2",
      "SE2",
      "secretor blood group alpha-2-fucosyltransferase",
      "Alpha(12)FT 2",
      "2.4.1.344",
      "Se",
      "2.4.1.69",
      "Type 1 galactoside alpha-(12)-fucosyltransferase FUT2",
      "galactoside 2-alpha-L-fucosyltransferase 2",
      "alpha (12) fucosyltransferase",
      "Secretor factor",
      "fucosyltransferase 2",
      "FUT2",
      "TRA2.10",
      "MGC26544",
      "TLX",
      "MCP",
      "MIC10",
      "Membrane cofactor protein",
      "Trophoblast leukocyte common antigen",
      "CD46 molecule",
      "CD46",
      "IL1F2",
      "IL-1B",
      "IL1-BETA",
      "IL-1 beta",
      "Catabolin",
      "Interleukin-1 beta",
      "interleukin 1 beta",
      "IL1B",
      "CSIF",
      "TGIF",
      "IL10A",
      "IL-10",
      "Cytokine synthesis inhibitory factor",
      "Interleukin-10",
      "cytokine synthesis inhibitory factor",
      "T-cell growth inhibitory factor",
      "interleukin 10",
      "IL10",
      "SCYB8",
      "LUCT",
      "LECT",
      "MDNCF",
      "TSG-1",
      "IL-8",
      "NAP-1",
      "3-10C",
      "MONAP",
      "AMCF-I",
      "LYNAP",
      "NAF",
      "b-ENAP",
      "GCP-1",
      "K60",
      "GCP1",
      "NAP1",
      "IL8",
      "granulocyte chemotactic protein 1",
      "C-X-C motif chemokine 8",
      "Interleukin-8",
      "Neutrophil-activating protein 1",
      "Monocyte-derived neutrophil chemotactic factor",
      "Emoctakin",
      "Granulocyte chemotactic protein 1",
      "Monocyte-derived neutrophil-activating peptide",
      "T-cell chemotactic factor",
      "tumor necrosis factor-induced gene 1",
      "neutrophil-activating peptide 1",
      "alveolar macrophage chemotactic factor I",
      "beta endothelial cell-derived neutrophil activating peptide",
      "Chemokine (C-X-C motif) ligand 8",
      "lymphocyte derived neutrophil activating peptide",
      "monocyte-derived neutrophil chemotactic factor",
      "monocyte-derived neutrophil-activating peptide",
      "lung giant cell carcinoma-derived chemotactic protein",
      "Protein 3-10C",
      "C-X-C motif chemokine ligand 8",
      "CXCL8",
      "PRL",
      "Prolactin",
      "prolactin",
      "STC",
      "Stanniocalcin-1",
      "STC-1",
      "stanniocalcin 1",
      "STC1",
      "UCNI",
      "SRP",
      "URP",
      "UCN-II",
      "Stresscopin-related peptide",
      "Urocortin II",
      "Urocortin-related peptide",
      "Ucn II",
      "prepro-urocortin 2",
      "Urocortin-2",
      "urocortin 2",
      "UCN2",
      "IFN-gamma",
      "Interferon gamma",
      "Immune interferon",
      "interferon gamma",
      "IFNG",
      "hToll",
      "CD284",
      "TLR-4",
      "ARMD10",
      "3.2.2.6",
      "Toll-like receptor 4",
      "toll like receptor 4",
      "TLR4",
      "LARC",
      "MIP-3a",
      "exodus-1",
      "ST38",
      "CKb4",
      "MIP3A",
      "SCYA20",
      "C-C motif chemokine 20",
      "CC chemokine LARC",
      "Macrophage inflammatory protein 3 alpha",
      "Beta-chemokine exodus-1",
      "Small-inducible cytokine A20",
      "MIP-3-alpha",
      "Liver and activation-regulated chemokine",
      "C-C motif chemokine ligand 20",
      "CCL20",
      "p33",
      "TNFSF3",
      "TNFC",
      "Lymphotoxin-beta",
      "Tumor necrosis factor C",
      "TNF-C",
      "TNF superfamily member 3",
      "LT-beta",
      "Tumor necrosis factor ligand superfamily member 3",
      "lymphotoxin beta",
      "LTB",
      "TNFSF2",
      "DIF",
      "TNF-alpha",
      "TNFA",
      "TNF-a",
      "Cachectin",
      "TNF superfamily member 2",
      "Tumor necrosis factor ligand superfamily member 2",
      "Tumor necrosis factor",
      "tumor necrosis factor",
      "TNF",
      "T-cell surface glycoprotein CD4",
      "T-cell surface antigen T4/Leu-3",
      "CD4 molecule",
      "CD4",
      "IB1",
      "JIP-1",
      "JIP1",
      "PRKM8IP",
      "Islet-brain 1",
      "C-Jun-amino-terminal kinase-interacting protein 1",
      "JNK MAP kinase scaffold protein 1",
      "IB-1",
      "JNK-interacting protein 1",
      "Mitogen-activated protein kinase 8-interacting protein 1",
      "mitogen-activated protein kinase 8 interacting protein 1",
      "MAPK8IP1",
      "BP240",
      "KIAA0728",
      "FLJ21489",
      "FLJ13425",
      "FLJ32235",
      "FLJ30627",
      "CATX-15",
      "BPA",
      "MACF2",
      "BP230",
      "BPAG1",
      "DMH",
      "DT",
      "Hemidesmosomal plaque protein",
      "Dystonin",
      "230 kDa bullous pemphigoid antigen",
      "Bullous pemphigoid antigen",
      "Bullous pemphigoid antigen 1",
      "Dystonia musculorum protein",
      "230/240 kDa bullous pemphigoid antigen",
      "dystonin",
      "DST",
      "STAR",
      "GUC2C",
      "Intestinal guanylate cyclase",
      "4.6.1.2",
      "STA receptor",
      "GC-C",
      "Guanylyl cyclase C",
      "Heat-stable enterotoxin receptor",
      "hSTAR",
      "heat stable enterotoxin receptor",
      "guanylate cyclase 2C",
      "GUCY2C",
      "STC-2",
      "Stanniocalcin-related protein",
      "STCRP",
      "STC-related protein",
      "Stanniocalcin-2",
      "stanniocalcin 2",
      "STC2",
      "H2R",
      "Histamine H2 receptor",
      "HH2R",
      "Gastric receptor I",
      "histamine receptor H2",
      "HRH2",
      "bA225H22.7",
      "FAM26A",
      "Calcium homeostasis modulator protein 3",
      "Protein A",
      "calcium homeostasis modulator 3",
      "CALHM3",
      "CD142",
      "tissue factor",
      "Tissue factor",
      "Thromboplastin",
      "Coagulation factor III",
      "coagulation factor III tissue factor",
      "F3",
      "PBK1",
      "L12",
      "DKFZP564M182",
      "CSIG",
      "UTP30",
      "CATX11",
      "Ribosomal L1 domain-containing protein 1",
      "CATX-11",
      "Cellular senescence-inhibited gene protein",
      "Protein PBK1",
      "ribosomal L1 domain containing 1",
      "RSL1D1",
      "MTM",
      "metallothionein 1D pseudogene",
      "MT1DP",
      "MAKV",
      "Hormonally up-regulated neu tumor-associated kinase",
      "Serine/threonine-protein kinase MAK-V",
      "2.7.11.1",
      "B19",
      "hormonally up-regulated Neu-associated kinase",
      "HUNK",
      "PSA",
      "APS",
      "P-30 antigen",
      "3.4.21.77",
      "Kallikrein-3",
      "Prostate-specific antigen",
      "Gamma-seminoprotein",
      "Seminin",
      "Semenogelase",
      "kallikrein related peptidase 3",
      "KLK3",
      "prepro-coagulation factor II",
      "Coagulation factor II",
      "Prothrombin",
      "3.4.21.5",
      "coagulation factor II thrombin",
      "F2",
      "HUSI-I",
      "ALK1",
      "ALP",
      "BLPI",
      "HUSI",
      "WAP4",
      "WFDC4",
      "Antileukoproteinase",
      "Seminal proteinase inhibitor",
      "WAP four-disulfide core domain protein 4",
      "Mucus proteinase inhibitor",
      "Secretory leukocyte protease inhibitor",
      "HUSI-1",
      "antileukoproteinase",
      "Protease inhibitor WAP4",
      "MPI",
      "secretory leukocyte peptidase inhibitor",
      "SLPI"
   ],
   "terms25":[
      "DHEA-ST",
      "HST",
      "STD",
      "ST2",
      "Bile salt sulfotransferase",
      "Dehydroepiandrosterone sulfotransferase",
      "SULT2A3",
      "2.8.2.14",
      "Hydroxysteroid Sulfotransferase",
      "Sulfotransferase 2A1",
      "2.8.2.2",
      "DHEA-ST8",
      "ST2A1",
      "sulfotransferase family 2A member 1",
      "SULT2A1",
      "IB1099",
      "ETL1",
      "EPITEMPIN",
      "EPT",
      "Epitempin-1",
      "Leucine-rich glioma-inactivated protein 1",
      "leucine rich glioma inactivated 1",
      "LGI1",
      "C4BP",
      "PRP",
      "C4bp",
      "Proline-rich protein",
      "C4b-binding protein alpha chain",
      "complement component 4 binding protein alpha",
      "C4BPA",
      "MDP",
      "RDP",
      "Dehydropeptidase-I",
      "Beta-lactamase",
      "Renal dipeptidase",
      "3.4.13.19",
      "Microsomal dipeptidase",
      "hRDP",
      "Dipeptidase 1",
      "3.5.2.6",
      "dipeptidase 1",
      "DPEP1",
      "A3GALNT",
      "A3GALT1",
      "ABO alpha 1-3-N-acetylgalactosaminyltransferase and alpha 1-3-galactosyltransferase",
      "ABO",
      "MTA1-L1",
      "MTA1L1",
      "PID",
      "Metastasis-associated protein MTA2",
      "MTA1-L1 protein",
      "p53 target protein in deacetylase complex",
      "Metastasis-associated 1-like 1",
      "metastasis associated 1 family member 2",
      "MTA2",
      "TMP",
      "CL-20",
      "B4B",
      "Epithelial membrane protein 1",
      "Protein B4B",
      "EMP-1",
      "Tumor-associated membrane protein",
      "epithelial membrane protein 1",
      "EMP1",
      "HLF2",
      "GIG12",
      "LF",
      "Growth-inhibiting protein 12",
      "Talalactoferrin",
      "Lactotransferrin",
      "3.4.21.-",
      "Lactoferrin",
      "lactotransferrin",
      "LTF",
      "CD66e",
      "CEA",
      "Carcinoembryonic antigen-related cell adhesion molecule 5",
      "Carcinoembryonic antigen",
      "Meconium antigen 100",
      "CEA cell adhesion molecule 5",
      "CEACAM5",
      "ANX4",
      "P32.5",
      "Annexin A4",
      "35-beta calcimedin",
      "Endonexin I",
      "Lipocortin IV",
      "Placental anticoagulant protein II",
      "Chromobindin-4",
      "Annexin IV",
      "PP4-X",
      "Carbohydrate-binding protein p33/p41",
      "Protein II",
      "Annexin-4",
      "PAP-II",
      "annexin A4",
      "ANXA4",
      "PRO1557",
      "PRO2086",
      "Beta-1 metal-binding globulin",
      "serotransferrin",
      "Serotransferrin",
      "Siderophilin",
      "Transferrin",
      "transferrin",
      "TF",
      "Activating transcription factor 3",
      "Cyclic AMP-dependent transcription factor ATF-3",
      "cAMP-dependent transcription factor ATF-3",
      "activating transcription factor 3",
      "ATF3",
      "SERS",
      "SARS",
      "Seryl-tRNA(Ser/Sec) synthetase",
      "Serine--tRNA ligase cytoplasmic",
      "serine tRNA ligase 1 cytoplasmic",
      "Seryl-tRNA synthetase",
      "SerRS",
      "6.1.1.11",
      "seryl-tRNA synthetase 1",
      "SARS1",
      "AREGB",
      "SDGF",
      "CRDGF",
      "Colorectum cell-derived growth factor",
      "AR",
      "Amphiregulin",
      "amphiregulin",
      "AREG",
      "MDA-5",
      "Hlcd",
      "MDA5",
      "IDDM19",
      "RH116",
      "Helicase with 2 CARD domains",
      "3.6.4.13",
      "CADM-140 autoantigen",
      "Clinically amyopathic dermatomyositis autoantigen 140 kDa",
      "melanoma differentiation-associated gene 5",
      "Interferon-induced with helicase C domain protein 1",
      "RNA helicase-DEAD box protein 116",
      "RLR-2",
      "Interferon-induced helicase C domain-containing protein 1",
      "helicard",
      "Murabutide down-regulated protein",
      "Helicard",
      "RIG-I-like receptor 2",
      "Melanoma differentiation-associated protein 5",
      "interferon induced with helicase C domain 1",
      "IFIH1",
      "IL-6",
      "BSF2",
      "HGF",
      "HSF",
      "IFNB2",
      "Interleukin-6",
      "interferon beta 2",
      "Hybridoma growth factor",
      "BSF-2",
      "IFN-beta-2",
      "CDF",
      "CTL differentiation factor",
      "B-cell stimulatory factor 2",
      "Interferon beta-2",
      "interleukin 6",
      "IL6",
      "BLAU",
      "CD",
      "PSORAS1",
      "CLR16.3",
      "NLRC2",
      "CARD15",
      "IBD1",
      "Caspase recruitment domain-containing protein 15",
      "nucleotide-binding oligomerization domain leucine rich repeat and CARD domain containing 2",
      "NLR family CARD domain containing 2",
      "Inflammatory bowel disease protein 1",
      "Nucleotide-binding oligomerization domain-containing protein 2",
      "NOD-like receptor C2",
      "nucleotide binding oligomerization domain containing 2",
      "NOD2",
      "RIG-I",
      "FLJ13599",
      "DKFZp434J1111",
      "RIG-1",
      "RIG1",
      "Retinoic acid-inducible gene 1 protein",
      "DEAD box protein 58",
      "Antiviral innate immune response receptor RIG-I",
      "Retinoic acid-inducible gene I protein",
      "Probable ATP-dependent RNA helicase DDX58",
      "retinoic acid inducible gene I",
      "RIG-I-like receptor 1",
      "RLR-1",
      "RNA helicase RIG-I",
      "DExD/H-box helicase 58",
      "DDX58",
      "P21",
      "CIP1",
      "WAF1",
      "SDI1",
      "CAP20",
      "p21CIP1",
      "p21Cip1/Waf1",
      "p21",
      "CDKN1",
      "MDA6",
      "PIC1",
      "MDA-6",
      "CDK-interacting protein 1",
      "Melanoma differentiation-associated protein 6",
      "Cyclin-dependent kinase inhibitor 1",
      "cyclin dependent kinase inhibitor 1A",
      "CDKN1A",
      "IL-2",
      "TCGF",
      "T cell growth factor",
      "T-cell growth factor",
      "Interleukin-2",
      "interleukin 2",
      "IL2",
      "NLRC1",
      "CLR7.1",
      "CARD4",
      "NLR family CARD domain containing 1",
      "Nucleotide-binding oligomerization domain-containing protein 1",
      "nucleotide-binding oligomerization domain leucine rich repeat and CARD domain containing 1",
      "Caspase recruitment domain-containing protein 4",
      "nucleotide binding oligomerization domain containing 1",
      "NOD1",
      "CMP",
      "CRTM",
      "Matrilin-1",
      "Cartilage matrix protein",
      "matrilin 1",
      "MATN1",
      "PCD",
      "DCOH",
      "PCBD",
      "PHS",
      "pterin-4-alpha carbinolamine dehydratase",
      "Pterin-4a-carbinolamine dehydratase (dimerization cofactor of hepatic nuclear factor 1-alpha)",
      "dimerizing cofactor for HNF1",
      "4.2.1.96",
      "DCoH",
      "Phenylalanine hydroxylase-stimulating protein",
      "Pterin-4-alpha-carbinolamine dehydratase",
      "Dimerization cofactor of hepatocyte nuclear factor 1-alpha",
      "Dimerization cofactor of HNF1",
      "4-alpha-hydroxy-tetrahydropterin dehydratase",
      "Pterin carbinolamine dehydratase",
      "pterin-4 alpha-carbinolamine dehydratase 1",
      "PCBD1",
      "1.16.3.1",
      "Ceruloplasmin",
      "ferroxidase",
      "Ferroxidase",
      "ceruloplasmin",
      "CP",
      "CDHF4",
      "Pemphigus foliaceus antigen",
      "DG1",
      "Cadherin family member 4",
      "Desmoglein-1",
      "DGI",
      "Desmosomal glycoprotein 1",
      "desmoglein 1",
      "DSG1"
   ],
   "terms5":[
      "DHEA-ST",
      "HST",
      "STD",
      "ST2",
      "Bile salt sulfotransferase",
      "Dehydroepiandrosterone sulfotransferase",
      "SULT2A3",
      "2.8.2.14",
      "Hydroxysteroid Sulfotransferase",
      "Sulfotransferase 2A1",
      "2.8.2.2",
      "DHEA-ST8",
      "ST2A1",
      "sulfotransferase family 2A member 1",
      "SULT2A1",
      "IB1099",
      "ETL1",
      "EPITEMPIN",
      "EPT",
      "Epitempin-1",
      "Leucine-rich glioma-inactivated protein 1",
      "leucine rich glioma inactivated 1",
      "LGI1",
      "C4BP",
      "PRP",
      "C4bp",
      "Proline-rich protein",
      "C4b-binding protein alpha chain",
      "complement component 4 binding protein alpha",
      "C4BPA",
      "MDP",
      "RDP",
      "Dehydropeptidase-I",
      "Beta-lactamase",
      "Renal dipeptidase",
      "3.4.13.19",
      "Microsomal dipeptidase",
      "hRDP",
      "Dipeptidase 1",
      "3.5.2.6",
      "dipeptidase 1",
      "DPEP1",
      "A3GALNT",
      "A3GALT1",
      "ABO alpha 1-3-N-acetylgalactosaminyltransferase and alpha 1-3-galactosyltransferase",
      "ABO"
   ],
   "multiplier":1.0072873555874382
}
```



## so

[http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/so/ontology-so-2021-02-09.json](http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/so/ontology-so-2021-02-09.json)

```text
{
   "@id":"obo:SO_0000000",
   "@type":"owl:Class",
   "hasOBONamespace":"sequence",
   "id":"SO:0000000",
   "inSubset":[
      "so:SOFA"
   ],
   "label":"Sequence_Ontology",
   "owl:deprecated":true,
   "subClassOf":[
      
   ],
   "hasExactSynonym":[
      
   ],
   "hasDbXref":[
      
   ],
   "hasAlternativeId":[
      
   ]
}
```



Targets

{% embed url="http://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/targets/" %}

```text
{
   "id":"ENSG00000001561",
   "approvedName":"ectonucleotide pyrophosphatase/phosphodiesterase 4",
   "approvedSymbol":"ENPP4",
   "bioType":"protein_coding",
   "hgncId":"HGNC:3359",
   "reactome":[
      "R-HSA-6798695"
   ],
   "nameSynonyms":[
      "E-NPP 4",
      "3.6.1.29",
      "Bis(5'-adenosyl)-triphosphatase",
      "Bis(5'-adenosyl)-triphosphatase ENPP4",
      "Ectonucleotide pyrophosphatase/phosphodiesterase family member 4",
      "AP3Aase",
      "NPP-4",
      "AP3A hydrolase"
   ],
   "symbolSynonyms":[
      "NPP4",
      "KIAA0879",
      "AP3Aase"
   ],
   "genomicLocation":{
      "chromosome":"6",
      "start":46129989,
      "end":46146688,
      "strand":1
   },
   "proteinAnnotations":{
      "id":"Q9Y6X5",
      "accessions":[
         "Q7L2N1",
         "Q9Y6X5",
         "A8K5G1"
      ],
      "functions":[
         "Hydrolyzes extracellular Ap3A into AMP and ADP, and Ap4A into AMP and ATP. Ap3A and Ap4A are diadenosine polyphosphates thought to induce proliferation of vascular smooth muscle cells. Acts as a procoagulant, mediating platelet aggregation at the site of nascent thrombus via release of ADP from Ap3A and activation of ADP receptors."
      ],
      "pathways":[
         
      ],
      "similarities":[
         "Belongs to the nucleotide pyrophosphatase/phosphodiesterase family."
      ],
      "subcellularLocations":[
         "Cell membrane"
      ],
      "subunits":[
         
      ]
   },
   "tractability":{
      "antibody":{
         "buckets":[
            4,
            5,
            7
         ],
         "categories":{
            "clinical_precedence":0.0,
            "predicted_tractable_high_confidence":1.0,
            "predicted_tractable_med_low_confidence":0.25
         },
         "top_category":"Predicted_Tractable_ab_High_confidence"
      },
      "smallmolecule":{
         "buckets":[
            4
         ],
         "categories":{
            "clinical_precedence":0.0,
            "discovery_precedence":0.7,
            "predicted_tractable":0.0
         },
         "high_quality_compounds":0,
         "small_molecule_genome_member":false,
         "top_category":"Discovery_Precedence_sm"
      }
   },
   "go":[
      {
         "id":"GO:0070062",
         "value":{
            "evidence":"ECO_0007005",
            "project":"UniProtKB",
            "term":"C:extracellular exosome"
         }
      },
      {
         "id":"GO:0101003",
         "value":{
            "evidence":"ECO_0000304",
            "project":"Reactome",
            "term":"C:ficolin-1-rich granule membrane"
         }
      },
      {
         "id":"GO:0016021",
         "value":{
            "evidence":"ECO_0000501",
            "project":"UniProtKB-KW",
            "term":"C:integral component of membrane"
         }
      },
      {
         "id":"GO:0016020",
         "value":{
            "evidence":"ECO_0007005",
            "project":"UniProtKB",
            "term":"C:membrane"
         }
      },
      {
         "id":"GO:0005886",
         "value":{
            "evidence":"ECO_0000304",
            "project":"Reactome",
            "term":"C:plasma membrane"
         }
      },
      {
         "id":"GO:0047710",
         "value":{
            "evidence":"ECO_0000314",
            "project":"UniProtKB",
            "term":"F:bis(5'-adenosyl)-triphosphatase activity"
         }
      },
      {
         "id":"GO:0046872",
         "value":{
            "evidence":"ECO_0000501",
            "project":"UniProtKB-KW",
            "term":"F:metal ion binding"
         }
      },
      {
         "id":"GO:0007596",
         "value":{
            "evidence":"ECO_0000501",
            "project":"UniProtKB-KW",
            "term":"P:blood coagulation"
         }
      },
      {
         "id":"GO:0043312",
         "value":{
            "evidence":"ECO_0000304",
            "project":"Reactome",
            "term":"P:neutrophil degranulation"
         }
      },
      {
         "id":"GO:0030194",
         "value":{
            "evidence":"ECO_0000314",
            "project":"UniProtKB",
            "term":"P:positive regulation of blood coagulation"
         }
      },
      {
         "id":"GO:0046130",
         "value":{
            "evidence":"ECO_0000314",
            "project":"UniProtKB",
            "term":"P:purine ribonucleoside catabolic process"
         }
      }
   ],
   "hallMarks":{
      
   }
}
```

