# Citation-Semantic Misalignment in Academic Networks

**CSCE 670 — Data Mining Project**

**Repository:** [https://github.com/Utkarsh-Mishra444/graphsplit](https://github.com/Utkarsh-Mishra444/graphsplit)

## Overview

This project investigates the structural divergence between citation networks and topic-semantic networks in academic computer science papers. Papers cite each other for many reasons beyond topical similarity — prestige, methodological borrowing, recency bias, and community effects. Understanding this misalignment can improve paper classification, recommendation, and anomaly detection.

Using the **ogbn-arxiv** dataset (169,343 papers, 1.1M citation edges, 40 arXiv CS categories), we build both a citation graph and a topic-semantic graph from the same set of papers, then analyze where they agree, where they diverge, and whether that divergence is structured and meaningful.

## Key Findings (Checkpoint 1)

- Citation communities and LDA topic clusters share only **NMI = 0.33** — far from identical, confirming genuine misalignment
- **53% of citation edges** connect papers with different dominant topics, even though same-topic citation is 11x above random chance
- PageRank and topic centrality are essentially independent (**rho = 0.044**) — structurally important papers are not topically representative
- Louvain community detection finds **149 communities** in the citation graph, vs. 40 LDA topics and 40 arXiv categories
- All findings validated via permutation tests (z-score = 5,353) and configuration model baselines

## Dataset

- **Source:** [Open Graph Benchmark (ogbn-arxiv)](https://ogb.stanford.edu/docs/nodeprop/#ogbn-arxiv)
- **Text:** Titles and abstracts from [Stanford SNAP](https://snap.stanford.edu/ogb/data/misc/ogbn_arxiv/titleabs.tsv.gz)
- **Size:** 169,343 nodes, 1,166,243 directed citation edges
- **Labels:** 40 arXiv CS subcategories (e.g., cs.CV, cs.LG, cs.CL)
- **Temporal range:** 1971-2020
- **License:** ODC-BY

## Techniques Used

**Course techniques:**
- PageRank (citation importance)
- Community detection (Louvain algorithm)
- Topic modeling (LDA with 40 topics)
- TF-IDF text representation
- Clustering evaluation (NMI, ARI)

**Beyond-course techniques (planned for Checkpoint 2+):**
- Graph Neural Networks (GNNs) on dual graph views
- Multi-view graph learning
- Transformer-based text embeddings (SciBERT)

## Repository Structure

```
.
├── checkpoint1.ipynb    # Main analysis notebook (fully executed)
├── requirements.txt     # Python dependencies
├── README.md            # This file
└── data/                # Downloaded datasets (not tracked in git)
```

## Setup

```bash
# Create conda environment
conda create -n citation-misalignment python=3.10 -y
conda activate citation-misalignment

# Install dependencies
pip install -r requirements.txt

# Run the notebook
jupyter notebook checkpoint1.ipynb
```

Data downloads automatically on first run (~250 MB total).

## References

- Hu et al. (2020). *Open Graph Benchmark: Datasets for Machine Learning on Graphs.* NeurIPS.
- He et al. (2024). *TAPE: Harnessing Large Language Models as Versatile Enhancers for Text-Attributed Graphs.* ICLR.
- Blondel et al. (2008). *Fast unfolding of communities in large networks.* Journal of Statistical Mechanics.
- Blei et al. (2003). *Latent Dirichlet Allocation.* Journal of Machine Learning Research.
