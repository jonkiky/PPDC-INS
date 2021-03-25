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

###  sourceId=slapenrich/ sourceId=sysbio/ sourceId=uniprot\_literature/



