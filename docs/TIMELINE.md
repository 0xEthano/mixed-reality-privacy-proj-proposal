# Eight-week project timeline

Weeks are relative to the team-approved start date; no calendar dates are assumed. Owners coordinate work with the other members.

| Week | Work | Milestone / output | Lead |
| --- | --- | --- | --- |
| 1 | Review literature; catalog pose, gaze, and gesture candidates; plan environment | Literature matrix, access checklist, workstation plan | Avaneesh; Project Owner |
| 2 | Inspect accessible samples, terms, IDs, and labels; choose scope and split policy | Dataset selection gate; final experiment plan; access barriers recorded | Avaneesh; Jeff |
| 3 | Validate and preprocess; audit missingness and units; construct split manifests | Data quality summary and reproducible preprocessing | Jeff |
| 4 | Extract features; implement identification baselines | Validation results and leakage review | Jeff; Avaneesh |
| 5 | Analyze supported behavior; compare sensor subsets | Behavior baseline or documented exploratory analysis | Avaneesh |
| 6 | Evaluate normalization and other privacy transformations; run sensitivity checks | Privacy–utility comparison; optional Unity replay only if time permits | Avaneesh; Jeff |
| 7 | Freeze configurations; run held-out tests; quantify uncertainty; draft report | Aggregate metrics, figures, limitations, report draft | All; Project Owner integrates |
| 8 | Review reproducibility and evidence; finalize report and presentation | Final project package and contribution statement | Project Owner; all review |

## Scope controls
If full dataset access is unresolved by week 2, use an accessible alternative and record missing modalities. If group metadata is unavailable, omit dyadic/group analysis. If compute becomes limiting, keep classical models and reduce experiment combinations using validation results. Drop optional Unity replay before compromising evaluation or writing.

## Future deliverable checklist
- [ ] Catalog and terms review complete
- [ ] Data validation and split manifests complete
- [ ] Identification evaluation and uncertainty reported
- [ ] Behavior analysis validated or clearly marked exploratory
- [ ] Privacy–utility comparison complete
- [ ] Reproduction instructions and dependency versions recorded
- [ ] Report, presentation, and member contributions reviewed
