# Vantage Documentation

Welcome to the Vantage technical and analytical documentation. This directory contains deep-dive references into the mathematical models, methodology, and visual assets powering the platform.

---

## Table of Contents

- [Methodology Whitepaper (`METHODOLOGY.md`)](#methodology-whitepaper)
- [Analytics Engine (`lib/analytics/README.md`)](#analytics-engine)
- [Mock Data & Personas (`data/README.md`)](#mock-data--personas)
- [Visual Assets & Screenshots (`screenshots/`)](#visual-assets--screenshots)

---

## Methodology Whitepaper

The primary technical reference is [**`docs/METHODOLOGY.md`**](file:///Users/harihara/Downloads/Vantage-main/docs/METHODOLOGY.md).

It documents the deterministic arithmetic behind every score in Vantage, including:
1. **Design Principles**: Rule-based vs. learned systems, why explanation travels with the number, and reporting floor figures.
2. **Normalisation and Look-Through**: Asset decomposition matrices for 17+ SEBI mutual fund categories.
3. **Risk Capacity Formulation**: Age factor, investment horizon, emergency fund coverage, and dependency ratios.
4. **Allocation and Drift**: Divergence calculation from rule-based target heuristics.
5. **Look-Through Overlap**: Pairwise and portfolio-wide stock-level duplication equations.
6. **Concentration and HHI**: Single-stock caps, top-10 share, and Herfindahl-Hirschman index benchmarks.
7. **Composite Health Score**: Weighted scoring system (0–100) aggregating diversification, risk alignment, concentration, and cost efficiency.
8. **Rule Engine & Findings**: Trigger thresholds for critical, warning, notice, and info diagnoses.
9. **What-If Simulation**: Deterministic drawdown and shock scenario projections.
10. **Known Limitations**: Disclosures on monthly factsheet latency, partial holdings coverage, and heuristics.

---

## Analytics Engine

For an architectural overview of the pure TypeScript modules executing this methodology in Next.js, refer to [**`lib/analytics/README.md`**](file:///Users/harihara/Downloads/Vantage-main/lib/analytics/README.md).

---

## Mock Data & Personas

For details on the synthetic portfolios and fund factsheets used for demonstration and testing, refer to [**`data/README.md`**](file:///Users/harihara/Downloads/Vantage-main/data/README.md).

---

## Visual Assets & Screenshots

The `docs/screenshots/` directory contains high-resolution captures of Vantage in action:

| Asset | Description |
|---|---|
| [`landing.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/landing.jpg) | Landing page with hero narrative and interactive problem demo |
| [`connect.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/connect.jpg) | Consent-driven Account Aggregator and CAS statement upload screen |
| [`dashboard.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/dashboard.jpg) | Main dashboard view with portfolio health score, metrics, and actions |
| [`overlap.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/overlap.jpg) | Look-through mutual fund overlap and cross-holding stack |
| [`sectors.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/sectors.jpg) | Interactive squarified industry concentration treemap |
| [`findings.jpg`](file:///Users/harihara/Downloads/Vantage-main/docs/screenshots/findings.jpg) | Severity-ranked diagnostic findings with mathematical derivations |
