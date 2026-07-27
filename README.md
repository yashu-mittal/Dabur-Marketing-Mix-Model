# Dabur Gen-Z Wellness Range — Marketing Mix Model + GTM Strategy

> **Portfolio / learning project.** This is **not** an official Dabur document and Dabur was not involved in its creation. Only the aggregate figures below (total ad spend, total revenue, and the digital-shift trend) are real and cited. All channel-level splits and monthly data are analyst-modeled simulations calibrated to those real figures. Full sourcing and every underlying data point are in the report and workbook — nothing here is presented as Dabur's actual internal data.

## What this is

A lite Marketing Mix Model (MMM) + Gen-Z go-to-market strategy for Dabur's Immunity & Wellness range (Chyawanprash, Honey, Glucose-D, wellness gummies). It quantifies channel-level marketing ROI across four consolidated channels and uses that to inform a digital-first repositioning strategy for a legacy Ayurvedic category, aimed at 18–27 year olds.


## Key findings

| Channel | Total Spend (Rs Cr, 24mo) | Attributed Sales (Rs Cr) | Contribution % | ROI (x) |
|---|---|---|---|---|
| Traditional Media (TV+Print) | 51.35 | 512.62 | 50.3% | **9.98x** |
| Digital Display & Search | 37.49 | 221.81 | 21.8% | 5.92x |
| Influencer/Social | 39.93 | 132.22 | 13.0% | 3.31x |
| Trade Promo & Sampling | 17.04 | 151.55 | 14.8% | 8.90x |

**Model fit:** R² = 74.1%, F-statistic = 13.6 (k=4 predictors, n=24 months)

A reallocation scenario — shifting Rs 3 Cr/year from Influencer/Social to Traditional Media, holding total budget constant — projects a **net incremental gain of ~Rs 20.01 Cr/year** in sales. Influencer/Social shows the lowest measured ROI in this dataset, but likely carries brand-building and word-of-mouth value the model doesn't fully capture — see Limitations below.

## Methodology

1. **Channel consolidation** — 5 raw channels merged into 4 (TV + Print → "Traditional Media") to avoid multicollinearity given only 24 monthly observations.
2. **Adstock transformation** — captures carryover effects: `Adstock(t) = Spend(t) + decay × Adstock(t-1)`, with a channel-specific decay rate (e.g., 0.5 for Traditional Media, 0.15 for Trade Promo — fast decay/immediate response).
3. **Regression** — monthly sales regressed on adstocked spend across all 4 channels using Excel's `LINEST`. Fit is verified transparently via a full actual-vs-predicted table rather than relying on LINEST's built-in stats block alone.
4. **Budget reallocation scenario** — applies each channel's derived ROI to a hypothetical spend shift, assuming linear, independent returns at the margin (a simplification — see Limitations).
5. **Primary research plan** — a Gen-Z survey/interview template (100+ respondents, 8–10 interviews) to validate positioning, using the Insight → Tension → Resolution framework from the Lakmé project.

## Data sources

| Figure | Value | Source |
|---|---|---|
| Dabur FY2025 total Advertising & Publicity spend | Rs 864.64 Cr | BestMediaInfo, 7-May-2025 |
| Dabur FY2025 consolidated revenue | Rs 12,563 Cr | Moneycontrol / Storyboard18, 7-May-2025 |
| A&P spend as % of revenue | ~7–8% | MatrixBCG, Dabur Marketing Strategy analysis |
| Digital media spend shift | >35% shifting to digital | MatrixBCG, Dabur Marketing Strategy analysis |

Everything else — channel-level splits, monthly spend/sales figures, adstock decay rates, seasonality — is an **analyst assumption** clearly flagged as such in the `Assumptions` and `Monthly Data` tabs of the workbook. Every hardcoded number carries its own source note.

## Repo contents

```
├── Dabur-Marketing-Mix-Model.pdf     # Full written report (exec summary, methodology, results, GTM plan, appendices)
├── Dabur_GenZ_MMM_Model.xlsx         # Full model, live and editable
├── Dabur_GenZ_MMM_Dashboard.pbix     # Power BI dashboard (built per the 'PowerBI Data Prep' tab in the workbook)
└── README.md
```

> Rename `Dabur_GenZ_MMM_Dashboard.pbix` above to match your actual filename before uploading.

### Workbook tabs

| Tab | Purpose |
|---|---|
| `Read Me` | Project objective + the same "this is simulated, not real Dabur data" disclaimer |
| `Assumptions` | Every input used in the model, tagged REAL / FORMULA / ASSUMPTION with source |
| `Monthly Data` | 24 months of channel spend + sales (Apr-24 to Mar-26) |
| `Adstock` | Adstock-transformed spend per channel per month |
| `MMM Regression` | LINEST regression output, coefficients, and full actual-vs-predicted diagnostics |
| `Budget Reallocation` | Editable what-if scenario — change the yellow "Shift" cells to test other allocations |
| `GTM Research Plan` | Template survey + interview guide for real primary research (not simulated — meant to be filled in) |
| `PowerBI Data Prep` | Guide for importing these tables into Power BI for dashboarding |

## Power BI dashboard

`Dabur_GenZ_MMM_Dashboard.pbix` visualizes the model output — channel contribution, ROI, and the budget reallocation what-if — built by importing the tables listed in the workbook's `PowerBI Data Prep` tab (Monthly Data, the Channel Contribution & ROI table, and the Budget Reallocation table). Open it in [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop) (free) to explore or edit the visuals. If you update the source workbook, refresh the data connections in Power BI to pull the latest numbers through.

## Limitations

- Channel-level spend is simulated and calibrated to real aggregates — not Dabur's actual internal numbers.
- 24 months is a small sample for a 4-variable regression; no formal confidence intervals in this lite model.
- Influencer/Social's measured ROI likely understates its true value — MMM struggles to capture brand equity and word-of-mouth versus the more immediately measurable response to trade promos and traditional media.
- The model assumes linear, independent returns; real media effects show diminishing returns at higher spend and cross-channel interaction (e.g., influencer content often drives search behavior).
- The regression's fitted intercept (~Rs 25.5 Cr/month, see `MMM Regression` tab) differs from the Rs 45 Cr baseline assumption used to generate the underlying simulated sales series — reported here for transparency.

## How to use

1. Open `Dabur_GenZ_MMM_Model.xlsx` and start with the `Read Me` tab.
2. Review `Assumptions` to see exactly what's real vs. modeled.
3. Edit the yellow cells in `Budget Reallocation` to test different spend shifts.
4. If replicating this methodology for another brand, use `GTM Research Plan` as a template and swap in real survey data.
