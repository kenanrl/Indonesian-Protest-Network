# Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![Platform: X (Twitter)](https://img.shields.io/badge/Platform-X%20(Twitter)-black)](https://x.com)
[![Period: Aug–Sep 2025](https://img.shields.io/badge/Period-August–September%202025-blue)]()

---

## About This Repository

This repository contains the anonymized dataset and Python analytical notebooks used in the research manuscript:

> **"Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks"**

The repository is shared to support transparency and reproducibility in line with the journal's data availability policy. The analytical pipeline combines network analysis (Louvain community detection and cascade reachability), BERTopic thematic modeling, and two proposed composite metrics, the Excitation Index and the Cognitive Fusion Index (CFI), to examine how protest narratives diffused across structurally fragmented communities on platform X during the Indonesian civic unrest of August to September 2025.

---

## Data Availability Statement

The data supporting the findings of this study were collected from platform X (formerly Twitter) using keyword-based queries targeting protest-related hashtags and terms. The raw dataset cannot be shared in its original form because of platform Terms of Service restrictions.

The dataset provided here has been processed to comply with platform policies and to protect user privacy. All account identifiers have been irreversibly anonymized through one-way hashing prior to publication, so original usernames are not recoverable. Tweet text is retained in the shared files because it is required to reproduce the thematic modeling. Users of this data remain responsible for complying with X's Terms of Service.

---

## Repository Structure

```
Indonesian-Protest-Network/
│
├── main-data/
│   └── Book62-hashed.csv                                       ← Anonymized raw tweet dataset
│
├── analytical-notebook/
│   │  # Core sequential pipeline (Stages 1 to 11)
│   ├── BERTopic Setup.ipynb                                    ← Topic modeling on protest tweets
│   ├── BERTopic Linking Diffusion Depth to Topic Change.ipynb  ← Composite diffusion score per topic
│   ├── Network Graph Construction.ipynb                        ← Directed interaction network construction
│   ├── Community Detection.ipynb                               ← Louvain community detection
│   ├── Social Penetration Metrics.ipynb                        ← Cross-community penetration metrics
│   ├── Excitation Effect Narrative Shift Trigger Steps 1 and 2.ipynb
│   ├── Excitation Effect Narrative Shift Trigger Steps 3 and 4.ipynb
│   ├── Actor Role Analysis.ipynb                               ← Actor role classification
│   ├── Cross-Community Penetration Cognitive Fusion.ipynb      ← Community porosity and CFI
│   ├── Fix Analysis Novelty3 Engagement per Narrative 3.ipynb  ← Engagement comparison per narrative
│   ├── Fix Figure Engagement vs Structural Reach Final.ipynb   ← Figure 4: engagement vs structural reach
│   │
│   │  # Robustness and reviewer-requested analyses
│   ├── Louvain Seed Stability Audit.ipynb                      ← 50-seed Louvain stability, 20-seed porosity recheck
│   ├── Account Classification Intercoder Reliability.ipynb     ← Cohen's kappa and AI vs human agreement
│   ├── Classification Accuracy CI.ipynb                        ← Wilson and Clopper-Pearson CI for AI accuracy
│   ├── Simplified Community-Level Network (Figure S2).ipynb    ← Meta-network of largest communities
│   ├── Dyadic Dependence Robustness.ipynb                      ← Cross-community shift on unique dyads
│   ├── Duration and Volume Control.ipynb                       ← Day-level cross-community ratio test
│   ├── Paired Community Selection-Bias Assessment.ipynb        ← 38 selected vs 75 excluded communities
│   └── Engagement Effect Sizes and CIs.ipynb                   ← Rank-biserial effect sizes with 95% CI
│
├── derived-data/
│   ├── cognitive fusion index.csv
│   ├── community porosity.csv
│   ├── descriptive engagement per narrative.csv
│   ├── excitation index.csv
│   ├── excitation integrated table.csv
│   ├── kruskal wallis engagement.csv
│   ├── meta network per narrative.csv
│   ├── pairwise mannwhitney engagement.csv
│   ├── penetration by narrative.csv
│   ├── penetration by topic.csv
│   │
│   └── hashed/
│       ├── Data bert with topics hashed.csv
│       ├── Data diffusion analysis hashed.csv
│       ├── Data with community hashed.csv
│       ├── actor engagement structural merged hashed.csv
│       ├── actor roles classification hashed.csv
│       ├── affan community propagation fixed hashed.csv
│       ├── cascade hop levels hashed.csv
│       ├── community summary hashed.csv
│       ├── network edges hashed.csv
│       ├── network nodes hashed.xlsx
│       └── network nodes with community hashed.csv
│
├── CITATION.cff
├── LICENSE
└── README.md
```

---

## Dataset Description

**Collection period:** August 1 to September 29, 2025
**Platform:** X (formerly Twitter)
**Language:** Bahasa Indonesia

### Raw Data

| File | Description |
| --- | --- |
| `main-data/Book62-hashed.csv` | Anonymized tweet dataset: 29,289 tweets from 19,621 unique authoring accounts |

#### Column Dictionary — Raw Data

| Column | Description |
| --- | --- |
| `username` | Anonymized account identifier (irreversibly hashed, original usernames not recoverable) |
| `full_text` | Full text content of the tweet |

### Derived Data

Files in `derived-data/` contain aggregate-level outputs with no account identifiers. Files in `derived-data/hashed/` contain account-level outputs where usernames are present in hashed form only.

> **Note on anonymization:** Usernames in all files within `derived-data/hashed/` have been anonymized with a one-way hashing method prior to publication, in compliance with X's Terms of Service and to protect user privacy.

---

## Analytical Framework and Pipeline

The notebooks in `analytical-notebook/` fall into two groups. The core pipeline (Stages 1 to 11) implements the sequential analysis described in Section 3 of the manuscript. The robustness notebooks implement the additional sensitivity and reliability analyses requested during peer review.

### Core pipeline

**Stage 1 — Thematic Modeling via BERTopic** (`BERTopic Setup.ipynb`)
Identifies thematic structure with BERTopic using Indonesian sentence-BERT embeddings (`firqaaa/indo-sentence-bert-base`), UMAP dimensionality reduction, and HDBSCAN clustering. Produces 19 topics with an outlier rate of about 23 percent, and defines the pre-shift (August 1 to 26) and post-shift (August 28 to September 29) windows.

**Stage 2 — Diffusion Score per Topic** (`BERTopic Linking Diffusion Depth to Topic Change.ipynb`)
Computes a composite diffusion score per narrative topic, used as input to the Excitation Index.

**Stage 3 — Network Graph Construction** (`Network Graph Construction.ipynb`)
Constructs a directed weighted graph where nodes are accounts and edges represent replies, quote tweets, and mentions directed from the referring account to the account referred to. Retweets are not used as edges because only an aggregate retweet count is recorded. Output: 11,426 nodes and 13,994 unique weighted directed edges.

**Stage 4 — Community Detection** (`Community Detection.ipynb`)
Applies the Louvain algorithm on the undirected weighted projection (resolution 1.0, seed 42). Output: 1,667 communities, modularity 0.7991.

**Stage 5 — Social Penetration Metrics** (`Social Penetration Metrics.ipynb`)
Computes cross-community penetration metrics including community porosity, hop distance, and inter-community edge ratios across the pre- and post-shift windows.

**Stage 6 — Excitation Effect and Narrative Shift Trigger, Steps 1 and 2** (`Excitation Effect Narrative Shift Trigger Steps 1 and 2.ipynb`)
Reconstructs cascade sequences from timestamped interaction events matched to BERTopic topics, and runs the chi-square test for the cross-community ratio shift (pre-shift 13.5 percent vs post-shift 16.7 percent).

**Stage 7 — Excitation Effect and Narrative Shift Trigger, Steps 3 and 4** (`Excitation Effect Narrative Shift Trigger Steps 3 and 4.ipynb`)
Computes the Excitation Index as the unweighted mean of four z-scored indicators: mean diffusion score, maximum hop depth, mean hop depth, and post-shift median engagement per tweet.

**Stage 8 — Actor Role Analysis** (`Actor Role Analysis.ipynb`)
Classifies each account as Attention Sink, Local Amplifier, or Diffusion Driver using the 75th-percentile degree rule and cross-community edge count. Includes the chi-square test for the association between account type and structural role (χ² = 275.41, df = 4, p < 0.001).

**Stage 9 — Cross-Community Penetration and Cognitive Fusion** (`Cross-Community Penetration Cognitive Fusion.ipynb`)
Computes paired community porosity and the Cognitive Fusion Index as the unweighted mean of four z-scored structural indicators. Includes the Wilcoxon signed-rank test (n = 38, W = 178, p = 0.025) and the CFI sensitivity analysis under four weighting schemes.

**Stage 10 — Engagement Comparison per Narrative** (`Fix Analysis Novelty3 Engagement per Narrative 3.ipynb`)
Kruskal-Wallis and pairwise Mann-Whitney U tests on view count across the seven narratives (Bonferroni-corrected α = 0.000476). Produces the engagement statistics in Table S1 and Section 4.2.

**Stage 11 — Figure 4, Engagement vs Structural Reach** (`Fix Figure Engagement vs Structural Reach Final.ipynb`)
Produces Figure 4 and the Spearman correlation between cumulative view count and cross-community edges (ρ = 0.232, p = 8.73 × 10⁻⁷⁹, n = 6,365). Uses the post-relabeling corrected account classification.

### Robustness and reviewer-requested analyses

**Louvain Seed Stability Audit** (`Louvain Seed Stability Audit.ipynb`)
Reruns Louvain under 50 random seeds against the seed-42 partition (modularity 0.797, SD 0.002, community count 1,661 to 1,687, NMI 0.935, ARI 0.726), and rechecks the paired porosity result against 20 alternative seed partitions.

**Account Classification Intercoder Reliability** (`Account Classification Intercoder Reliability.ipynb`)
Reports Cohen's kappa between two coders (0.890) and AI versus human consensus agreement (91.9 percent). Provided as a record of the reliability assessment. Raw coder sheets are not published because they contain account identifiers.

**Classification Accuracy CI** (`Classification Accuracy CI.ipynb`)
Wilson and Clopper-Pearson 95 percent confidence intervals for the AI classification accuracy (374 of 407, Wilson [88.8, 94.2]).

**Simplified Community-Level Network, Figure S2** (`Simplified Community-Level Network (Figure S2).ipynb`)
Builds the simplified meta-network of the largest communities, colored by dominant narrative, shown as Figure S2 in the Supplementary Material.

**Dyadic Dependence Robustness** (`Dyadic Dependence Robustness.ipynb`)
Recomputes the cross-community shift on unique directed dyads (14.5 to 17.3 percent, χ² = 21.17, p = 4.2 × 10⁻⁶), with Fisher's exact test and a dyad-level permutation test.

**Duration and Volume Control** (`Duration and Volume Control.ipynb`)
Day-level test of the cross-community ratio (Mann-Whitney rank-biserial r = 0.552, p = 0.0002), showing the shift is not an artifact of higher post-shift volume.

**Paired Community Selection-Bias Assessment** (`Paired Community Selection-Bias Assessment.ipynb`)
Compares the 38 paired communities against the 75 excluded communities on size and pre-shift porosity.

**Engagement Effect Sizes and CIs** (`Engagement Effect Sizes and CIs.ipynb`)
Rank-biserial effect sizes with 95 percent bootstrap confidence intervals (B = 10,000, seed 42) for the pairwise engagement comparisons.

---

## Replication Instructions

All notebooks are designed to run in [Google Colab](https://colab.research.google.com/) with a standard GPU runtime (T4).

1. Clone or download this repository.
2. Upload the target notebook to Google Colab.
3. When prompted, upload the input files from `main-data/` or `derived-data/` named at the top of each notebook.
4. Run cells in order. Core pipeline stages depend on outputs from earlier stages, so run Stages 1 to 11 in sequence. The robustness notebooks read outputs of the core pipeline.

The intercoder reliability notebooks read coder sheets that are not published because they contain account identifiers. They are provided with their outputs as a record of the reported reliability statistics.

**Key dependencies:**

| Library | Version |
| --- | --- |
| NetworkX | 3.6.1 |
| SciPy | 1.16.3 |
| BERTopic | latest stable |
| HDBSCAN | latest stable |
| UMAP-learn | latest stable |
| pandas | latest stable |
| matplotlib | latest stable |
| scikit-learn | latest stable |
| statsmodels | latest stable |

---

## License

The dataset and code in this repository are shared under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).

You are free to share and adapt the material for any purpose, provided appropriate credit is given.

> **Note:** This dataset is derived from X (formerly Twitter). Users of this data are responsible for complying with [X's Terms of Service](https://x.com/en/tos) and applicable data protection regulations.

---

## Contact

For questions about the dataset or analytical notebooks, please open a [GitHub Issue](../../issues) or contact the corresponding author as listed in the manuscript.

---

## Acknowledgements

Data collection used keyword-based retrospective queries from platform X in accordance with platform policies at the time of collection. The authors acknowledge that platform Terms of Service restrict the redistribution of raw tweet content, and all shared data has been anonymized accordingly.
