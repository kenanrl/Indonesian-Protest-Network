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

The dataset provided here has been processed to comply with platform policies and to protect user privacy. All account identifiers have been **irreversibly anonymized through one-way hashing** prior to publication, so original usernames are not recoverable. Tweet text is retained in the shared files because it is required to reproduce the thematic modeling. Users of this data remain responsible for complying with X's Terms of Service.

---

## Repository Structure

```
Indonesian-Protest-Network/
│
├── main-data/
│   └── Book62-hashed.csv                                                        ← Anonymized raw tweet dataset
│
├── analytical-notebook/
│   │  # Core sequential pipeline (Stages 1 to 11)
│   ├── BERTopic Setup.ipynb                                                     ← Topic modeling on protest tweets
│   ├── BERTopic Linking Diffusion Depth to Topic Change.ipynb                   ← Composite diffusion score per topic
│   ├── Network Graph Construction.ipynb                                         ← Directed interaction network construction
│   ├── Community Detection.ipynb                                                ← Louvain community detection
│   ├── Social Penetration Metrics.ipynb                                         ← Cross-community penetration metrics
│   ├── Excitation Effect Narrative Shift Trigger Steps 1 and 2.ipynb            ← Temporal excitation & engagement velocity
│   ├── Excitation Effect Narrative Shift Trigger Steps 3 and 4.ipynb            ← Statistical integration & Excitation Index
│   ├── Actor Role Analysis.ipynb                                                ← Actor role classification (sink vs driver)
│   ├── Cross-Community Penetration Cognitive Fusion.ipynb                       ← Community porosity & CFI computation
│   ├── Fix Analysis Novelty3 Engagement per Narrative 3.ipynb                   ← Supplementary engagement comparison per narrative
│   ├── Fix Figure Engagement vs Structural Reach Final.ipynb                    ← Figure 4: engagement vs structural reach (post-relabeling)
│   │
│   │  # Robustness and reviewer-requested analyses
│   ├── Louvain Seed Stability Audit.ipynb                                       ← 50-seed Louvain stability & 20-seed porosity recheck
│   ├── Account Classification Intercoder Reliability.ipynb                      ← Cohen's kappa & AI vs human agreement
│   ├── Classification Accuracy CI.ipynb                                         ← Wilson & Clopper-Pearson CI for AI accuracy
│   ├── Simplified Community-Level Network (Figure S2).ipynb                     ← Meta-network of the largest communities
│   ├── Dyadic Dependence Robustness.ipynb                                       ← Cross-community shift on unique dyads
│   ├── Duration and Volume Control.ipynb                                        ← Day-level cross-community ratio test
│   ├── Paired Community Selection-Bias Assessment.ipynb                         ← 38 selected vs 75 excluded communities
│   └── Engagement Effect Sizes and CIs.ipynb                                    ← Rank-biserial effect sizes with 95% CI
│
├── derived-data/
│   ├── cognitive fusion index.csv                                               ← CFI scores and z-scores per narrative
│   ├── community porosity.csv                                                   ← Community porosity pre- and post-shift
│   ├── descriptive engagement per narrative.csv                                 ← Median view counts per narrative
│   ├── excitation index.csv                                                     ← Excitation Index scores per narrative
│   ├── excitation integrated table.csv                                          ← Integrated EI component table
│   ├── kruskal wallis engagement.csv                                            ← Kruskal-Wallis engagement test results
│   ├── meta network per narrative.csv                                           ← Meta-network community connectivity per narrative
│   ├── pairwise mannwhitney engagement.csv                                      ← Pairwise Mann-Whitney U test results
│   ├── penetration by narrative.csv                                             ← Cross-community edges and reach per narrative
│   ├── penetration by topic.csv                                                 ← Cross-community penetration per BERTopic topic
│   │
│   └── hashed/
│       ├── Data bert with topics hashed.csv                                     ← Tweets with BERTopic topic assignments
│       ├── Data diffusion analysis hashed.csv                                   ← Tweets with diffusion scores and narrative labels
│       ├── Data with community hashed.csv                                       ← Tweets with community assignments
│       ├── actor engagement structural merged hashed.csv                        ← Per-account engagement and structural reach merged
│       ├── actor roles classification hashed.csv                                ← Structural role classification per account
│       ├── affan community propagation fixed hashed.csv                         ← First-mover accounts per community (Affan cascade)
│       ├── cascade hop levels hashed.csv                                        ← Hop-level assignments per account in cascade
│       ├── community summary hashed.csv                                         ← Community-level summary statistics
│       ├── network edges hashed.csv                                             ← Directed edge list with interaction metadata
│       ├── network nodes hashed.xlsx                                            ← Node list with degree and account type
│       └── network nodes with community hashed.csv                              ← Node list with Louvain community assignments
│
├── CITATION.cff                                                                 ← Citation metadata
├── LICENSE                                                                      ← Creative Commons Attribution 4.0 License
└── README.md                                                                    ← This file
```

---

## Dataset Description

**Collection period:** August 1 – September 29, 2025
**Platform:** X (formerly Twitter)
**Language:** Bahasa Indonesia

### Raw Data

| File | Description |
| --- | --- |
| `main-data/Book62-hashed.csv` | Anonymized tweet dataset: 29,289 tweets from 19,621 unique authoring accounts |

#### Column Dictionary — Raw Data

| Column | Description |
| --- | --- |
| `username` | Anonymized account identifier (irreversibly hashed; original usernames are not recoverable) |
| `full_text` | Full text content of the tweet |

### Derived Data

Files in `derived-data/` contain aggregate-level outputs with no account identifiers. Files in `derived-data/hashed/` contain account-level outputs where usernames remain present in hashed form.

#### derived-data/

| File | Description |
| --- | --- |
| `cognitive fusion index.csv` | CFI scores and component z-scores for all seven narrative categories |
| `community porosity.csv` | Community porosity values per community per temporal phase (pre- and post-shift) |
| `descriptive engagement per narrative.csv` | Median view counts and tweet counts per narrative |
| `excitation index.csv` | Excitation Index scores and component values per narrative |
| `excitation integrated table.csv` | Full integrated EI component table including post-shift engagement per tweet |
| `kruskal wallis engagement.csv` | Kruskal-Wallis test results for engagement metric comparisons across narratives |
| `meta network per narrative.csv` | Meta-network statistics per narrative: communities connected, diameter, average path length |
| `pairwise mannwhitney engagement.csv` | Pairwise Mann-Whitney U test results with Bonferroni-corrected p-values and effect sizes |
| `penetration by narrative.csv` | Cross-community edge counts, maximum hop depth, and communities reached per narrative |
| `penetration by topic.csv` | Cross-community penetration statistics per individual BERTopic topic prior to narrative consolidation |

#### derived-data/hashed/

| File | Description |
| --- | --- |
| `Data bert with topics hashed.csv` | Full tweet dataset with BERTopic topic assignments and probabilities |
| `Data diffusion analysis hashed.csv` | Tweet dataset with diffusion scores, narrative labels, and phase assignments |
| `Data with community hashed.csv` | Tweet dataset with Louvain community assignments |
| `actor engagement structural merged hashed.csv` | Per-account engagement metrics merged with structural reach measures |
| `actor roles classification hashed.csv` | Structural role classification (Attention Sink, Local Amplifier, Diffusion Driver) per account |
| `affan community propagation fixed hashed.csv` | First-mover account per community for the Affan Kurniawan cascade |
| `cascade hop levels hashed.csv` | Hop-level assignments for all accounts reached in the BFS cascade traversal |
| `community summary hashed.csv` | Community-level summary statistics including size and degree distribution |
| `network edges hashed.csv` | Directed edge list with interaction type, weight, and temporal metadata |
| `network nodes hashed.xlsx` | Node list with in-degree, out-degree, and account type |
| `network nodes with community hashed.csv` | Node list with Louvain community assignments and account type |

> **Note on anonymization:** Usernames in all files within `derived-data/hashed/` have been anonymized using a one-way hashing method prior to publication, in compliance with X's Terms of Service and to protect user privacy.

---

## Analytical Framework and Pipeline

The notebooks in `analytical-notebook/` fall into two groups. The **core pipeline** (Stages 1 to 11) implements the sequential analysis described in Section 3 of the manuscript, where each stage corresponds to a distinct methodological step and later stages depend on the outputs of earlier ones. The **robustness notebooks** implement the additional sensitivity, stability, and reliability analyses added during peer review, and they read outputs produced by the core pipeline.

### Core Pipeline

### Stage 1 — Thematic Modeling via BERTopic
**Notebook:** `BERTopic Setup.ipynb`

Identifies thematic structure using BERTopic with Indonesian sentence-BERT embeddings (`firqaaa/indo-sentence-bert-base`), UMAP dimensionality reduction, and HDBSCAN clustering. Produces 19 coherent topics with an outlier rate of approximately 23%. Temporal distributions are used to define the pre-shift (August 1–26) and post-shift (August 28–September 29) analytical windows.

### Stage 2 — Diffusion Score per Topic
**Notebook:** `BERTopic Linking Diffusion Depth to Topic Change.ipynb`

Links BERTopic-assigned topics to diffusion behavior by computing a composite diffusion score per narrative topic. Outputs are used as inputs to the Excitation Index computation in Stage 7.

### Stage 3 — Network Graph Construction
**Notebook:** `Network Graph Construction.ipynb`

Constructs a directed weighted graph where nodes represent accounts and edges represent replies, quote tweets, and mentions directed from the referring account to the account referred to. Retweets are not used as edges because only an aggregate retweet count is recorded and the retweeting account is not identifiable. Output: 11,426 nodes and 13,994 unique weighted directed edges.

### Stage 4 — Community Detection
**Notebook:** `Community Detection.ipynb`

Applies the Louvain algorithm on the undirected weighted projection (resolution 1.0, seed 42) to detect community structure. Output: 1,667 communities, modularity = 0.7991.

### Stage 5 — Social Penetration Metrics
**Notebook:** `Social Penetration Metrics.ipynb`

Computes cross-community penetration metrics including community porosity, hop depth per cascade, and inter-community edge ratios across the pre- and post-shift temporal windows.

### Stage 6 — Excitation Effect and Narrative Shift Trigger (Steps 1 and 2)
**Notebook:** `Excitation Effect Narrative Shift Trigger Steps 1 and 2.ipynb`

Reconstructs cascade sequences in chronological order using timestamped interaction events matched to BERTopic-assigned topics. Computes engagement velocity and temporal excitation patterns. Includes the chi-square test for the cross-community ratio shift (pre-shift 13.5% vs. post-shift 16.7%).

### Stage 7 — Excitation Effect and Narrative Shift Trigger (Steps 3 and 4)
**Notebook:** `Excitation Effect Narrative Shift Trigger Steps 3 and 4.ipynb`

Performs statistical integration of cascade components and formally computes the Excitation Index (EI) as the unweighted mean of four z-scored indicators: mean diffusion score, maximum hop depth, mean hop depth, and post-shift median engagement per tweet.

### Stage 8 — Actor Role Analysis
**Notebook:** `Actor Role Analysis.ipynb`

Classifies each account into one of three structural roles (Attention Sink, Local Amplifier, or Diffusion Driver) using the 75th-percentile degree rule and the cross-community edge count. Includes the chi-square test for the association between account type and structural role (χ² = 275.41, df = 4, p < 0.001).

### Stage 9 — Cross-Community Penetration and Cognitive Fusion
**Notebook:** `Cross-Community Penetration Cognitive Fusion.ipynb`

Computes community porosity at paired temporal windows and the Cognitive Fusion Index (CFI) as the unweighted mean of four z-scored structural indicators: maximum hop depth, mean hop depth, narrative-level porosity, and unique inter-community dyads. Includes the Wilcoxon signed-rank test (n = 38, W = 178, p = 0.025) and the CFI sensitivity analysis under four alternative weighting schemes.

### Stage 10 — Supplementary: Engagement Comparison per Narrative
**Notebook:** `Fix Analysis Novelty3 Engagement per Narrative 3.ipynb`

Supplementary analysis demonstrating that the Affan Kurniawan narrative produced significantly higher diffusion intensity than economic grievance narratives, measured through Kruskal-Wallis and pairwise Mann-Whitney U tests (Bonferroni-corrected α = 0.000476) on view count distributions across all seven narrative categories. Produces the engagement statistics reported in Table S1 and Section 4.2 of the manuscript.

### Stage 11 — Supplementary: Figure 4 (Engagement vs. Structural Reach)
**Notebook:** `Fix Figure Engagement vs Structural Reach Final.ipynb`

Produces Figure 4 and computes the Spearman correlation between cumulative view count and cross-community edges (ρ = 0.232, p = 8.73 × 10⁻⁷⁹, n = 6,365). This notebook incorporates the post-relabeling corrected account classification file.

### Robustness and Reviewer-Requested Analyses

These notebooks implement the additional sensitivity, stability, and reliability analyses added during the revision. They read outputs produced by the core pipeline.

### Louvain Seed Stability Audit
**Notebook:** `Louvain Seed Stability Audit.ipynb`

Reruns Louvain community detection under 50 random seeds and compares each partition against the canonical seed-42 partition (modularity 0.797, SD 0.002; community count 1,661 to 1,687; normalized mutual information 0.935; adjusted Rand index 0.726). Rechecks the paired porosity result against 20 alternative seed partitions to confirm the direction of the porosity increase is not an artifact of a single partition.

### Account Classification Intercoder Reliability
**Notebook:** `Account Classification Intercoder Reliability.ipynb`

Reports the intercoder reliability of the account-type classification: Cohen's kappa between two independent coders (0.890) and the AI versus human-consensus agreement (91.9%). Provided as a record of the reliability assessment. The raw coder sheets are not published because they contain account identifiers.

### Classification Accuracy CI
**Notebook:** `Classification Accuracy CI.ipynb`

Computes the Wilson and Clopper-Pearson 95% confidence intervals for the AI classification accuracy (374 of 407 consensus accounts; Wilson interval [88.8, 94.2]).

### Simplified Community-Level Network (Figure S2)
**Notebook:** `Simplified Community-Level Network (Figure S2).ipynb`

Builds the simplified community-level meta-network of the largest communities, with nodes sized by member count and colored by dominant narrative and edges representing cross-community interaction volume. Produces Figure S2 in the Supplementary Material.

### Dyadic Dependence Robustness
**Notebook:** `Dyadic Dependence Robustness.ipynb`

Recomputes the cross-community proportion shift on unique directed dyads, counting each source-target pair once per period (14.5% pre-shift to 17.3% post-shift; χ² = 21.17, p = 4.2 × 10⁻⁶), corroborated by Fisher's exact test and a dyad-level permutation test (10,000 permutations, seed 42).

### Duration and Volume Control
**Notebook:** `Duration and Volume Control.ipynb`

Tests whether the cross-community increase reflects the narrative shift rather than the greater post-shift activity volume, using a day-level analysis in which each day is one observation (Mann-Whitney rank-biserial r = 0.552, p = 0.0002).

### Paired Community Selection-Bias Assessment
**Notebook:** `Paired Community Selection-Bias Assessment.ipynb`

Assesses the selection implied by restricting the paired porosity analysis to the 38 communities active in both windows, comparing them against the 75 excluded communities on size and pre-shift porosity.

### Engagement Effect Sizes and CIs
**Notebook:** `Engagement Effect Sizes and CIs.ipynb`

Computes rank-biserial effect sizes with 95% bootstrap confidence intervals (B = 10,000, seed 42) for the pairwise engagement comparisons across the seven narrative categories.

---

## Replication Instructions

All notebooks are designed to run in [Google Colab](https://colab.research.google.com/) with a standard GPU runtime (T4).

1. Clone or download this repository.
2. Upload the target notebook to your Google Colab workspace.
3. When prompted, upload the relevant input files from `main-data/` or `derived-data/` as specified at the top of each notebook.
4. Execute cells sequentially. Intermediate output files generated by earlier stages are required inputs for later stages, so run the core pipeline in order (Stages 1–11). The robustness notebooks read outputs of the core pipeline and can be run afterward.

The intercoder reliability notebooks read coder sheets that are not published because they contain account identifiers. They are provided together with their outputs as a record of the reported reliability statistics.

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

Data collection was conducted using keyword-based retrospective queries from platform X in accordance with platform policies at the time of collection. The authors acknowledge that platform Terms of Service restrict the redistribution of raw tweet content; all shared data has been anonymized accordingly.
