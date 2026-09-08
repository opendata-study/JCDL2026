# Classification Prompt

Used with DeepSeek-V3.2, GPT-5.4, and Mistral-Large-3 (zero-shot, no fine-tuning),
accessed via the University of Tokyo Azure environment.

Classify the Data Availability statement into ONE category.

DATA DEFINITION:
"Data" refers strictly to evidentiary data supporting the study's scientific claims.
Exclude administrative documents, study protocols, ethics approvals, trial registrations,
slides, videos, project plans, or similar materials unless they contain evidentiary data.

PUBLIC REPOSITORY DEFINITION:
A public repository is an openly accessible data archive providing persistent identifiers
(e.g., accession numbers or DOIs). Examples include (but are not limited to): GenBank (NCBI),
GEO, SRA, ArrayExpress, Dryad, Figshare, Zenodo, OSF, PDB, PRIDE, ENA, institutional
repositories with open public access.

- NOTE 1: GitHub is treated as a repository named in the article, but because it does not
  provide persistent identifiers by default, GitHub alone should be classified as category P.
- NOTE 2: If GitHub data are archived in a DOI-enabled repository (e.g., Zenodo), classify
  according to that repository (typically F).
- NOTE 3: Data Journals are considered public repositories with DOI. Data deposited in
  these journals should be classified as F. Examples: Scientific Data, Data in Brief,
  GigaScience, Biodiversity Data Journal, F1000Research (Data Articles), Data (MDPI),
  Earth System Science Data, Open Health Data, Genomics Data, Journal of Open Archaeology
  Data, Open Research Europe (Data Articles), Data Science Journal, Ecological Archives,
  Geoscience Data Journal, Journal of Open Humanities Data, Big Earth Data, BMC Genomic
  Data, Data Intelligence.
  Judgment criteria: (1) data published as a DOI-enabled dataset or Data Article;
  (2) the journal ensures public access and long-term archival; (3) if met, classify as F
  even if some data are also available elsewhere.

CATEGORIES (non-ordinal labels):

F = Fully Public Repository Deposition
  - Evidentiary data deposited in a public repository with DOI or accession number
  - If accession or DOI is present, classify as F even if not all data are explicitly described
  - Includes DOI-enabled Data Journals

M = Mixed Public Repository + Author Request
  - Some evidentiary data publicly deposited (repository named with DOI/accession)
  - AND additional evidentiary data explicitly available upon request

P = Public Within Article / Supplement Only
  - Data available only within the article or supplementary files
  - OR repository named but no accession number or DOI provided
  - Includes GitHub alone

R = Reuse of Public Third-Party Data Only
  - Study exclusively reuses previously published public datasets
  - No new evidentiary data generated

C = Controlled-Access Repository
  - Data require application, approval, or restricted access

A = Author Upon Request Only
  - Evidentiary data available only upon request
  - No public repository deposition

N = No Data Generated / Not Applicable
  - Explicitly states no new evidentiary data were generated
  - Or data availability not applicable

PRIORITY RULE:
If multiple categories appear applicable, choose the most open category according to:
F > M > P > R > C > A > N

Return ONLY one uppercase letter from this set: F, M, P, R, C, A, N
Do not explain. Do not add anything else. Do not output JSON.
Return strictly one character.
If you output anything other than this format, the answer is invalid.
Do not repeat definitions. Do not output explanation. Do not output anything else.
