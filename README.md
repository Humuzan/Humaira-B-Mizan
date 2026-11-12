# A* Search & Betweenness Centrality on the Pennsylvania Road Network

Graph analysis of a real-world road network using two AI algorithms — A* Search for shortest-path routing and Brandes' Betweenness Centrality for identifying critical intersections.

**Dataset:** Stanford SNAP — [roadNet-PA](https://snap.stanford.edu/data/roadNet-PA.html)  
**Course:** Artificial Intelligence Lab | Bangladesh University of Professionals (BUP)  
**Team:** Reefah Tasnia · Humaira Binte Mizan · Maisha Monwar Prodipta

---

## What This Project Does

Given Pennsylvania's road network (1,088,092 intersections, 1,541,898 roads), we answer two questions:

1. **What is the shortest route between two intersections?** → A* Search
2. **Which intersections are so critical that removing them would most disrupt the network?** → Brandes' Betweenness Centrality

---

## Dataset

| Property | Value |
|---|---|
| Nodes | 1,088,092 |
| Edges | 1,541,898 |
| Avg Degree | 2.83 |
| Clustering Coefficient | 0.0455 |
| Largest Component | 99.95% of nodes |
| Source | Stanford SNAP |

Download `roadNet-PA.txt` from: https://snap.stanford.edu/data/roadNet-PA.html

---

## Algorithms

### A* Search
- Finds optimal shortest paths on the full 1M-node graph
- Heuristic: `h(u, v) = 1 / (1 + degree(v))` — admissible, no GPS coordinates required
- Verified against NetworkX BFS: **100% optimality**

### Brandes' Betweenness Centrality
- Identifies the most critical intersections in the network
- Run on a 5,000-node BFS-extracted subgraph (full graph requires ~10¹² operations)
- Verified against NetworkX: **Pearson r = 1.0000**

---

## Results

| Metric | Value |
|---|---|
| A* — paths found | 10 / 10 (100%) |
| A* — avg path cost | 349.40 hops |
| A* — avg nodes expanded | 583,036 |
| A* — avg time per query | 4.10 seconds |
| A* — optimality | 100% (verified vs NetworkX BFS) |
| Brandes' — runtime | 584.84 seconds |
| Brandes' — peak memory | 1.71 MB |
| Brandes' — Pearson r | 1.0000 (vs NetworkX) |
| Top BC node | Node 280193 (BC = 0.4517) |

---

## Setup & Usage

This project runs entirely in **Google Colab** — no local installation required.

### Step 1 — Open the notebook
Upload `roadNet_PA_AI_Lab_Project.ipynb` to [Google Colab](https://colab.research.google.com)

### Step 2 — Upload the dataset
Run Section 2 of the notebook and upload `roadNet-PA.txt` when prompted,  
or mount Google Drive and set the file path accordingly.

### Step 3 — Run all cells
Run cells top to bottom. All dependencies install automatically.

### Dependencies
