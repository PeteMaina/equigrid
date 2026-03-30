# EquiGrid

**Household energy vulnerability intelligence for equitable tariff design.**

EquiGrid is a regulatory decision-support platform built for the EPRA Hackathon 2026 — Challenge 1: Optimal Tariff Design for Energy Affordability & Equity.

The core problem it solves: Kenya's residential electricity tariff classifies ~8.8 million households almost entirely by historical consumption. That single variable cannot tell you whether a household is poor, whether they live in Wajir or Westlands, or whether they have dependents with essential energy needs. The result is a system that regularly misclassifies the people it is trying to protect — and gives regulators no way to test whether a proposed tariff change will actually help before it is gazetted.

EquiGrid changes that.

---

## What it does

**Vulnerability Profiler**
Builds household profiles from KNBS 2019 Census data, EPRA tariff schedules, and World Bank county-level poverty assessments. A K-means clustering model segments households into archetypes and assigns each a Vulnerability Score (0–100) using poverty rate, household size, county, dwelling type, and rural/urban classification — not consumption alone.

**Tariff Scenario Simulator**
An analyst configures a proposed tariff — adjusting lifeline thresholds, subsidy bands, cross-subsidy rates — and the simulator returns an immediate equity impact projection across all 47 counties: proportion of vulnerable households protected, misclassification shift vs current structure, and cost recovery implications.

**AI Regulatory Brief Generator**
Simulation output feeds into an Anthropic API inference layer that generates a structured regulatory memo in EPRA's submission format — equity findings, scenario comparison, county-level highlights, and recommended parameters. The gap between analysis and a ready-to-submit document is closed automatically.

---

## Stack

| Layer | Tools |
|---|---|
| Backend | FastAPI · Python · scikit-learn · pandas · PostgreSQL |
| Frontend | React · Vite · Recharts |
| AI |  API (Claude Anthropic or OpenAI) |
| Deployment | Render (API) · Netlify, vercel (frontend) |

---

## Data sources

All open-access:

- **KNBS 2019 Kenya Population and Housing Census** — household size, dwelling type, county distribution, rural/urban split
- **Kenya Poverty Report 2022** (KNBS / World Bank) — county-level poverty rates and income proxies
- **EPRA Energy and Petroleum Statistics FY 2023/24 + Biannual 2024/25** — current tariff bands, domestic customer counts, consumption breakdown
- **KPLC connection data** — embedded in EPRA Statistics Reports

Synthetic household profiles are generated using statistical distributions derived from these sources. See `/data/README.md` for exact download links and extraction notes.

---


## Build timeline

This project is being built live at the EPRA Hackathon, 20–23 April 2026.

| Day | Target |
|---|---|
| Day 1 | Data pipeline, household profiling model, core FastAPI scaffolding |
| Day 2 | Simulation API complete, React dashboard connected, county heat map live |
| Day 3 | AI brief generator integrated, full demo path tested |


---

## Scalability

The vulnerability scoring engine requires only census-equivalent public data to operate. The same architecture applies directly to Uganda, Tanzania, Rwanda, and Ethiopia all EAPP member states. Kenya is the reference implementation.

---

## Team

**Peter Maina** — Software Engineer, Nairobi
[github.com/petemaina](https://github.com/petemaina) · [mainapeter.netlify.app](https://mainapeter.netlify.app) · [linkedin.com/in/petermaina-](https://linkedin.com/in/petermaina-)

**Kihara Chege** — Full-Stack Engineer & ML Systems Developer
[linkedin.com/in/kihara-chege-3b2198321](https://linkedin.com/in/kihara-chege-3b2198321/)

---

Built for the EPRA Research Week Hackathon 2026 · Challenge 1: Optimal Tariff Design for Energy Affordability & Equity
 