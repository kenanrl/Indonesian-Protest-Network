# Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![Platform: X (Twitter)](https://img.shields.io/badge/Platform-X%20(Twitter)-black)](https://x.com)
[![Period: Aug–Sep 2025](https://img.shields.io/badge/Period-August–September%202025-blue)]()
[![Journal: SSHO](https://img.shields.io/badge/Journal-Social%20Sciences%20%26%20Humanities%20Open-orange)]()

---

## About This Repository

This repository contains the anonymized dataset and Python analytical notebooks used in the research manuscript:

> **"Who Carries the Message? Mapping the Hidden Infrastructure of Grassroots Solidarity in Indonesia's 2025 Digital Protest Networks"**

The repository is shared to ensure transparency and reproducibility in accordance with the journal's data availability policy. The analytical pipeline combines network analysis (Louvain community detection, cascade depth tracking), BERTopic-based thematic modeling, and novel composite metrics, the Excitation Index and Cognitive Fusion Index (CFI) to examine how protest narratives diffused across structurally fragmented communities on platform X during the Indonesian civic unrest of August-September 2025.

---

## Data Availability Statement

The data supporting the findings of this study were collected from platform X (formerly Twitter) using keyword-based queries targeting protest-related hashtags and terms. The raw dataset cannot be publicly shared in its original form due to platform Terms of Service restrictions.

The dataset provided in this repository has been processed to comply with platform policies and ethical standards. Specifically, all user identifiers have been **irreversibly anonymized through one-way hashing** prior to publication, making original usernames non-recoverable. Only the hashed identifier and tweet text content are retained.

---

## Repository Structure

```
Indonesian-Protest-Discourse/
│
├── main-data/
│   └── raw-data-hashed.csv                                        ← Anonymized tweet dataset
│
├── data-analysis/
│   ├── BERTopic: Linking Diffusion Depth to Topic Change          ← Composite diffusion score per topic
│   ├── Network Graph Construction                                 ← Directed interaction network construction
│   ├── Community Detection                                        ← Louvain community detection
│   ├── Social Penetration Metrics                                 ← Cross-community penetration metrics
│   ├── Excitation Effect & Narrative Shift Trigger (Steps 1–2)    ← Temporal excitation & engagement velocity
│   ├── Excitation Effect & Narrative Shift Trigger (Steps 3–4)    ← Statistical integration & cascade trigger
│   ├── Actor Role Analysis                                        ← Actor role classification (sink vs driver)
│   └── Cross-Community Penetration & Cognitive Fusion             ← Community porosity & CFI computation
│
├── CITATION.cff                                                   ← Citation metadata
├── LICENSE                                                        ← Creative Commons Attribution 4.0 License
└── README.md                                                      ← This file
```

---

## Dataset Description

**Collection period:** August 1 – September 29, 2025  
**Platform:** X (formerly Twitter)  
**Language:** Bahasa Indonesia  
**Collection method:** Keyword-based retrospective queries targeting 12 protest-related hashtags and terms (e.g., `IndonesiaGelap`, `JusticeForAffan`, `BubarkanDPR`, `ACAB`, `demo dpr`)

| File | Description |
|---|---|
| `main-data/raw-data-hashed.csv` | Anonymized tweet dataset: 29,289 tweets from 11,426 unique accounts |

### Column Dictionary

| Column | Description |
|---|---|
| `username` | Anonymized account identifier (irreversibly hashed; original usernames are not recoverable) |
| `full_text` | Full text content of the tweet |

> **Note on anonymization:** Usernames have been anonymized using a one-way hashing method prior to publication, in compliance with X's Terms of Service and to protect user privacy.

---

## Analytical Framework & Pipeline

The notebooks in `data-analysis/` implement a sequential computational pipeline. Each notebook corresponds to a distinct methodological stage described in Section 3 of the manuscript.

### Stage 1 — Thematic Modeling via BERTopic
**Notebook:** `BERTopic: Linking Diffusion Depth to Topic Change`

Identifies thematic structure using BERTopic with Indonesian sentence-BERT embeddings (`firqaaa/indo-sentence-bert-base`), UMAP dimensionality reduction, and HDBSCAN clustering. Produces 19 coherent topics with temporal distributions used to define the pre-shift (August 1–26) and post-shift (August 28–September 29) windows. Computes a composite diffusion score per narrative topic.

### Stage 2 — Network Graph Construction
**Notebook:** `Network Graph Construction`

Constructs a directed weighted graph where nodes represent accounts and edges represent retweets, quote tweets, and replies. Output: 11,426 nodes, 13,994 directed edges.

### Stage 3 — Community Detection
**Notebook:** `Community Detection`

Applies the Louvain algorithm to detect community structure. Output: 1,667 communities, modularity = 0.7991.

### Stage 4 — Social Penetration Metrics
**Notebook:** `Social Penetration Metrics`

Computes cross-community penetration metrics including community porosity, hop depth per cascade, and inter-community edge ratios across pre- and post-shift temporal windows.

### Stage 5 — Excitation Effect & Narrative Shift Trigger (Steps 1–2)
**Notebook:** `Excitation Effect & Narrative Shift Trigger (Steps 1–2)`

Reconstructs cascade sequences in chronological order using timestamped interaction events matched to BERTopic-assigned topics. Computes engagement velocity and temporal excitation patterns.

### Stage 6 — Excitation Effect & Narrative Shift Trigger (Steps 3–4)
**Notebook:** `Excitation Effect & Narrative Shift Trigger (Steps 3–4)`

Performs statistical integration of cascade components and formally computes the Excitation Index (EI) as the unweighted mean of four z-scored indicators: mean diffusion score, maximum hop depth, mean hop depth, and post-shift median engagement per tweet.

### Stage 7 — Actor Role Analysis
**Notebook:** `Actor Role Analysis`

Classifies each account into one of three structural roles — Attention Sink, Local Amplifier, or Diffusion Driver — based on in-degree to out-degree ratio and cross-community edge count. Includes Spearman correlation between engagement and structural reach.

### Stage 8 — Cross-Community Penetration & Cognitive Fusion
**Notebook:** `Cross-Community Penetration & Cognitive Fusion`

Computes community porosity at paired temporal windows and the Cognitive Fusion Index (CFI) as the unweighted mean of four z-scored structural indicators: maximum hop depth, mean hop depth, post-shift porosity, and unique inter-community dyads. Includes Wilcoxon signed-rank test and CFI sensitivity analysis under four alternative weighting schemes.

---

## Replication Instructions

All notebooks are designed to run in [Google Colab](https://colab.research.google.com/) with a standard GPU runtime (T4).

1. Clone or download this repository.
2. Upload the target notebook to your Google Colab workspace.
3. When prompted, upload `main-data/raw-data-hashed.csv` as the input data file.
4. Execute cells sequentially. Intermediate output files generated by earlier stages are required inputs for later stages; run the pipeline in order (Stages 1–8).

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

## Citation

If you use this dataset or code in your research, please cite the manuscript as listed in `CITATION.cff` or use the following reference:

> Rahmandika, K. L., Ramadhani, D. P., & Alamsyah, A. (2025). Who carries the message? Mapping the hidden infrastructure of grassroots solidarity in Indonesia's 2025 digital protest networks. *Social Sciences & Humanities Open*. [DOI pending]

---

## Contact

For questions about the dataset or analytical notebooks, please open a [GitHub Issue](../../issues) or contact the corresponding author at `keinanlidzikri@student.telkomuniversity.ac.id`.

---

## Acknowledgements

Data collection was conducted using keyword-based retrospective queries from platform X in accordance with platform policies at the time of collection. The authors acknowledge that platform Terms of Service restrict the redistribution of raw tweet content; all shared data has been anonymized accordingly.
