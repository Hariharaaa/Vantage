# Vantage Portfolio & Market Datasets (`data/`)

This directory houses the mock investor portfolios, mutual fund factsheets, and instrument catalogs used to demonstrate and test Vantage.

> **Data Provenance & Privacy Note**:
> All investor folios, accounts, unit counts, balances, and values are **synthetic fixtures** generated for demonstration. Company names, mutual fund scheme names, ISINs, and market categories reflect real Indian market instruments, but no data represents any real individual or live investment account.

---

## Bundled Investor Personas

Vantage includes four distinct synthetic personas configured in [`data/mock/portfolios.ts`](file:///Users/harihara/Downloads/Vantage-main/data/mock/portfolios.ts). Each persona is designed to test and highlight specific portfolio risks:

| Persona | URL Parameter | Age | Risk Capacity | Health Score | Core Diagnostic Findings |
|---|---|:---:|:---:|:---:|---|
| **Aarav Sharma** | `?portfolio=aarav` | 32 | **86** (Aggressive) | **70** (Good) | **Hidden Fund Overlap**: 38.7% overlap between HDFC Flexi Cap and ICICI Bluechip; high aggregate concentration in financial services via direct + indirect routes. |
| **Sunita Rao** | `?portfolio=sunita` | 58 | **31** (Conservative) | **56** (Fair) | **Duration & Liquidity Mismatch**: Near-retirement investor with excess equity volatility and insufficient liquid debt cushion for near-term cashflow needs. |
| **Meera Patel** | `?portfolio=meera` | 41 | **63** (Moderate) | **82** (Strong) | **Exemplary Balanced Portfolio**: Thoughtful diversification across large cap, mid cap, debt, sovereign gold bonds (SGB), and REITs. |
| **Rohan Verma** | `?portfolio=rohan` | 28 | **86** (Aggressive) | **44** (Fair/Poor) | **Severe Concentration**: Extreme single-stock risk (>35% in one stock) and over 60% sector concentration in technology and financials. |

---

## File Structure

```
data/
├── mock/
│   ├── fund-holdings.ts   # Top 10-30 underlying equity/debt holdings per mutual fund scheme
│   ├── instruments.ts     # Metadata for NSE/BSE stocks, ETFs, REITs, and SGBs (ISIN, sector, market cap)
│   └── portfolios.ts      # Complete UnifiedPortfolio objects for Aarav, Sunita, Meera, and Rohan
└── portfolio.ts           # Sample visual datasets for landing page charts and feature showcases
```

---

## Fund Holdings & Look-Through Factsheets

In [`data/mock/fund-holdings.ts`](file:///Users/harihara/Downloads/Vantage-main/data/mock/fund-holdings.ts), each scheme maps to its disclosed underlying holdings:

```typescript
export const FUND_HOLDINGS: Record<string, FundFactsheet> = {
  "INF179K01YV8": {
    schemeName: "HDFC Flexi Cap Fund",
    asOf: "2026-06-30",
    equityShare: 0.95,
    topHoldings: [
      { isin: "INE040A01034", name: "HDFC Bank Ltd", weight: 0.088, sector: "Financial Services" },
      { isin: "INE009A01021", name: "Infosys Ltd", weight: 0.065, sector: "Technology" },
      // ...
    ]
  }
};
```

When an investor holds both the direct stock and one or more funds owning that stock, the analytics engine calculates the combined effective exposure.

---

## Adding a Custom Portfolio

To run Vantage against custom data, construct an object conforming to `UnifiedPortfolio` from [`types/portfolio.ts`](file:///Users/harihara/Downloads/Vantage-main/types/portfolio.ts):

```typescript
import { UnifiedPortfolio } from "@/types/portfolio";

export const customPortfolio: UnifiedPortfolio = {
  schemaVersion: "1.0.0",
  portfolioId: "custom-01",
  generatedAt: new Date().toISOString(),
  investorName: "Custom Investor",
  riskProfileInput: {
    age: 35,
    horizonYears: 15,
    monthlyIncome: 120000,
    monthlyExpenses: 60000,
    dependents: 2,
    statedRiskAppetite: "moderate",
    drawdownTolerancePercent: 25,
  },
  holdings: [
    {
      id: "h-1",
      kind: "equity",
      source: "cas_cdsl",
      asOf: "2026-10-01",
      currentValue: 150000,
      isin: "INE002A01018",
      symbol: "RELIANCE",
      name: "Reliance Industries Ltd",
      quantity: 50,
      sector: "Energy",
      marketCap: "large",
    },
    // Add additional mutual funds, bonds, EPF, gold, or REITs
  ],
};
```

You can then pass this object to `/api/analyze` or `analysePortfolio(customPortfolio)` in code.
