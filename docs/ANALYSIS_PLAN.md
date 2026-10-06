# Analysis plan and system requirements

## Research questions
1. Can pose, gaze, or gesture features identify users without explicit identifiers?
2. How does risk change across sensor groups, tasks, sessions, and body normalization?
3. Which observed behaviors are recoverable, and how do privacy transformations affect that utility?

## Threat model
An offline analyst receives sensor traces and labeled enrollment examples for a known participant cohort. Direct identifiers are removed from model inputs. The primary task is closed-set identification among those enrolled users. This does not measure identity discovery in the general population. Cross-task or cross-session tests are included only when the dataset supports them. No attempt will be made to link participants to real identities.

## System blocks and requirements
| Block | Input | Output / requirement |
| --- | --- | --- |
| Discovery | Papers and official data sources | Access decision, modality coverage, provenance, terms |
| Ingestion | Authorized files | Local immutable raw copy, file hashes, schema audit |
| Split construction | Participant, session, trial metadata | Versioned non-overlapping train/validation/test manifest |
| Preprocessing | Training partition and raw traces | Validated time series and train-fitted transforms |
| Feature extraction | Validated windows | Pose, motion, gaze, or gesture features with units |
| Modeling | Training features | Identification baseline and behavior model or clusters |
| Evaluation | Frozen models and test partition | Metrics, uncertainty, ablations, failure cases |
| Reporting | Aggregate outputs | Figures, methods, limitations, literature comparison |

## Preprocessing
Record dataset version, retrieval date, license, participant counts, sensor units, coordinate conventions, sample rates, and missingness. Use a common schema with dataset ID, pseudonymous participant ID, session ID, trial ID, timestamp, modality, signal values, validity, and optional behavior label. Preserve IDs as metadata, excluding them from feature inputs.

Audit time ordering, duplicated records, invalid gaze, quaternion norms, missing joints, and impossible values. Select a documented target sample rate per dataset. Use suitable interpolation for positions and rotations, with a maximum gap limit; do not bridge trials or long dropouts. Record excluded samples. Compare raw coordinates against head-relative and body-normalized variants where meaningful. Treat normalization as an experimental condition, not a guaranteed privacy defense.

Partition entire trials or sessions before windowing. Use separate sessions for enrolled users when available; otherwise use held-out whole trials and describe the weaker generalization claim. Every evaluated identity needs training examples. Fit scalers, imputation statistics, feature selection, and model tuning on training/validation data only. Overlapping windows must remain within one partition.

## Privacy analysis
Start with majority-class and stratified-random baselines, then logistic regression and random forests. Candidate features include position/orientation summaries, velocity, angular velocity, hand separation, gaze direction variability, and joint dynamics. Use only available signals and compare modality subsets. Tune on validation data; evaluate the final configuration once on held-out test data.

Report top-1 accuracy, macro-F1, balanced accuracy, confusion matrices, cohort size, per-user sample balance, and session/trial protocol. Estimate 95% confidence intervals using participant-level resampling, retaining each participant's test trials together. Save seeds and split manifests. Avoid treating correlated windows as independent evidence.

## Behavior analysis
With reliable labels, classify gesture or task categories using participant-disjoint splits so utility reflects unseen users. Report macro-F1 and confusion matrices. Without labels, analyze motion intensity, gaze dispersion, or cluster stability as exploratory patterns; do not assign cognitive or social meanings without supporting evidence. MURMR-inspired dyadic analysis requires synchronized group membership, shared coordinate frames, and interpersonal signals. It is an optional extension and will be omitted when those requirements are unmet.

## Privacy–utility comparison
Compare unmodified signals against downsampling, spatial quantization, noise, and coordinate/body normalization. Specify rates, bin widths, noise units, and seeds; select settings on validation data. Measure identification risk and behavior utility separately under their respective split protocols. Lower identification accuracy alone does not prove anonymity or formal privacy. Do not claim differential privacy without an explicit mechanism and accounting.

## Hardware and software requirements
- Core workstation: CPU; planned 16 GB RAM, 20 GB initial free disk, expandable after catalog review.
- Python: NumPy/pandas for tables, SciPy for signal processing, scikit-learn for baselines, Matplotlib for plots, Jupyter for inspection; lock versions when implementation starts.
- Git/GitHub: proposal, future code, configurations, and aggregate outputs.
- Unity: optional offline pose/gaze replay; no live headset, network transport, or XR SDK required for the core study.
- Optional GPU only if a later temporal model is justified by dataset size and remaining time.

## Data handling and reproducibility
Keep raw traces, participant mappings, derived per-user features, and trained biometric models out of the public repository unless explicit terms permit release and review supports it. Publish approved aggregate results and reproducible methods. Record hashes, dependencies, commands, seeds, split policy, and exclusion decisions. This proposal acquires no data and contacts no dataset authors.

## Acceptance and limitations
Core completion requires one usable privacy experiment and one behavior analysis, plus a catalog covering all three requested modalities. If a modality cannot be obtained, document the search and access barrier rather than imply coverage. Different datasets are analyzed separately; participants must not be assumed to correspond across sources. VR results, small cohorts, task-specific motion, unavailable labels, and single-session data constrain conclusions about MR.
