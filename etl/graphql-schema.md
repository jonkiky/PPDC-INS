# GraphQL Schema

```text
type APIVersion {
  x: Int!
  y: Int!
  z: Int!
}

# Curated target safety effects
type AdverseEffects {
  activationEffects: AdverseEffectsActivationEffects!
  inhibitionEffects: AdverseEffectsInhibitionEffects!
  organsSystemsAffected: [SafetyCode!]!
  references: [SafetyReference!]!
}

type AdverseEffectsActivationEffects {
  acuteDosing: [SafetyCode!]!
  chronicDosing: [SafetyCode!]!
  general: [SafetyCode!]!
}

type AdverseEffectsInhibitionEffects {
  acuteDosing: [SafetyCode!]!
  chronicDosing: [SafetyCode!]!
  general: [SafetyCode!]!
  developmental: [SafetyCode!]!
}

# Significant adverse event entries
type AdverseEvent {
  # Meddra term on adverse event
  name: String!

  # 8 digit unique meddra identification number
  meddraCode: String

  # Number of reports mentioning drug and adverse event
  count: Long!

  # Log-likelihood ratio
  logLR: Float!
}

# Significant adverse events inferred from FAERS reports
type AdverseEvents {
  # Total significant adverse events
  count: Long!

  # LLR critical value to define significance
  criticalValue: Float!

  # Significant adverse event entries
  rows: [AdverseEvent!]!
}

type Aggregation {
  key: String!
  uniques: Long!
  aggs: [Aggregation!]
}

input AggregationFilter {
  name: String!
  path: [String!]!
}

type Aggregations {
  uniques: Long!
  aggs: [NamedAggregation!]!
}

# Associated Disease Entity
type AssociatedDisease {
  score: Float!
  datatypeScores: [ScoredComponent!]!
  datasourceScores: [ScoredComponent!]!

  # Disease
  disease: Disease!
}

type AssociatedDiseases {
  datasources: [DatasourceSettings!]!
  aggregations: Aggregations
  count: Long!

  # Associated Targets using (On the fly method)
  rows: [AssociatedDisease!]!
}

# Associated Target Entity
type AssociatedTarget {
  score: Float!
  datatypeScores: [ScoredComponent!]!
  datasourceScores: [ScoredComponent!]!

  # Target
  target: Target!
}

type AssociatedTargets {
  datasources: [DatasourceSettings!]!
  aggregations: Aggregations
  count: Long!

  # Associated Targets using (On the fly method)
  rows: [AssociatedTarget!]!
}

# Entry on clinical relevance and drug responses of tumor genomic alterations on the target
type CancerBiomarker {
  # Target symbol and variant id
  id: String!

  # Drug responsiveness
  associationType: String!

  # Drug family or name
  drugName: String!

  # Source type
  evidenceLevel: String!

  # Sources
  sources: [CancerBiomarkerSource!]!

  # List of supporting publications
  pubmedIds: [Long!]!

  # Target entity
  target: Target!

  # Disease entity
  disease: Disease
}

# Detail on Cancer Biomarker sources
type CancerBiomarkerSource {
  # Source description
  description: String

  # Source link
  link: String

  # Source name
  name: String
}

# Set of clinical relevance and drug responses of tumor genomic alterations on the target entries
type CancerBiomarkers {
  # Number of unique drugs with response information
  uniqueDrugs: Long!

  # Number of unique cancer diseases with drug response information
  uniqueDiseases: Long!

  # Number of unique biomarkers with drug response information
  uniqueBiomarkers: Long!

  # Number of entries
  count: Long!

  # Cancer Biomarker entries
  rows: [CancerBiomarker!]!
}

type CancerHallmark {
  suppress: Boolean!
  promote: Boolean!
  reference: LiteratureReference!
  label: String!
}

type CellType {
  reliability: Boolean!
  name: String!
  level: Int!
}

# Set of potent, selective and cell-permeable chemical probes
type ChemicalProbes {
  # Probeminer chemical probe url
  probeminer: String

  # Chemical probes entries in SGC or ChemicalProbes.org
  rows: [PortalProbe!]!
}

type DataVersion {
  year: Int!
  month: Int!
  iteration: Int!
}

type DatasourceSettings {
  id: String!
  weight: Float!
  propagate: Boolean!
}

input DatasourceSettingsInput {
  id: String!
  weight: Float!
  propagate: Boolean!
}

# Disease or phenotype entity
type Disease {
  # Open Targets disease id
  id: String!

  # Disease name
  name: String!

  # Disease description
  description: String

  # List of external cross reference IDs
  dbXRefs: [String!]

  # Disease synonyms
  synonyms: [DiseaseSynonyms!]
  ancestors: [String!]!
  descendants: [String!]!

  # Ancestor therapeutic area disease entities in ontology
  therapeuticAreas: [Disease!]!

  # Disease parents entities in ontology
  parents: [Disease!]!

  # Disease children entities in ontology
  children: [Disease!]!

  # Is disease a therapeutic area itself
  isTherapeuticArea: Boolean!

  # Phenotype from HPO index
  phenotypes(page: Pagination): DiseaseHPOs

  # The complete list of all possible datasources
  evidences(
    # List of Ensembl IDs
    ensemblIds: [String!]!

    # Use disease ontology to capture evidences from all descendants to build associations
    enableIndirect: Boolean

    # List of datasource ids
    datasourceIds: [String!]
    size: Int
    cursor: String
  ): Evidences!

  # RNA and Protein baseline expression
  otarProjects: [OtarProject!]!

  # Clinical precedence for investigational or approved drugs indicated for disease and curated mechanism of action
  knownDrugs(
    # Query string
    freeTextQuery: String
    size: Int
    cursor: String
  ): KnownDrugs

  # Similar diseases based on their target association profiles
  relatedDiseases(page: Pagination): RelatedDiseases

  # associations on the fly
  associatedTargets(
    Bs: [String!]

    # Use disease ontology to capture evidences from all descendants to build associations
    enableIndirect: Boolean
    datasources: [DatasourceSettingsInput!]
    aggregationFilters: [AggregationFilter!]
    BFilter: String
    orderByScore: String
    page: Pagination
  ): AssociatedTargets!
}

# Disease and phenotypes annotations
type DiseaseHPO {
  # List of phenotype annotations.
  evidence: [DiseaseHPOEvidences!]!

  # Phenotype entity
  phenotypeHPO: HPO

  # Disease Entity
  phenotypeEFO: Disease
}

# the HPO project provides a large set of phenotype annotations. Source: Phenotype.hpoa
type DiseaseHPOEvidences {
  # One of P (Phenotypic abnormality), I (inheritance), C (onset and clinical course). Might be null (MONDO)
  aspect: String

  # This refers to the center or user making the annotation and the date on which the annotation was made
  bioCuration: String

  # This field refers to the database and database identifier. EG. OMIM
  diseaseFromSourceId: String!

  # Related name from the field diseaseFromSourceId
  diseaseFromSource: String!

  # This field indicates the level of evidence supporting the annotation.
  evidenceType: String

  # A term-id from the HPO-sub-ontology
  frequency: String

  # This optional field can be used to qualify the annotation. Values: [True or False]
  qualifierNot: Boolean!

  # This field indicates the source of the information used for the annotation (phenotype.hpoa)
  references: [String!]!

  # This field contains the strings MALE or FEMALE if the annotation in question is limited to males or females.
  sex: String

  # Possible source mapping: HPO or MONDO
  resource: String!

  # HP terms from the Clinical modifier subontology
  modifiers: [HPO!]!

  # A term-id from the HPO-sub-ontology below the term Age of onset.
  onset: [HPO!]!

  # HPO Entity
  frequencyHPO: HPO
}

# List of Phenotypes associated with the disease
type DiseaseHPOs {
  # Number of entries
  count: Long!

  # List of Disease and phenotypes annotations
  rows: [DiseaseHPO!]!
}

type DiseaseSynonyms {
  relation: String!
  terms: [String!]!
}

# Drug/Molecule entity
type Drug {
  # Open Targets molecule id
  id: String!

  # Molecule preferred name
  name: String!

  # Molecule synonyms
  synonyms: [String!]!

  # Drug trade names
  tradeNames: [String!]!

  # Year drug was approved for the first time
  yearOfFirstApproval: Int

  # Drug modality
  drugType: String!

  # Alias for maximumClinicalTrialPhase == 4
  isApproved: Boolean
  crossReferences: [DrugReferences!]

  # Maximum phase observed in clinical trial records and post-marketing package inserts
  maximumClinicalTrialPhase: Int

  # Has drug been withdrawn from the market
  hasBeenWithdrawn: Boolean!

  # Withdrawal reason
  withdrawnNotice: WithdrawnNotice

  # Indications for which there is a phase IV clinical trial
  approvedIndications: [String!]

  # Alert on life-threteaning drug side effects provided by FDA
  blackBoxWarning: Boolean!

  # Drug description
  description: String

  # ChEMBL ID of parent molecule
  parentMolecule: Drug

  # Chembl IDs of molecules that descend from current molecule.
  childMolecules: [Drug!]!

  # Mechanisms of action to produce intended pharmacological effects. Curated from scientific literature and post-marketing package inserts
  mechanismsOfAction: MechanismsOfAction

  # Investigational and approved indications curated from clinical trial records and post-marketing package inserts
  indications: Indications

  # Curated Clinical trial records and and post-marketing package inserts with a known mechanism of action
  knownDrugs(
    # Query string
    freeTextQuery: String
    size: Int
    cursor: String
  ): KnownDrugs

  # Significant adverse events inferred from FAERS reports
  adverseEvents(page: Pagination): AdverseEvents

  # Therapeutic indications for drug based on clinical trial data or post-marketed drugs, when mechanism of action is known"
  linkedDiseases: LinkedDiseases

  # Molecule targets based on drug mechanism of action
  linkedTargets: LinkedTargets
}

type DrugReferences {
  source: String!
  reference: [String!]!
}

# Evidence & Conclusion Ontology (ECO) annotation
type ECO {
  # ECO term id
  id: String!

  # ECO term label
  label: String!
}

union EntityUnionType = Target | Drug | Disease

# Evidence for a Target-Disease pair
type Evidence {
  # Evidence identifier
  id: String!

  # Evidence score
  score: Float!

  # Target evidence
  target: Target!

  # Disease evidence
  disease: Disease!
  diseaseCellLines: [String!]
  cohortPhenotypes: [String!]
  targetInModel: String
  reactionId: String

  # Variant evidence
  variantId: String

  # Variant dbSNP identifier
  variantRsId: String

  # Confidence interval lower-bound
  confidenceIntervalLower: Float

  # Sample size
  studySampleSize: Long
  variantAminoacidDescriptions: [String!]
  mutatedSamples: [EvidenceVariation!]
  drug: Drug
  cohortShortName: String
  diseaseModelAssociatedModelPhenotypes: [LabelledElement!]
  diseaseModelAssociatedHumanPhenotypes: [LabelledElement!]
  significantDriverMethods: [String!]
  pValueExponent: Long
  log2FoldChangePercentileRank: Long
  biologicalModelAllelicComposition: String
  confidence: String
  clinicalPhase: Long
  resourceScore: Float
  variantFunctionalConsequence: SequenceOntologyTerm
  biologicalModelGeneticBackground: String
  urls: [LabelledUri!]
  literature: [String!]
  studyCases: Long
  studyOverview: String
  allelicRequirements: [String!]
  pathwayName: String
  datasourceId: String!
  datatypeId: String!
  confidenceIntervalUpper: Float
  clinicalStatus: String
  log2FoldChangeValue: Float
  oddsRatio: Float
  cohortDescription: String
  publicationYear: Long
  diseaseFromSource: String
  diseaseFromSourceId: String
  targetFromSourceId: String
  targetModulation: String
  textMiningSentences: [EvidenceTextMiningSentence!]
  studyId: String
  clinicalSignificances: [String!]
  cohortId: String
  pValueMantissa: Long
  pathwayId: String
  publicationFirstAuthor: String
  contrast: String
}

type EvidenceSource {
  datasource: String!
  datatype: String!
}

type EvidenceTextMiningSentence {
  dEnd: Long!
  tEnd: Long!
  dStart: Long!
  tStart: Long!
  section: String!
  text: String!
}

# Sequence Ontology Term
type EvidenceVariation {
  functionalConsequence: SequenceOntologyTerm
  numberMutatedSamples: Long
  numberSamplesTested: Long
  numberSamplesWithMutationType: Long
}

# Evidence for a Target-Disease pair
type Evidences {
  count: Long!
  cursor: String
  rows: [Evidence!]!
}

type ExperimentDetails {
  assayFormatType: String!
  tissue: String
  assayFormat: String!
  assayDescription: String!
  cellShortName: String
}

type ExperimentalToxicity {
  dataSource: String!
  dataSourceReferenceLink: String!
  experimentDetails: ExperimentDetails!
}

type Expression {
  tissue: Tissue!
  rna: RNAExpression!
  protein: ProteinExpression!
}

type GeneOntology {
  id: String!
  project: String!
  term: String!

  # ECO object
  evidence: ECO!
}

type GenomicLocation {
  chromosome: String!
  start: Long!
  end: Long!
  strand: Int!
}

type GenotypePhenotype {
  subjectBackground: String!
  identifier: String!
  label: String!
  pubmedId: String!
  subjectAllelicComposition: String!
}

# Phenotype entity
type HPO {
  # Open Targets hpo id
  id: String!

  # Phenotype name
  name: String!

  # Phenotype description
  description: String

  # namespace
  namespace: [String!]
}

type HallmarkAttribute {
  name: String!
  reference: LiteratureReference!
}

type Hallmarks {
  rows: [CancerHallmark!]!
  attributes: [HallmarkAttribute!]!
  functions: [LiteratureReference!]!
}

type IndicationReference {
  ids: [String!]
  source: String!
}

type IndicationRow {
  maxPhaseForIndication: Long!
  references: [IndicationReference!]

  # Disease
  disease: Disease!
}

type Indications {
  rows: [IndicationRow!]!
  count: Long!
}

type Interaction {
  intA: String!
  targetA: Target
  intB: String!
  targetB: Target
  intABiologicalRole: String!
  intBBiologicalRole: String!
  scoring: Float
  count: Long!
  sourceDatabase: String!
  speciesA: InteractionSpecies
  speciesB: InteractionSpecies

  # List of evidences for this interaction
  evidences: [InteractionEvidence!]!
}

type InteractionEvidence {
  causalInteraction: Boolean!
  evidenceScore: Float
  expansionMethodMiIdentifier: String
  expansionMethodShortName: String
  hostOrganismScientificName: String
  hostOrganismTaxId: Long
  intASource: String!
  intBSource: String!
  interactionDetectionMethodMiIdentifier: String!
  interactionDetectionMethodShortName: String!
  interactionIdentifier: String
  interactionScore: Float
  interactionTypeMiIdentifier: String
  interactionTypeShortName: String
  participantDetectionMethodA: [InteractionEvidencePDM!]
  participantDetectionMethodB: [InteractionEvidencePDM!]
  pubmedId: String
}

type InteractionEvidencePDM {
  miIdentifier: String
  shortName: String
}

type InteractionResources {
  databaseVersion: String!
  sourceDatabase: String!
}

type InteractionSpecies {
  mnemonic: String
  scientificName: String
  taxonId: Long
}

type Interactions {
  count: Long!
  rows: [Interaction!]!
}

# Clinical precedence entry for drugs with investigational or approved indications targeting gene products according to their curated mechanism of action. Entries are grouped by target, disease, drug, phase, status and mechanism of action
type KnownDrug {
  # Drug target approved symbol based on curated mechanism of action
  approvedSymbol: String!
  approvedName: String!

  # Curated disease indication
  label: String!

  # Drug name
  prefName: String!

  # Drug modality
  drugType: String!

  # Drug target Open Targets id based on curated mechanism of action
  targetId: String!

  # Curated disease indication Open Targets id
  diseaseId: String!

  # Open Targets drug id
  drugId: String!

  # Clinical Trial phase
  phase: Int!

  # Mechanism of Action description
  mechanismOfAction: String!

  # Trial status
  status: String

  # Drug target class based on curated mechanism of action
  targetClass: [String!]!

  # Source urls for FDA or package inserts
  references: [KnownDrugReference!]!

  # Clinicaltrials.gov identifiers on entry trials
  ctIds: [String!]!

  # Source urls from clinical trials
  urls: [URL!]!

  # Curated disease indication entity
  disease: Disease

  # Drug target entity based on curated mechanism of action
  target: Target

  # Curated drug entity
  drug: Drug
}

type KnownDrugReference {
  source: String!
  ids: [String!]!
  urls: [String!]!
}

# Set of clinical precedence for drugs with investigational or approved indications targeting gene products according to their curated mechanism of action
type KnownDrugs {
  # Total unique drugs/molecules
  uniqueDrugs: Long!

  # Total unique diseases or phenotypes
  uniqueDiseases: Long!

  # Total unique known mechanism of action targetsTotal unique known mechanism of action targets
  uniqueTargets: Long!

  # Total number of entries
  count: Long!
  cursor: String

  # Clinical precedence entries with known mechanism of action
  rows: [KnownDrug!]!
}

type LabelledElement {
  id: String!
  label: String!
}

type LabelledUri {
  url: String!
  niceName: String!
}

# Linked Disease Entities
type LinkedDiseases {
  count: Int!

  # Disease List
  rows: [Disease!]!
}

# Linked Target Entities
type LinkedTargets {
  count: Int!

  # Target List
  rows: [Target!]!
}

type LiteratureReference {
  pubmedId: Long
  description: String!
}

type MechanismOfActionRow {
  mechanismOfAction: String!
  actionType: String
  targetName: String
  references: [Reference!]

  # Target List
  targets: [Target!]!
}

type MechanismsOfAction {
  rows: [MechanismOfActionRow!]!
  uniqueActionTypes: [String!]!
  uniqueTargetTypes: [String!]!
}

type Meta {
  name: String!
  apiVersion: APIVersion!
  dataVersion: DataVersion!
}

type MouseGene {
  id: String!
  symbol: String!
  phenotypes: [MousePhenotype!]!
}

type MousePhenotype {
  categoryIdentifier: String!
  categoryLabel: String!
  genotypePhenotype: [GenotypePhenotype!]!
}

type NamedAggregation {
  name: String!
  uniques: Long
  rows: [Aggregation!]!
}

type OtarProject {
  otarCode: String!
  status: String!
  projectName: String!
  reference: String!
}

type OtherModalities {
  buckets: [Long!]!
  categories: OtherModalitiesCategories!
}

type OtherModalitiesCategories {
  clinicalPrecedence: Float!
}

input Pagination {
  index: Int!
  size: Int!
}

# Chemical Probe entries (excluding Probeminer)
type PortalProbe {
  # Additional note
  note: String!

  # Chemical probe name
  chemicalprobe: String!

  # Chemical probe target as reported by source
  gene: String!

  # Sources
  sourcelinks: [SourceLink!]!
}

# Various protein coding annotation derived from Uniprot
type ProteinAnnotations {
  # Uniprot reference accession
  id: String!

  # All accessions
  accessions: [String!]!

  # Protein function
  functions: [String!]!

  # Pathway membership
  pathways: [String!]!

  # Protein similarities (families, etc.)
  similarities: [String!]!

  # Subcellular locations
  subcellularLocations: [String!]!

  # Protein subunits
  subunits: [String!]!

  # Chembl target classification
  classes: [ProteinClassPath!]!
}

type ProteinClassPath {
  l1: ProteinClassPathNode
  l2: ProteinClassPathNode
  l3: ProteinClassPathNode
  l4: ProteinClassPathNode
  l5: ProteinClassPathNode
  l6: ProteinClassPathNode
}

type ProteinClassPathNode {
  id: Int!
  label: String!
}

type ProteinExpression {
  reliability: Boolean!
  level: Int!
  cellType: [CellType!]!
}

type Query {
  # Return Open Targets API metadata information
  meta: Meta!

  # Return a Target
  target(
    # Ensembl ID
    ensemblId: String!
  ): Target

  # Return Targets
  targets(
    # List of Ensembl IDs
    ensemblIds: [String!]!
  ): [Target!]!

  # Return a Disease
  disease(
    # EFO ID
    efoId: String!
  ): Disease

  # Return Diseases
  diseases(
    # EFO ID
    efoIds: [String!]!
  ): [Disease!]!

  # Return a drug
  drug(
    # Chembl ID
    chemblId: String!
  ): Drug

  # Return drugs
  drugs(
    # List of Chembl IDs
    chemblIds: [String!]!
  ): [Drug!]!

  # Multi entity search
  search(
    # Query string
    queryString: String!

    # List of entity names to search for (target, disease, drug,...)
    entityNames: [String!]
    page: Pagination
  ): SearchResults!

  # The complete list of all possible datasources
  associationDatasources: [EvidenceSource!]!

  # The complete list of all possible datasources
  interactionResources: [InteractionResources!]!
}

type RNAExpression {
  zscore: Long!
  value: Float!
  unit: String!
  level: Int!
}

type Reactome {
  id: String!
  label: String!

  # If the node is root
  isRoot: Boolean!

  # Reactome Nodes
  children: [Reactome!]!

  # Reactome Nodes
  parents: [Reactome!]!

  # Reactome Nodes
  ancestors: [Reactome!]!
}

type Reference {
  ids: [String!]
  source: String!
  urls: [String!]
}

# Related Disease Entity
type RelatedDisease {
  id: String!
  countA: Long!
  countB: Long!
  countAOrB: Long!
  countAAndB: Long!
  score: Float!

  # Disease
  B: Disease!
}

# Related Diseases
type RelatedDiseases {
  maxCountAOrB: Long!
  count: Long!

  # Related Diseases
  rows: [RelatedDisease!]!
}

# Related Target Entity
type RelatedTarget {
  id: String!
  countA: Long!
  countB: Long!
  countAOrB: Long!
  countAAndB: Long!
  score: Float!

  # Target
  B: Target!
}

# Related Targets Entity
type RelatedTargets {
  maxCountAOrB: Long!
  count: Long!

  # Related Targets
  rows: [RelatedTarget!]!
}

type Safety {
  adverseEffects: [AdverseEffects!]!
  safetyRiskInfo: [SafetyRiskInfo!]!
  experimentalToxicity: [ExperimentalToxicity!]!
}

type SafetyCode {
  code: String
  mappedTerm: String
  termInPaper: String
}

type SafetyReference {
  pubmedId: Long
  refLabel: String
  refLink: String
}

type SafetyRiskInfo {
  organsSystemsAffected: [SafetyCode!]!
  references: [SafetyReference!]!
  safetyLiability: String!
}

type ScoredComponent {
  id: String!
  score: Float!
}

type SearchResult {
  id: String!
  entity: String!
  category: [String!]!
  name: String!
  description: String
  keywords: [String!]
  multiplier: Float!
  prefixes: [String!]
  ngrams: [String!]
  score: Float!
  highlights: [String!]!

  # Associations for a fixed target
  object: EntityUnionType
}

type SearchResultAggCategory {
  name: String!
  total: Long!
}

type SearchResultAggEntity {
  name: String!
  total: Long!
  categories: [SearchResultAggCategory!]!
}

type SearchResultAggs {
  total: Long!
  entities: [SearchResultAggEntity!]!
}

# Search results
type SearchResults {
  # Aggregations
  aggregations: SearchResultAggs

  # Return combined
  hits: [SearchResult!]!

  # Total number or results given a entity filter
  total: Long!
}

# Sequence Ontology Term
type SequenceOntologyTerm {
  # Sequence Ontology ID
  id: String!

  # Sequence Ontology Label
  label: String!
}

# "Datasource link"
type SourceLink {
  # Source name
  source: String!

  # Source full url
  link: String!
}

# Target entity
type Target {
  # Open Targets target id
  id: String!

  # HGNC approved symbol
  approvedSymbol: String!

  # Approved gene name
  approvedName: String!

  # Molecule biotype
  bioType: String!

  # HGNC approved id
  hgncId: String

  # Gene name synonyms
  nameSynonyms: [String!]!

  # Symbol synonyms
  symbolSynonyms: [String!]!

  # Chromosomic location
  genomicLocation: GenomicLocation!

  # Various protein coding annotation
  proteinAnnotations: ProteinAnnotations

  # Gene Ontology annotations
  geneOntology: [GeneOntology!]!

  # Known target safety effects and target safety risk information
  safety: Safety

  # Potent, selective and cell-permeable chemical probes
  chemicalProbes: ChemicalProbes

  # Target-modulated essential alterations in cell physiology that dictate malignant growth
  hallmarks: Hallmarks

  # Target Enabling Package (TEP)
  tep: Tep

  # Target druggability assessment
  tractability: Tractability
  reactome: [Reactome!]!

  # The complete list of all possible datasources
  evidences(
    # EFO ID
    efoIds: [String!]!

    # List of datasource ids
    datasourceIds: [String!]
    size: Int
    cursor: String
  ): Evidences!

  # Biological pathway membership from Reactome
  interactions(
    # Database name
    sourceDatabase: String
    page: Pagination
  ): Interactions

  # Biological pathway membership from Reactome
  mousePhenotypes: [MouseGene!]!

  # RNA and Protein baseline expression
  expressions: [Expression!]!

  # Clinical precedence for drugs with investigational or approved indications targeting gene products according to their curated mechanism of action
  knownDrugs(
    # Query string
    freeTextQuery: String
    size: Int
    cursor: String
  ): KnownDrugs

  # Clinical relevance and drug responses of tumor genomic alterations on the target
  cancerBiomarkers(page: Pagination): CancerBiomarkers

  # Similar targets based on their disease association profiles
  relatedTargets(page: Pagination): RelatedTargets

  # associations on the fly
  associatedDiseases(
    Bs: [String!]

    # Use disease ontology to capture evidences from all descendants to build associations
    enableIndirect: Boolean
    datasources: [DatasourceSettingsInput!]
    aggregationFilters: [AggregationFilter!]
    BFilter: String
    orderByScore: String
    page: Pagination
  ): AssociatedDiseases!
}

# Target Enabling Package (TEP)
type Tep {
  uri: String!
  name: String!
}

# Tissue, organ and anatomical system
type Tissue {
  # UBERON id
  id: String!

  # UBERON tissue label
  label: String!

  # Anatomical systems membership
  anatomicalSystems: [String!]!

  # Organs membership
  organs: [String!]!
}

type Tractability {
  smallmolecule: TractabilitySmallMolecule
  antibody: TractabilityAntibody
  otherModalities: OtherModalities
}

type TractabilityAntibody {
  topCategory: String!
  buckets: [Long!]!
  categories: TractabilityAntibodyCategories!
}

type TractabilityAntibodyCategories {
  predictedTractableMedLowConfidence: Float!
  clinicalPrecedence: Float!
  predictedTractableHighConfidence: Float!
}

type TractabilitySmallMolecule {
  topCategory: String!
  smallMoleculeGenomeMember: Boolean!
  buckets: [Long!]!
  highQualityCompounds: Long!
  categories: TractabilitySmallMoleculeCategories!
}

type TractabilitySmallMoleculeCategories {
  clinicalPrecedence: Float!
  predictedTractable: Float!
  discoveryPrecedence: Float!
}

# Source URL for clinical trials, FDA and package inserts
type URL {
  # resource url
  url: String!

  # resource name
  name: String!
}

# Withdrawal reason
type WithdrawnNotice {
  # Withdrawal classes
  classes: [String!]

  # Withdrawal countries
  countries: [String!]

  # Reason for withdrawal
  reasons: [String!]

  # Year of withdrawal
  year: Int
}

# The `Long` scalar type represents non-fractional signed whole numeric values. Long can represent values between -(2^63) and 2^63 - 1.
scalar Long
```

