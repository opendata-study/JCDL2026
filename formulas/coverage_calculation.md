# Dataset Coverage Calculation (Section 2.2)

For each journal–year combination:

- N_PMC = total number of PMC articles
- N_DAS = number containing a Data Availability Statement (DAS)
- N_WoS = number of DAS articles in the analytical dataset, i.e. matched to Web of Science
  via DOI AND assigned a DAS category

Proportions (sum to 100%):

- Included Articles = N_WoS / N_PMC
- Excluded DAS Articles = (N_DAS − N_WoS) / N_PMC
- Articles Without DAS = (N_PMC − N_DAS) / N_PMC

"Excluded DAS Articles" comprises DAS-containing articles with no Web of Science record and
Web of Science–matched articles without an assigned DAS category (mainly reviews and other
non-research article types).

These proportions were used to assess temporal changes in DAS adoption and the
representativeness of the Web of Science–matched analytical dataset across journals
and publication years.

Note on counting: N_DAS and N_WoS count unique PMCIDs. For the ten analysed journals,
N_DAS = 701,063 DAS-containing articles, of which 661,365 have an assigned DAS category and
39,698 do not. N_WoS = 653,356 articles have an assigned DAS category and a Web of Science
record (classified articles without a Web of Science record: 8,009). Hence Excluded DAS Articles
= 701,063 − 653,356 = 47,707 (39,698 without an assigned DAS category + 8,009 classified
articles without a Web of Science record). The analytical dataset has 653,490 records because
134 of these PMCIDs matched two Web of Science records each (see `labels/DAS_labels.csv`).
