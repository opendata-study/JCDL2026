# Category Definitions (extends Table 1 of the paper)

| Code | Category | Operational Definition |
|---|---|---|
| F | Fully Public Repository Deposition | Evidentiary data deposited in a public repository with a DOI or accession number. |
| M | Mixed Public Repository + Author Request | Some data deposited in a public repository (DOI/accession) while additional data are available upon request. |
| P | Public Within Article/Supplement Only | Data available only within the article, supplementary materials, or non-archival repositories without persistent identifiers (includes GitHub alone). |
| R | Reuse of Public Third-Party Data Only | Study exclusively reuses previously published public datasets; no new evidentiary data generated. |
| C | Controlled-Access Repository | Access requires application, approval, or other restrictions. |
| A | Author Upon Request Only | Data available solely upon reasonable request from the authors; not deposited in a public repository. |
| N | No Data Generated/Not Applicable | No new evidentiary data were generated, or data availability was explicitly stated to be not applicable. |

See `prompts/category_prompt.md` for the full classification prompt, including edge-case
handling (GitHub, Data Journals, evidentiary-data scope) and the priority rule used when
a statement could satisfy more than one category (F > M > P > R > C > A > N).
