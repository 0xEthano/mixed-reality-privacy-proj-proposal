# Dataset discovery catalog

Catalog reviewed 2026-10-06. These are candidates, not acquired or fully validated datasets. Download availability does not establish redistribution permission.

| Candidate | Coverage and intended use | Access status / next check | Limitation |
| --- | --- | --- | --- |
| [Liebers et al., 2021 dataset](https://hci.informatik.uni-due.de/publikationen/understanding-user-identification-in-virtual-reality-through-behavioral-biometrics-and-the-effect-of-body-normalization) | VR behavioral tracking; initial pose identification and normalization candidate | Author institution lists split-archive downloads; inspect schema, terms, and trial/session metadata | Gaze and joint coverage must be checked; do not assume cross-session support |
| [OpenNEEDS, 2021](https://doi.org/10.1145/3448018.3457996) | Candidate for gaze, head, hand, and scene signals in VR | Resolve current author-hosted download and license in week 1; download not validated | Publisher page was inaccessible during review; confirm participant IDs and usable labels before selection |
| [SCUT-DHGA](https://github.com/SCUT-BIP-Lab/SCUT-DHGA) | Dynamic hand gesture authentication; gesture behavior/privacy fallback | Official repository requires a signed release agreement for full data; access not requested | RGB/depth video rather than headset-native joints; feature extraction may exceed scope; noncommercial research restriction |
| [BehaVR](https://arxiv.org/abs/2308.07304) | Framework and literature for identification from multiple VR sensor groups | Paper verified; data access and permitted use remain unconfirmed | Literature source until usable data access is established |
| [MURMR](https://arxiv.org/abs/2507.11797v3) | MR group behavior methods; optional structural/temporal analysis | 2026 revision verified; public dataset release not confirmed | Requires synchronized group data; not a core acquisition dependency |
| [Miller et al., 2020](https://doi.org/10.1038/s41598-020-74486-y) | Identification during 360-degree VR viewing; pose literature and potential fallback | Check article data-availability statement and current source permissions | Observational VR setting differs from interactive MR |

## Selection gate: end of week 2
Prefer headset-native streams, usable participant IDs, distinct trials or sessions, explicit terms, and manageable preprocessing. Select one primary dataset and one complementary dataset only if needed for modality/behavior coverage. If access is blocked, prioritize an accessible pose study and labeled gesture task, while documenting unfilled gaze coverage.

For each selected source, record URL, paper citation, access conditions, version, hashes, file size, modality list, units, coordinates, sample rate, participant/session/trial counts, labels, exclusions, and permitted outputs. Inspect actual files before asserting any schema property.

Do not combine unrelated participants or align independent datasets as if they were simultaneous multimodal recordings. Catalog completion covers discovery; analysis coverage depends on approved usable data.
