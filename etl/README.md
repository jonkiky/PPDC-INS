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

[**platform-input-support**](https://github.com/opentargets/platform-input-support) ****- scripts that process and prepare data for our ETL pipelines 

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

### EFO step \(disease\)

The EFO step is used to gather the raw data for the [platform ETL](https://github.com/opentargets/platform-etl-backend).

The scope of EFO is to support the annotation, analysis and visualization of data handled by the core ontology for Open Targets.

This step downloads and manipulates the input files and it generates the following output:

* ontology-efo-v3.xx.yy.jsonl : list of EFO terms
* ontology-mondo.jsonl : list of MONDO terms
* ontology-hpo.jsonl : list of HPO terms
* hpo-phenotypes-_yyyy-mm-dd_.jsonl : mapping between CrossReference databaseId

### Drug step

The Drug step is used to gather the raw data for the [platform ETL](https://github.com/opentargets/platform-etl-backend).

ChEMBL have made an Elasticsearch instance available for querying. To keep data volumes and running times down specify the index and fields which are required in the config file.

ChEMBL's ES instance is only available from within the EMBL-EBI VPN. If you need to run this step it is necessary that you use a machine that is connected to the VPN network.



## Data pipeline

[**data\_pipeline**](https://github.com/opentargets/data_pipeline)  ****to process different data files that provide evidence for the target-disease associations in the Open Targets Platform. ****

{% embed url="https://github.com/opentargets/data\_pipeline" %}



#### Overview

The pipeline can be broken down in a number of steps, each of which can be run as a separate command. Each command typically reads data from one or more sources \(such as a URL or local file, or Elasticsearch\) and writes into one or more Elasticsearch indexes.

**--rea Reactome**

Downloads and processes information into a local index for performance.

**--hpa Expression**

Downloads and processes information into a local index for performance.

**--gen Target**

Downloads and processes information from various sources. Is built around a "plugin" structure. Constructs an Elasticsarch index containg most of the information about each Target within the platform. It requires `--rea` reactome step. Note: HGNC,Ensembl,Uniprot plugins should always be first, as they initialize the gene list used in other plugins. Note: Chembl is required by the `--sea` step below.

**--efo Disease**

Downloads and processes the Experimental Factor Ontology, as well as Human Phenotype Ontology and other sources. Constructs an Elasticsarch index containg the information about each Disease within the platform.

**--eco Evidence Code**

Downloads and processes the Evidence Code Ontology and Sequence Ontology.

**--val Validation**

Read in evidence strings \(either from filesystem or URLs\) and validate. The validation includes syntatic JSON schema validation, as well as ensuring that the disease and target are appropriate. This step will also make some corrections to evidence, where appropriate. For example,replacing Uniprot protein identifiers with Ensembl gene identifiers. It requires `--gen` target, `--efo` disease, and `--eco` evidence code steps. It is expecting JSON matching schema [1.6.0](https://raw.githubusercontent.com/opentargets/json_schema/1.6.0/opentargets.json).

**--as Associations**

This step reads the valide evidence strings and calculates the appropriate assocations as well as calculated their scores. It requires `--val` validation, and `--hpa` expression steps.

**--sea Search**

This step will create the index `${DATA_RELEASE_VERSION}_search-data` which is used for the search function in the platform. It requires `--as` associations step.

**--ddr Relationships**

This step will compute the target-to-target and disease-to-disease relationships. It requires `--as` associations step.  


![](../.gitbook/assets/screen-shot-2021-04-09-at-1.33.13-pm.png)



Inputs:

{% embed url="https://docs.targetvalidation.org/technical-pipeline/technical-notes" %}

Command line template: https://github.com/opentargets/data\_pipeline/blob/master/mrtarget.ops.yml

ES: https://github.com/opentargets/data\_pipeline/blob/master/mrtarget.es.yml

### **--rea Reactome** 

**part of annotations data**

ReactomeProcess\(args.elasticseach\_nodes, es\_config.rea.name, es\_config.rea.mapping, es\_config.rea.setting, data\_config.reactome\_pathway\_data, data\_config.reactome\_pathway\_relation, args.rea\_workers\_writer, args.rea\_queue\_write\)

process\_all\(\)

-&gt; Reactome.py 

1. Generate a direct graph

Node from : reactome-pathway-data: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ReactomePathways-2021-02-09.txt](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ReactomePathways-2021-02-09.txt)   
Edge from: reactome-pathway-relation: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ReactomePathwaysRelation-2021-02-09.txt](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ReactomePathwaysRelation-2021-02-09.txt)

Node:{ id, name, species }

Edge:{id, child\_id}

2.  Save Graph to elastic search   
mapping: rea\_mappings.json

setting: rea\_settings.json 

docs = generate\_documents\(self.g\)

actions = elasticsearch\_actions\(docs, self.es\_index\)

set of dicts :dict\(id=node, label=node\_data\['name'\], path=paths, children=children, parents=parents, is\_root=node == 'root', ancestors=list\(ancestors\) \)



### **--hpa Expression**

\*\*\*\*

HPAProcess\(args.elasticseach\_nodes, es\_config.hpa.name, es\_config.hpa.mapping, es\_config.hpa.setting, data\_config.tissue\_translation\_map, data\_config.tissue\_curation\_map, data\_config.hpa\_normal\_tissue, data\_config.hpa\_rna\_level, data\_config.hpa\_rna\_value, data\_config.hpa\_rna\_zscore, args.hpa\_workers\_writer, args.hpa\_queue\_write\)

**inputs:**

args.elasticseach\_nodes,   
 es\_config.  
 hpa.name,   
 es\_config.hpa.mapping,   
 es\_config.hpa.setting,   
 data\_config.tissue\_translation\_map: none  
 data\_config.tissue\_curation\_map: none  
 hpa-normal-tissue: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/normal\_tissue-2021-02-09.tsv](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/normal_tissue-2021-02-09.tsv)  
 hpa-rna-level: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline\_expression\_binned-2020-05-07.tsv](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline_expression_binned-2020-05-07.tsv)  
 hpa-rna-value: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline\_expression\_counts-2020-05-07.tsv](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline_expression_counts-2020-05-07.tsv)  
 hpa-rna-zscore: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline\_expression\_zscore\_binned-2020-05-07.tsv](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/baseline_expression_zscore_binned-2020-05-07.tsv)  
 args.hpa\_workers\_writer,   
 args.hpa\_queue\_write  


process\_all

```text
 self.hpa_normal_table = self.downloader.retrieve_normal_tissue_data()
        self.hpa_rna_table = self.downloader.retrieve_rna_data()
        self.hpa_merged_table = self.process_join()
        self.store_data(dry_run)
```

  
retrieve\_normal\_tissue\_data-&gt; download data from hpa-normal-tissue as CSV file, use it as a dictionary object.

retrieve\_rna\_data:  read data from hpa-rna-level and hpa-rna-zscore, then  melting rna level table into geneid tissue level.

process\_join\(\)-&gt;  melting retrieve\_normal\_tissue\_data and retrieve\_rna\_data, plus new format of expression \(dictionary\)

store\_data-&gt; save hpa\_merged\_table to elasticsearch

### **--gen Target**

```text
 process = GeneManager(args.elasticseach_nodes, es_config.gen.name, 
            es_config.gen.mapping, es_config.gen.setting, 
            args.gen_plugin_places, data_config.gene_data_plugin_names,
            data_config, es_config,
            args.gen_workers_writer, args.gen_queue_write )
        if not args.qc_only:
            process.merge_all(args.dry_run)
        if not args.skip_qc:
            qc_metrics.update(process.qc(es, es_config.gen.name))  
```

**inputs:**

args.elasticseach\_nodes  
 es\_config.gen.name  
 es\_config.gen.mapping  
 es\_config.gen.setting  
 args.gen\_plugin\_places  
 data\_config.gene\_data\_plugin\_names**:  null???**  
 data\_config  
 es\_config  
 args.gen\_workers\_writer  
 args.gen\_queue\_write



plugin system : [http://yapsy.sourceforge.net/\#](http://yapsy.sourceforge.net/#)

```text
plugin.plugin_object.merge_data(self.genes, 
                es, None, 
                self.data_config, self.es_config)
```

It seems like the genes obj is modified within a plugin.

```text
 gene._create_suggestions()
```

reorder gene's field, add suggestion filed, code below shows the content of suggestions. 

```text
    field_order = [self.approved_symbol,
                       self.approved_name,
                       self.symbol_synonyms,
                       self.name_synonyms,
                       self.previous_symbols,
                       self.previous_names,
                       self.uniprot_id,
                       self.uniprot_accessions,
                       self.ensembl_gene_id,
                       self.entrez_gene_id,
                       self.refseq_ids
                       ]
   self._private['suggestions'] = dict(input = [],
                                              output = self.approved_symbol,
                                              payload = dict(gene_id = self.id,
                                                             gene_symbol = self.approved_symbol,
                                                             gene_name = self.approved_name),
                                              )


        for field in field_order:
            if isinstance(field, list):
                self._private['suggestions']['input'].extend(field)
            else:
                self._private['suggestions']['input'].append(field)
        try:
            self._private['suggestions']['input'] = [x.lower() for x in self._private['suggestions']['input']]
        except:
            print("error", repr(self._private['suggestions']['input']))
```

```text
gene._create_facets()
```

add pathway info in gene.\_create\_facets\(\) step.  code below shows how it does. 

```text
 self._private['facets']['reactome']=dict(pathway_code = pathways,
              # pathway_name=pathways,
               pathway_type_code=pathway_types,
              # pathway_type_name=pathway_types,
  )
```

  
Then gene is stored in elastic search. 

### **--efo Disease**

```text
  process = EfoProcess(args.elasticseach_nodes, es_config.efo.name, 
            es_config.efo.mapping, es_config.efo.setting, 
            data_config.ontology_efo, data_config.ontology_hpo, 
            data_config.ontology_mp, data_config.disease_phenotype,
            args.efo_workers_writer, args.efo_queue_write)
        if not args.qc_only:
            process.process_all(args.dry_run)
```

**inputs:**

args.elasticseach\_nodes  
 es\_config.efo.name  
 es\_config.efo.mapping  
 es\_config.efo.setting  
ontology-efo: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/efo\_otar\_slim.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/efo_otar_slim.owl)  
 ontology-hpo: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/hp.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/hp.owl)  
 ontology-mp: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-mp-2021-02-08.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-mp-2021-02-08.owl)  
 disease-phenotype:- [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ibd\_2\_pheno\_associations-2021-02-08.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ibd_2_pheno_associations-2021-02-08.owl)  
 args.efo\_workers\_writer  
 args.efo\_queue\_write

**process\_all**

```text
def process_all(self, dry_run):
        self._process_ontology_data()
        self._store_efo(dry_run)

```

rprocess\_ontology\_data:

refers to : [https://github.com/opentargets/ontology-utils](https://github.com/opentargets/ontology-utils)

create a text block definition/description by joining others together

build a set of all the relevant synonyms

\*need to dig into ontology utils and EFO.py

**\_store\_efo**

store data into elasticsearch





### **--eco Evidence Code** 

```text
process = EcoProcess(args.elasticseach_nodes, es_config.eco.name, 
            es_config.eco.mapping, es_config.eco.setting,
            data_config.ontology_eco, data_config.ontology_so,
            args.eco_workers_writer, args.eco_queue_write)
        if not args.qc_only:
            process.process_all(args.dry_run)
```

**inputs:**

args.elasticseach\_nodes  
 es\_config.eco.name  
 es\_config.eco.mapping  
 es\_config.eco.setting  
 data\_config.ontology-eco: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-eco-2021-02-09.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-eco-2021-02-09.owl)  
 data\_config.ontology-so: [https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-so-2021-02-09.owl](https://storage.googleapis.com/open-targets-data-releases/21.02/input/annotation-files/ontology/ontology-so-2021-02-09.owl)  
 args.eco\_workers\_writer  
 args.eco\_queue\_write

**process\_all**

```text
def process_all(self, dry_run):
        self._process_ontology_data()
        self._store_eco(dry_run)
```

  
**process\_ontology\_data:**

Loads evidence from ECO, SO and the Open Targets evidence classes

Namespace**??** classes\_paths??

The codes below are from [https://github.com/opentargets/ontology-utils](https://github.com/opentargets/ontology-utils)  
eco\_so.py

```text
cttv = rdflib.Namespace(str("http://www.targetvalidation.org/disease"))
    ot = rdflib.Namespace(str("http://identifiers.org/eco"))

    #namespace_manager = NamespaceManager(self.rdf_graph)
    ocr.rdf_graph.namespace_manager.bind('cttv', cttv)
    ocr.rdf_graph.namespace_manager.bind('ot',ot)

    open_targets_terms = {
        'http://www.targetvalidation.org/disease/cttv_evidence':'CTTV evidence',
        'http://identifiers.org/eco/drug_disease':'drug-disease evidence',
        'http://identifiers.org/eco/target_drug':'biological target to drug evidence',
        'http://identifiers.org/eco/clinvar_gene_assignments':'ClinVAR SNP-gene pipeline',
        'http://identifiers.org/eco/cttv_mapping_pipeline':'CTTV-custom annotation pipeline',
        'http://identifiers.org/eco/GWAS':'Genome-wide association study evidence',
        'http://identifiers.org/eco/GWAS_fine_mapping': 'Fine-mapping study evidence',
        'http://identifiers.org/eco/somatic_mutation_evidence':'Somatic mutation evidence',
        'http://www.targetvalidation.org/evidence/genomics_evidence':'genomics evidence',
        'http://targetvalidation.org/sequence/nearest_gene_five_prime_end':'Nearest gene counting from 5&apos; end',
        'http://targetvalidation.org/sequence/regulatory_nearest_gene_five_prime_end':'Nearest regulatory gene from 5&apos; end',
        'http://www.targetvalidation.org/evidence/literature_mining':'Literature mining',
        'http://www.targetvalidation.org/provenance/DatabaseProvenance':'database provenance',
        'http://www.targetvalidation.org/provenance/ExpertProvenance':'expert provenance',
        'http://www.targetvalidation.org/provenance/GWAS_SNP_to_trait_association':'GWAS SNP to trait association',
        'http://www.targetvalidation.org/provenance/LiteratureProvenance':'literature provenance',
        'http://www.targetvalidation.org/provenance/disease_to_phenotype_association':'disease to phenotype association',
        'http://www.targetvalidation.org/provenance/gene_to_disease_association':'gene to disease association',
        'http://identifiers.org/eco/locus_to_gene_pipeline':'Open Targets Genetics portal locus to gene annotation pipeline',
        'http://identifiers.org/eco/PheWAS': 'PheWAS catalog evidence'
    }

    for uri, label in open_targets_terms.items():
        u = rdflib.URIRef(uri)
        ocr.rdf_graph.add((u, rdflib.RDF.type, rdflib.term.URIRef(u'http://www.w3.org/2002/07/owl#Class')))
        ocr.rdf_graph.add([u, rdflib.RDFS.label, rdflib.Literal(label)])
        ocr.rdf_graph.add([u, rdflib.RDFS.subClassOf, evidence_uri])

```

add info into  evidence\_ontology.rdf\_graph  and evidence\_ontology.classes\_paths 

generate eco object, store into database.

```text
 eco = ECO(uri,
                      label,
                      self.evidence_ontology.classes_paths[uri]['all'],
                      self.evidence_ontology.classes_paths[uri]['ids'],
                      self.evidence_ontology.classes_paths[uri]['labels']
                      )

```



### **--val Validation** 

TO BE DONE

###  **--as Associations**

```text
if args.assoc:
        process = ScoringProcess(args.elasticseach_nodes, es_config.asc.name, 
                es_config.asc.mapping, es_config.asc.setting,
                es_config.gen.name, es_config.val_right.name, es_config.hpa.name, es_config.efo.name,
                args.as_workers_writer, args.as_workers_production, args.as_workers_score, 
                args.as_queue_score, args.as_queue_production, args.as_queue_write,
                args.as_cache_hpa, args.as_cache_efo, args.as_cache_target, 
                data_config.scoring_weights, data_config.is_direct_do_not_propagate,
                data_config.datasources_to_datatypes)
        if not args.qc_only:
            process.process_all(args.dry_run)
```

**inputs:**

args.elasticseach\_nodes  
 es\_config.asc.name  
 es\_config.asc.mapping  
 es\_config.asc.setting  
 es\_config.gen.name  
 es\_config.val\_right.name  
 es\_config.hpa.name  
 es\_config.efo.name  
 args.as\_workers\_writer  
 args.as\_workers\_production  
 args.as\_workers\_score  
 args.as\_queue\_score  
 args.as\_queue\_production  
 args.as\_queue\_write  
 args.as\_cache\_hpa  
 args.as\_cache\_efo  
 args.as\_cache\_target  
 data\_config.scoring\_weights  
 data\_config.is\_direct\_do\_not\_propagate  
 data\_config.datasources\_to\_datatypes

**scoring\_weights**

```text
scoring_weights:
  crisp: 1
  europepmc: 0.2
  expression_atlas: 0.2
  phenodigm: 0.2
  progeny: 0.5
  slapenrich: 0.5
  sysbio: 0.5
```

**is\_direct\_do\_not\_propagate:**

```text
is_direct_do_not_propagate:
- expression_atlas
```

  
**datasources\_to\_datatypes:** 

```text
datasources_to_datatypes:
  cancer_gene_census: somatic_mutation
  chembl: known_drug
  clingen: genetic_association
  crispr: affected_pathway
  europepmc: literature
  eva: genetic_association
  eva_somatic: somatic_mutation
  expression_atlas: rna_expression
  gene2phenotype: genetic_association
  genomics_england: genetic_association
  gwas_catalog: genetic_association
  intogen: somatic_mutation
  ot_genetics_portal: genetic_association
  phenodigm: animal_model
  phewas_catalog: genetic_association
  postgap: genetic_association
  progeny: affected_pathway
  reactome: affected_pathway
  slapenrich: affected_pathway
  sysbio: affected_pathway
  uniprot_literature: genetic_association
  uniprot_somatic: somatic_mutation
```



**process\_all:**

pipeline stage for making the lists of the target/disease pairs and evidence

```text
pipeline_stage1 = pr.flat_map(produce_evidence, targets, 
            workers=self.workers_production,
            maxsize=self.queue_produce,
            on_start=produce_evidence_local_init_baked)
```

inputs:

produce\_evidence, is a function, which returns  \(evidence\['target'\]\['id'\], efo,evidence, is\_direct\), also it calculate the  **association\_score for each evidence.** 

```text
def produce_evidence(target, es, es_index_val_right,
        scoring_weights, is_direct_do_not_propagate, datasources_to_datatypes):
```

```text
            key = (evidence['target']['id'], efo)
            ....
            score = evidence['scores']['association_score']
            if data_source in scoring_weights:
                score = score * scoring_weights[data_source]
                ....
            row = EvidenceScore(score, data_type, data_source, is_direct)
            data_cache[key].append(row)
                   #    class EvidenceScore(object):
                   #    def __init__(self, score, datatype, datasource, is_direct):
                   #     self.score = score
                   #     self.datatype = datatype
                   #     self.datasource = datasource
                   #     self.is_direct = is_direct
           ....
           return_values.append((key[0],key[1], evidence, is_direct))
```

**targets**: from elasticsearch.

**produce\_evidence\_local\_init\_baked:**

pipeline stage for scoring the evidence sets includes writing to elasticsearch

```text
 pipeline_stage2 = pr.map(score_producer, pipeline_stage1, 
            workers=self.workers_score,
            maxsize=self.queue_score,
            on_start=score_producer_local_init_baked)
```

score\_producer is a function

```text

def score_producer(data, 
        scorer, lookup_data, datasources_to_datatypes, dry_run):
```

input:

data = target, disease, evidence, is\_direct 

```text
def score(self,target, disease, evidence_scores, is_direct, datasources_to_datatypes):

....
# init evidence_count['datasources'] and evidence_count['datatypes']
 association = Association(target, disease, is_direct, datasources, datatypes)
 
 
  # set evidence counts
        for e in evidence_scores:
            # make sure datatype is constrained
            if all([e.datatype in association.evidence_count['datatypes'],
                    e.datasource in association.evidence_count['datasources']]):
                association.evidence_count['total']+=1
                association.evidence_count['datatypes'][e.datatype]+=1
                association.evidence_count['datasources'][e.datasource]+=1

                # set facet data
                association.set_available_datatype(e.datatype)
                association.set_available_datasource(e.datasource)

## compute harmonic sum with quadratic (scale_factor) degradation
        #limit to first 100 entries and scale with afactor of 2
        self._harmonic_sum(evidence_scores, association, 100, 2, datasources_to_datatypes)

```

skip associations only with data with score 0

```text
# get gene data by target
 gene_data = Gene()
            gene_data_index = lookup_data.available_genes.get_gene(target)
            if gene_data_index != None:
                gene_data.load_json(gene_data_index)
            score.set_target_data(gene_data)

```



