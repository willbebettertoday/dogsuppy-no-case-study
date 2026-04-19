# Dental Bright → Norway — Case Study

Three Google Search Ads campaigns to take DogSuppy's **Dental Bright** from €0 in Norway to **€1k/day at 1.5× ROAS** in four weeks, derived from 6 months of NL search term performance.

Prepared for **Chamzat Tambiyev / DogSuppy** · April 2026 · by Danil Sysenko.

---

## TL;DR

| Campaign | % of budget | NL benchmark ROAS | Rationale |
|---|---|---|---|
| **01 · Problem-Aware** | 30% | 2.87× | Symptom queries: `hund dårlig ånde`, `tannstein hund`. Cheapest CPC (€0.94 NL), hottest intent. |
| **02 · Solution-Aware** | 55% | 3.09× | Category queries: `tannpulver hund`, `tannpleie hund`. Largest volume + highest ROAS. |
| **03 · DSA Discovery** | 15% | target 1.5× | Dynamic Search Ads against `/no/dental-bright` + blog. Surfaces NO-specific queries our translation misses. |

**Model outcome:** €14,350 spend over 4 weeks → **€24,913 revenue**, blended **1.74× ROAS**. Week 4 steady state is 1.87×. Week 2 dips to 1.42× on purpose — we expand the keyword universe before we know what works, then cut losers in Week 3.

**Break-even check:** at €1k/day and CPC €1.45, we need CVR ≥ 3.5%. Baseline assumes 4.2% (a 25% haircut from NL 5.66%). Plan holds even if NO CVR lands 40% below NL.

---

## Repo contents

```
.
├── DogSuppy_NO_Case_Study.pptx      ← main deliverable (9 slides)
├── DogSuppy_NO_Case_Study.pdf       ← PDF version
├── analysis.ipynb                    ← full reproducible notebook
├── data/
│   └── nl_search_terms.csv          ← raw Google Ads search term report
└── output/
    ├── cluster_performance.csv      ← NL cluster summary (Spend/Revenue/ROAS/CPC/CVR)
    ├── aggregated_terms.csv         ← all 2,993 unique terms with cluster tags
    ├── norway_keyword_plan.csv      ← 33 Bokmål seed keywords across 3 campaigns
    ├── norway_negatives.csv         ← 14 account-level negative keywords
    ├── norway_4week_ramp.csv        ← week-by-week budget + revenue projection
    ├── cluster_performance.png      ← chart: spend share & ROAS by cluster
    └── ramp.png                     ← chart: 4-week budget vs revenue
```

---

## How I approached this

### 1. Understand the NL engine

Loaded the 59k-row Google Ads report, cleaned nulls and `#DIV/0!` entries, deduplicated identical terms appearing across ad groups, and aggregated spend / clicks / purchases / revenue per unique term. Final active set: **2,993 unique terms · €63,149 spend · €171,551 revenue · 2.72× blended ROAS · €58.83 AOV**.

### 2. Cluster by search intent

Rule-based regex classifier over Dutch search terms into six buckets. Hierarchy matters — own-brand is matched first, then competitor, problem-aware, solution-aware, broad dog context, and finally an `OTHER` catch-all.

| Cluster | Terms | Spend | Revenue | ROAS | CPC | CVR |
|---|---:|---:|---:|---:|---:|---:|
| Solution-Aware (tandpoeder, gebitsreiniging…) | 541 | €26,636 | €82,282 | **3.09×** | €1.22 | 6.5% |
| Problem-Aware (slechte adem, stinkt uit bek…) | 223 | €15,596 | €44,730 | **2.87×** | €0.94 | 4.8% |
| Other (mostly English DTC queries) | 1,467 | €7,535 | €15,465 | 2.05× | €1.67 | 5.5% |
| Broad dog context | 508 | €6,881 | €15,087 | 2.19× | €1.54 | 5.4% |
| Branded own (Beemzy) | 23 | €3,366 | €8,424 | 2.50× | €1.37 | 5.2% |
| Competitor (Plaque Off, Orozyme…) | 231 | €3,134 | €5,564 | 1.78× | €1.86 | 5.3% |

**Key finding: Solution + Problem together drive 67% of NL spend and 74% of NL revenue, both at 2.87×+ ROAS.** That's the template for Norway.

### 3. Decide what won't translate

- **Branded (Beemzy) is off the table.** It's DogSuppy's dental sub-brand in NL with €3k earned spend at 2.50× — but zero awareness in Norway at Day 1. Building brand queries is a Month 3+ exercise.
- **Competitor conquest is risky.** Worst-performing cluster in NL at 1.78× ROAS, and that's *with* NL brand trust and familiarity. In a cold market with no Trustpilot social proof yet, expect lower. Not one of the three.
- **Broad dog / Other.** These clusters exist because of messy match types in NL; in a fresh Norway build we tighten match types from Day 1 and avoid broad match on non-winning terms.

### 4. Build the Norway plan

Three campaigns mapped to the two winning NL clusters, plus a discovery campaign for unknown-unknowns:

- **Campaign 01 — Problem-Aware.** 15 phrase-match Bokmål keywords grouped into three ad families (breath / tartar / gums). Ad copy leans into symptom language: *"Hunden din stinker fra munnen? Naturlig pulver — ryddig ånde på 14 dager."*
- **Campaign 02 — Solution-Aware.** 16 phrase-match keywords across powder / paste-brush / general care. Ad copy leans product + proof: *"Tannpulver for hund — Dental Bright. Vet-utviklet. 4.6/5 fra 12 000 anmeldelser."*
- **Campaign 03 — DSA Discovery.** Dynamic Search Ads targeting `/no/`, `/no/dental-bright`, and dental-care blog. Google crawls the content and matches NO-specific queries manual translation misses. Weekly review: promote winners to Camp-1/2 as phrase match, add losers to the negatives list.

All three share the same 14-item account-level negatives list (`gratis`, `diy`, `katt`, `hest`, `veterinær`, `valp trening`, etc.) — cheap to add, saves €50+/week from low-intent leakage in a cold market.

### 5. Model the ramp

| Week | Daily budget | Expected ROAS | Daily revenue | What happens |
|---|---:|---:|---:|---|
| 1 | €150 | 1.50× | €225 | Launch tight on the 12 highest-intent keywords. |
| 2 | €300 | **1.42×** | €426 | Expand — add long-tail variants. ROAS dips as lower-intent terms enter the mix. This is the point. |
| 3 | €600 | 1.73× | €1,038 | Kill W2 losers, scale winners, tROAS bidding takes over. |
| 4 | €1,000 | **1.87×** | €1,870 | Steady state; DSA discoveries promoted to phrase match. |

The W2 dip is deliberate — without it, we have no signal about what doesn't work. Week 1 real data will calibrate the CPC and CVR assumptions immediately.

---

## Norway assumptions (adjustable with Week 1 real data)

| Metric | NL baseline | NO assumption | Delta | Rationale |
|---|---:|---:|---:|---|
| CPC | €1.22 | €1.45 | +20% | Nordic auction density; cold market means less competition advantage |
| CVR | 5.66% | 4.20% | −25% | No brand trust yet; improves W3-4 as social proof accrues |
| AOV | €58.83 | €62.00 | +5% | Nordic price index uplift, consistent with Active Ants fulfilment pricing |

---

## Day-1 operator backlog

If hired, my **Week 1 commitment** is one thing only:

**Daily pacing & ROAS Slack bot.** Python + Google Ads API + Slack webhook. At 09:00 CET it posts yesterday's spend, revenue, orders, and ROAS broken out by campaign. Red if any campaign is under 1.3× ROAS or pacing ±20% off budget. One screenshot per day that replaces a spreadsheet check. Build time: one evening. Pays for itself in Week 1 by catching a bad ad group before it burns a day of budget.

Everything else — search-term harvesting, feed generation, multi-market translation pipelines — waits until Week 4+. Automating things I don't have data for yet is how teams build shelfware.

---

## Reproducing the analysis

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook analysis.ipynb
```

The notebook loads `data/nl_search_terms.csv`, rebuilds the cluster classifier, and writes all CSVs to `output/`. Single-file, ~22 cells, runs in under 10 seconds on a laptop.

---

## One honest note

Everything downstream of Week 1 is a model built on NL→NO extrapolation. The Norway CPC and CVR assumptions are directional; the first seven days of real data will shift them. The plan is designed to be cheap to be wrong about — €150/day for Week 1, kill criteria explicit, DSA catching what translation misses. The target 1.5× ROAS has a safety buffer even if NO CVR comes in 40% below NL.

If we disagree on an assumption, I'd rather hear it now than debug it in Week 3.
