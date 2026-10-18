# Graph Theory and Systemic Risk in Banking (NetworkX)

Graph theory fundamentals with NetworkX, applied to a real question: **how interconnected are major
global banks, and which ones would spread a shock?**

## Part 1: graph theory fundamentals

Undirected and directed graphs, layouts, degrees and shortest paths, centrality measures
(betweenness, closeness, degree), cliques, connected components, and loading graphs from edge lists.

## Part 2: systemic-risk network of 10 global banks

- **Data:** daily adjusted closing prices 2015 to 2025 from Yahoo Finance (`yfinance`) for
  JPM, BAC, WFC, C, HSBC, RY, BNP.PA, GLE.PA, DB and UBS.
- **Method:** daily returns (stationarity checked with ADF tests) → correlation matrix → bank network
  where edges link strongly co-moving institutions.
- **Findings:**
  - With all correlations, the network is a single complete clique: every bank moves with every other,
    so centrality cannot discriminate between them.
  - With a **0.6 correlation threshold**, structure appears: a dense core (JPM, BAC, C, WFC, RY, UBS),
    a periphery (BNP.PA, GLE.PA, HSBC), and **Deutsche Bank acting as the bridge** between them.
  - **Shock simulation:** removing DB cuts the periphery off from the core, showing how a single
    institution can carry the contagion paths of the network.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook notebooks/graph_theory_systemic_risk.ipynb
```

**Author:** Klaus KUEKOU
