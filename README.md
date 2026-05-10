# Financial Reporting Dashboard — Power BI | Real Client Project

> **Real client · SAGE ERP integration · 100+ DAX measures · Live in production**  
> 4,000+ accounting entries · 15+ tables · Star Schema + Bridge tables · 7 pages

🇫🇷 [Version française disponible ici](README_FR.md)

---

## Client Context

**Industry:** Moroccan company — distribution & services  
**Main stakeholder:** Chief Financial Officer (CFO / RAF)  
**Timeline:** February – April 2026  
**Status:** Delivered and live in production with automated refresh on Power BI Service

> *Client data and dashboard visuals are not publicly shared to protect
> confidentiality. This repository documents the architecture, data modeling,
> and business logic.*

---

## Business Problem

The CFO was producing monthly financial reports manually in Excel:
a slow, error-prone process that delivered little value in management meetings.

**Concrete consequences:**
- High monthly closing time
- Financial indicators hard to read quickly for the board
- No real-time visibility on cash flow and working capital (BFR)
- SAGE accounting data underused — no structured pipeline

**Mission:** Transform raw SAGE exports into a dynamic financial management
tool, immediately adopted by the CFO and the executive team.

---

## Solution Delivered

### ETL Pipeline — SAGE to Power BI
- Extraction from multi-file SAGE Excel exports
- Cleaning and normalization: account classes, accounting roots, reversal entry detection
- Data quality rules and consistency checks
- Cross-period anomaly detection and correction
- Automated refresh deployed on Power BI Service

### Data Model — Star Schema with Bridge Tables

Architecture optimized for performance and scalability:

```
Fact table
└── Faits_GrandLivre        → 4,000+ SAGE accounting entries

Dimension tables
├── DimCalendrier            → time intelligence
├── DimTiers                 → clients & suppliers
└── DimMapping               → accounting classification (PCGE)

Bridge tables
├── Bridge_Piece_Tiers       → revenue attribution to clients
└── Bridge_Piece_Fourn       → purchase attribution to suppliers

Disconnected tables
└── Segmentation, waterfall, advanced business logic
```

![Star Schema](Schema_Etoile.png)

### DAX Measures — 100+ measures developed

**Profitability**

| Measure | Description |
|---|---|
| `CA_Total` | Total revenue (Export + Local) |
| `Marge_Brute` | Revenue - Cost of goods sold |
| `EBITDA` | Gross Margin - Personnel costs - Fixed costs |
| `Résultat_Net` | Net income after all charges and taxes |

**Cash Flow & Working Capital**

| Measure | Description |
|---|---|
| `BFR` | Receivables + Inventory - Payables - Tax liabilities |
| `DSO` | Receivables / (Revenue / 365) — average collection delay |
| `DPO` | Payables / (Charges / 365) — average supplier payment delay |
| `DIO` | Inventory / (Variable Cost / 365) — inventory turnover in days |
| `Cash_Runway_Mois` | Months of cash available at current burn rate |

**Advanced Analytics**
- Dynamic KPI alerts on variance thresholds (defined with CFO)
- Client concentration analysis
- Drill-through to individual General Ledger entries
- P&L waterfall (Revenue → Net Income)
- Dynamic segmentation by client, supplier, and geography

---

## Dashboard — 7 Pages

| Page | Content |
|---|---|
| 1 — Executive View | Synthetic KPIs · Global performance · Board-level alerts |
| 2 — Income Statement (P&L) | Revenue → Net Income waterfall · Margin analysis |
| 3 — Revenue & Counterparties | Export/Local breakdown · Top clients · Concentration |
| 4 — Cost Analysis | Cost structure · Trend · Variance |
| 5 — Cash Flow & Working Capital | DSO · DPO · DIO · Cash Runway · Liquidity alerts |
| 6 — General Ledger Detail | Drill-through to individual SAGE accounting entries |
| 7 — Management Comments | Input page for CFO annotations during board meetings |

---

## Business Impact

| Result | Detail |
|---|---|
| Immediate adoption | CFO and executive team onboarded from day one |
| Reduced closing time | Measurable reduction in monthly reporting production time |
| Standardized reporting | From manual Excel to dynamic financial management tool |
| Training delivered | Onboarding videos + user guide & refresh documentation |
| Fully documented | All DAX measures and business rules documented for reproducible use |

---

## Tech Stack

- **Power BI Desktop + Power BI Service** — development & production deployment
- **DAX** — 100+ calculated measures
- **Power Query / M** — ETL pipeline from SAGE exports
- **Excel** — data source (multi-file SAGE exports)
- **Star Schema + Bridge Tables** — advanced dimensional modeling

---

## Documentation

| Document | Content |
|---|---|
| [DAX_MEASURES.md](DAX_MEASURES.md) | Full DAX measure code by category |
| [METHODOLOGY.md](METHODOLOGY.md) | Architecture, ETL pipeline, modeling decisions |
| [Schema_Etoile.png](Schema_Etoile.png) | Data model diagram |

---

## Repository Structure

```
cmgp-financial-dashboard/
├── README.md                  # This file (English)
├── README_FR.md               # French version
├── DAX_MEASURES.md
├── METHODOLOGY.md
├── Schema_Etoile.png
└── pbix/
    └── (not shared — confidential client data)
```

---

## Author

**Boubacar Nikiema** — Data Analyst & BI Consultant

Specialized in financial dashboards, management reporting and ETL pipelines
using Power BI, SQL, Python and Excel. Based in Morocco, working with clients
across Africa and French-speaking Europe.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-boubacar--nikiema-blue?logo=linkedin)](https://linkedin.com/in/boubacar-nikiema)
[![YouTube](https://img.shields.io/badge/YouTube-BoubacarDataAnalyst-red?logo=youtube)](https://youtube.com/@BoubacarDataAnalyst)
[![Email](https://img.shields.io/badge/Email-nikiemaboubacar%40gmail.com-gray?logo=gmail)](mailto:nikiemaboubacar@gmail.com)

---

Looking to automate your financial reporting or implement data-driven management?
Let's talk.

---

*Real client project · Confidential data not shared · Code: MIT License*
