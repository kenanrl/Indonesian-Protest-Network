# Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![Platform: X (Twitter)](https://img.shields.io/badge/Platform-X%20(Twitter)-black)](https://x.com)
[![Period: Aug–Sep 2025](https://img.shields.io/badge/Period-August–September%202025-blue)]()

---

## About This Repository

This repository contains the anonymized dataset and Python analytical notebooks used in the research manuscript:

> **"Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks"**

The repository is shared to ensure transparency and reproducibility in accordance with the journal's data availability policy. The analytical pipeline combines network analysis (Louvain community detection, cascade depth tracking), BERTopic-based thematic modeling, and novel composite metrics, the Excitation Index and Cognitive Fusion Index (CFI), to examine how protest narratives diffused across structurally fragmented communities on platform X during the Indonesian civic unrest of August–September 2025.

---

## Data Availability Statement

The data supporting the findings of this study were collected from platform X (formerly Twitter) using keyword-based queries targeting protest-related hashtags and terms. The raw dataset cannot be publicly shared in its original form due to platform Terms of Service restrictions.

The dataset provided in this repository has been processed to comply with platform policies and ethical standards. Specifically, all user identifiers have been **irreversibly anonymized through one-way hashing** prior to publication, making original usernames non-recoverable. Only the hashed identifier and tweet text content are retained.

---

## Repository Structure

```
Indonesian-Protest-Network/
│
├── main-data/
│   └── raw-data-hashed.csv                                                      ← Anonymized raw tweet dataset
│
├── analytical-notebook/
│   ├── BERTopic Setup.ipynb                                                     ← Topic modeling on protest tweets
│   ├── BERTopic Linking Diffusion Depth to Topic Change.ipynb                   ← Composite diffusion score per topic
│   ├── Network Graph_Construction.ipynb                                         ← Directed interaction network construction
│   ├── Community Detection.ipynb                                                ← Louvain community detection
│   ├── Social Penetration Metrics.ipynb                                         ← Cross-community penetration metrics
│   ├── Excitation Effect Narrative Shift Trigger Steps 1 and 2.ipynb            ← Temporal excitation & engagement velocity
│   ├── Excitation Effect Narrative Shift Trigger Steps 3 and 4.ipynb            ← Statistical integration & cascade trigger
│   ├── Actor Role Analysis.ipynb                                                ← Actor role classification (sink vs driver)
│   ├── Cross-Community Penetration Cognitive Fusion.ipynb                       ← Community porosity & CFI computation
│   ├── Fix Analysis Novelty3 Engagement per Narrative 3.ipynb                   ← Supplementary engagement comparison per narrative
│   └── Fix Figure6 Engagement vs Structural Reach_Final.ipynb                   ← Figure 6: engagement vs structural reach (post-relabeling)
│
├── derived-data/
│   ├── cognitive fusion_index.csv                                               ← CFI scores and z-scores per narrative
│   ├── community porosity.csv                                                   ← Community porosity pre- and post-shift
│   ├── descriptive engagement per narrative.csv                                 ← Median view counts per narrative (Table S1)
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
│       ├── Data with community3_hashed.csv                                      ← Tweets with community assignments
│       ├── actor engagement structural merged hashed.csv                        ← Per-account engagement and structural reach merged
│       ├── actor roles classification hashed.csv                                ← Structural role classification per account
│       ├── affan_community propagation fixed hashed.csv                         ← First-mover accounts per community (Affan cascade)
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
|---|---|
| `main-data/raw-data-hashed.csv` | Anonymized tweet dataset: 29,289 tweets from 11,426 unique accounts |

#### Column Dictionary — Raw Data

| Column | Description |
|---|---|
| `username` | Anonymized account identifier (irreversibly hashed; original usernames are not recoverable) |
| `full_text` | Full text content of the tweet |

### Derived Data

Files in `derived-data/` contain aggregate-level outputs with no account identifiers. Files in `derived-data/hashed/` contain account-level outputs where usernames remain present in hashed form.

#### derived-data/ (aggregate, no identifiers)

| File | Description |
|---|---|
| `cognitive_fusion_index.csv` | CFI scores and component z-scores for all seven narrative categories (Table 5) |
| `community_porosity.csv` | Community porosity values per community per temporal phase (pre- and post-shift) |
| `descriptive_engagement_per_narrative.csv` | Median view counts and tweet counts per narrative (Table S1) |
| `excitation_index2.csv` | Excitation Index scores and component values per narrative (Table 4) |
| `excitation_integrated_table2.csv` | Full integrated EI component table including post-shift engagement per tweet |
| `kruskal_wallis_engagement.csv` | Kruskal-Wallis test results for engagement metric comparisons across narratives |
| `meta_network_per_narrative.csv` | Meta-network statistics per narrative: communities connected, diameter, average path length (Table S4) |
| `pairwise_mannwhitney_engagement.csv` | Pairwise Mann-Whitney U test results with Bonferroni-corrected p-values and effect sizes |
| `penetration_by_narrative.csv` | Cross-community edge counts, maximum hop depth, and communities reached per narrative (Table 4) |
| `penetration_by_topic.csv` | Cross-community penetration statistics per individual BERTopic topic prior to narrative consolidation |

#### derived-data/hashed/ (account-level, usernames hashed)

| File | Description |
|---|---|
| `Data_bert_with_topics2_hashed.csv` | Full tweet dataset with BERTopic topic assignments and probabilities |
| `Data_diffusion_analysis2_hashed.csv` | Tweet dataset with diffusion scores, narrative labels, and phase assignments |
| `Data_with_community3_hashed.csv` | Tweet dataset with Louvain community assignments |
| `actor_engagement_structural_merged_hashed.csv` | Per-account engagement metrics merged with structural reach measures |
| `actor_roles_classification_hashed.csv` | Structural role classification (Attention Sink, Local Amplifier, Diffusion Driver) per account |
| `affan_community_propagation_fixed2_hashed.csv` | First-mover account per community for the Affan Kurniawan cascade |
| `cascade_hop_levels_hashed.csv` | Hop-level assignments for all accounts reached in the BFS cascade traversal |
| `community_summary_hashed.csv` | Community-level summary statistics including size and degree distribution |
| `network_edges_hashed.csv` | Directed edge list with interaction type, weight, and temporal metadata |
| `network_nodes_hashed.xlsx` | Node list with in-degree, out-degree, and account type |
| `network_nodes_with_community3_hashed.csv` | Node list with Louvain community assignments and account type |

> **Note on anonymization:** Usernames in all files within `derived-data/hashed/` have been anonymized using a one-way hashing method prior to publication, in compliance with X's Terms of Service and to protect user privacy.

---

## Analytical Framework and Pipeline

The notebooks in `analytical-notebook/` implement a sequential computational pipeline. Each notebook corresponds to a distinct methodological stage described in Section 3 of the manuscript. The two supplementary fix notebooks (Stages 10 and 11) produce outputs used in Section 4 and the supplementary materials.

### Stage 1 — Thematic Modeling via BERTopic
**Notebook:** `BERTopic_Setup.ipynb`

Identifies thematic structure using BERTopic with Indonesian sentence-BERT embeddings (`firqaaa/indo-sentence-bert-base`), UMAP dimensionality reduction, and HDBSCAN clustering. Produces 19 coherent topics with an outlier rate of approximately 23%. Temporal distributions are used to define the pre-shift (August 1–26) and post-shift (August 28–September 29) analytical windows.

### Stage 2 — Diffusion Score per Topic
**Notebook:** `BERTopic_Linking_Diffusion_Depth_to_Topic_Change.ipynb`

Links BERTopic-assigned topics to diffusion behavior by computing a composite diffusion score per narrative topic. Outputs are used as inputs to the Excitation Index computation in Stage 6.

### Stage 3 — Network Graph Construction
**Notebook:** `Network_Graph_Construction.ipynb`

Constructs a directed weighted graph where nodes represent accounts and edges represent retweets, quote tweets, and replies. Output: 11,426 nodes, 13,994 directed edges.

### Stage 4 — Community Detection
**Notebook:** `Community_Detection.ipynb`

Applies the Louvain algorithm to detect community structure. Output: 1,667 communities, modularity = 0.7991.

### Stage 5 — Social Penetration Metrics
**Notebook:** `Social_Penetration_Metrics.ipynb`

Computes cross-community penetration metrics including community porosity, hop depth per cascade, and inter-community edge ratios across pre- and post-shift temporal windows.

### Stage 6 — Excitation Effect and Narrative Shift Trigger (Steps 1 and 2)
**Notebook:** `Excitation_Effect___Narrative_Shift_Trigger__Steps_1_and_2_.ipynb`

Reconstructs cascade sequences in chronological order using timestamped interaction events matched to BERTopic-assigned topics. Computes engagement velocity and temporal excitation patterns. Includes the chi-square test for the cross-community ratio shift (pre-shift 13.5% vs. post-shift 16.9%).

### Stage 7 — Excitation Effect and Narrative Shift Trigger (Steps 3 and 4)
**Notebook:** `Excitation_Effect___Narrative_Shift_Trigger__Steps_3_and_4_.ipynb`

Performs statistical integration of cascade components and formally computes the Excitation Index (EI) as the unweighted mean of four z-scored indicators: mean diffusion score, maximum hop depth, mean hop depth, and post-shift median engagement per tweet.

### Stage 8 — Actor Role Analysis
**Notebook:** `Actor_Role_Analysis.ipynb`

Classifies each account into one of three structural roles: Attention Sink, Local Amplifier, or Diffusion Driver, based on the in-degree to out-degree ratio and cross-community edge count. Includes the chi-square test for the association between account type and structural role (χ² = 275.41, p < 0.001, df = 4).

### Stage 9 — Cross-Community Penetration and Cognitive Fusion
**Notebook:** `Cross-Community_Penetration___Cognitive_Fusion.ipynb`

Computes community porosity at paired temporal windows and the Cognitive Fusion Index (CFI) as the unweighted mean of four z-scored structural indicators: maximum hop depth, mean hop depth, post-shift porosity, and unique inter-community dyads. Includes the Wilcoxon signed-rank test (n = 38, W = 178, p = 0.025) and CFI sensitivity analysis under four alternative weighting schemes.

### Stage 10 — Supplementary: Engagement Comparison per Narrative
**Notebook:** `Fix_Analysis_Novelty3_Engagement_per_Narrative__3_.ipynb`

Supplementary analysis demonstrating that the Affan Kurniawan narrative produced significantly higher diffusion intensity than economic grievance narratives, measured through Kruskal-Wallis and pairwise Mann-Whitney U tests (Bonferroni-corrected α = 0.000476) on view count distributions across all seven narrative categories. Produces the engagement statistics reported in Table S1 and Section 4.2 of the manuscript.

### Stage 11 — Supplementary: Figure 6 (Engagement vs. Structural Reach)
**Notebook:** `Fix_Figure6_Engagement_vs_Structural_Reach_Final.ipynb`

Produces Figure 6 (the dissociation between platform engagement and cross-community structural reach across account types) and computes the Spearman correlation between cumulative view count and cross-community edges (ρ = 0.232, p = 8.73 × 10⁻⁷⁹, n = 6,365). This notebook incorporates the post-relabeling corrected account classification file.

---

## Replication Instructions

All notebooks are designed to run in [Google Colab](https://colab.research.google.com/) with a standard GPU runtime (T4).

1. Clone or download this repository.
2. Upload the target notebook to your Google Colab workspace.
3. When prompted, upload the relevant input files from `main-data/` or `derived-data/` as specified at the top of each notebook.
4. Execute cells sequentially. Intermediate output files generated by earlier stages are required inputs for later stages; run the pipeline in order (Stages 1–11).

**Key dependencies:**

| Library | Version |
|---|---|
| NetworkX | 3.6.1 |
| SciPy | 1.16.3 |
| BERTopic | latest stable |
| HDBSCAN | latest stable |
| UMAP-learn | latest stable |
| pandas | latest stable |
| matplotlib | latest stable |

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
