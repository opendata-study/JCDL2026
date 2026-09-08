# Dataset Coverage Calculation (Section 2.2)

For each journal–year combination:

- N_PMC = total number of PMC articles
- N_DAS = number containing a Data Availability Statement (DAS)
- N_WoS = number of DAS articles successfully matched to Web of Science via DOI

Proportions (sum to 100%):

- Included Articles = N_WoS / N_PMC
- Unmatched DAS Articles = (N_DAS − N_WoS) / N_PMC
- Articles Without DAS = (N_PMC − N_DAS) / N_PMC

These proportions were used to assess temporal changes in DAS adoption and the
representativeness of the Web of Science–matched analytical dataset across journals
and publication years.
