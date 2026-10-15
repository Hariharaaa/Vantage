# Vantage UI Components (`components/`)

This directory houses the React 19 UI component library powering Vantage. It is styled with Tailwind CSS 4, animated with Framer Motion, and composed using Radix UI primitives.

---

## Directory Overview

```
components/
├── landing/     # Landing page sections, hero visualizer, interactive demo widgets
├── connect/     # Onboarding workflows, Account Aggregator consent simulation, CAS upload
├── dashboard/   # Product dashboard: health score, allocation charts, treemaps, overlap matrices
├── report/      # Print-styled document components designed for Puppeteer PDF export
└── ui/          # Low-level primitives (buttons, dialogs, badges, cards, tabs, tooltips)
```

---

## Key Modules

### 1. `components/dashboard/`
The core application surface:
- **`HealthScoreRing.tsx`**: Radial animated score gauge visualizing overall score (0–100) and sub-component ratings.
- **`AllocationChart.tsx`**: Asset class distribution bar and target drift indicator.
- **`OverlapMatrix.tsx`**: Heatmap and cross-holding stacked bar chart showing duplicate stock exposure across mutual funds.
- **`Treemap.tsx`**: Squarified industry concentration treemap visualizing capital exposure by economic sector.
- **`FindingsFeed.tsx`**: Ranked list of diagnostic findings with expandable arithmetic derivation cards.
- **`WhatIfSimulator.tsx`**: Interactive slider simulating portfolio value under severe market shock conditions.
- **`NarrativeCard.tsx`**: Streaming plain-language portfolio explanation powered by Google Gemini 2.5 Flash.

### 2. `components/landing/`
Marketing and educational landing page components:
- **`HeroSection.tsx`**: Visual introduction to portfolio look-through intelligence.
- **`OverlapTeaser.tsx`**: Interactive preview of the fund duplication problem.
- **`MethodologyCard.tsx`**: Highlights the deterministic, rule-based approach vs. black-box models.

### 3. `components/connect/`
Consent-first onboarding and data ingestion:
- Consent flow matching the Indian Account Aggregator (AA) framework.
- CAS (Consolidated Account Statement) PDF/Excel upload handler.
- Persona quick-picker allowing instantaneous testing with sample portfolios.

### 4. `components/report/`
Print-styled 9-section portfolio audit report designed for server-side PDF generation via Puppeteer.

### 5. `components/ui/`
Reusable design system primitives built with `clsx` and `tailwind-merge` (`cn()` helper in `lib/utils.ts`):
- `Button`, `Badge`, `Card`, `Dialog`, `Progress`, `Tabs`, `Tooltip`, and icons from `lucide-react`.
