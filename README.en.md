<p align="center">
  <a href="README.md">简体中文</a> · <strong>English</strong>
</p>

<h1 align="center">Commodity Futures Research Skills</h1>
<p align="center"><strong>Research methods for AI agents working on fundamentals, price relationships and risk.</strong></p>
<p align="center">Supply & demand · Macro drivers · Basis & spreads · Delivery structure · Trade risk</p>
<p align="center">
  <a href="#skill-catalog"><img src="https://img.shields.io/badge/Skills-13-16477b" alt="13 Skills"></a>
</p>
<p align="center">
  <a href="#start-with-a-research-question">Research tasks</a> ·
  <a href="#input-and-output-examples">Examples</a> ·
  <a href="#skill-catalog">Skills</a> ·
  <a href="#install-and-start">Get started</a>
</p>

## Why these skills

Commodity research connects physical markets, price relationships and risk exposures on a consistent basis. Falling stocks at one location may not imply a national shortage; a profitable futures leg alone does not establish a profitable hedge.

This library turns research tasks into callable methods: define the product, region and horizon, check data and units, recompute key relationships, and develop evidence-based views with explicit invalidation conditions.

## Start with a research question

| Research question | Lead skill | Deliverable |
|---|---|---|
| Why do inventories and profits diverge? | Fundamental thesis | Supply–demand attribution, baseline and opposing scenarios, invalidation conditions |
| Is the hedged business profitable despite falling spot prices? | Basis | Physical and futures P&L, costs and residual exposure |
| Why do PTA and ethylene glycol perform differently? | Cross-commodity | Economic links, individual drivers, leg contributions and counter-evidence |
| How do policy, weather or FX affect commodities? | Macro / Weather / FX | Transmission channels, timing and verification indicators |
| Do fewer warehouse receipts imply delivery pressure? | Delivery structure | Deliverable supply, batch eligibility and carry-cost checks |
| Need to build a model from reports or update a workbook? | Balance-sheet Build / Maintain | Traceable inputs, explicit assumptions and calculation checks |

## How research works

1. **Define the scope**: product, region, contract, observation date and deliverable.
2. **Select methods**: choose a domain lead; share variables, units, periods and evidence across topics.
3. **Verify**: distinguish facts, assumptions and gaps; recompute key relationships and test opposing scenarios.
4. **Deliver a view**: state evidence, uncovered risks, invalidation conditions and the next data to check.

<p align="center">
  <img src="assets/skill-collaboration.png" width="920" alt="Domain research is the core; balance-sheet Build and Maintain provide optional model support">
</p>

**1 research guide + 10 domain skills + 2 supporting workflows.** The diagram shows task responsibilities. Balance-sheet workflows are used when modeling is needed. The guide currently routes to the 10 domain skills; invoke Build and Maintain directly by name.

## Input and output examples

These are **synthetic teaching examples already present in the skills**. Numbers illustrate the calculations.

### Spot loses money. What is the combined result?

**Input**: 100 tonnes of spot inventory fully hedged with an equal futures short, with matching location, grade and contract. Spot moves from 3,000 to 2,960 CNY/tonne; futures from 3,050 to 2,980. Total costs are 12 CNY/tonne.

| Calculation | Result |
|---|---:|
| Physical P&L | −4,000 CNY |
| Futures P&L | +7,000 CNY |
| Combined gross P&L | +3,000 CNY |
| Net P&L after costs | **+1,800 CNY** |

The output explains that basis strengthens from −50 to −20 CNY/tonne, generating gross P&L of 30 CNY/tonne. Actual work must also verify contract multipliers, quantities and costs. Source: [Basis](skills/commodity-basis/SKILL.md).

<details>
<summary>Show the calculation</summary>

```text
Physical P&L = (2,960 − 3,000) × 100 = −4,000 CNY
Futures P&L = (3,050 − 2,980) × 100 = +7,000 CNY
Net P&L = −4,000 + 7,000 − 12 × 100 = +1,800 CNY
```

</details>

### Does a higher product price mean a higher processing margin?

**Input**: product price of 7,200 CNY/tonne; feedstock consumption of 3 tonnes per tonne of product; feedstock price of 2,200 CNY/tonne; processing cost of 450 CNY/tonne of product. Only these cash flows are included. Product price then rises by 90 CNY/tonne and feedstock by 50, with processing cost unchanged.

**Output**: the margin proxy falls from **150 to 90 CNY/tonne of product**, a decline of 60. Feedstock changes must be weighted by consumption, rather than comparing price directions alone. Co-production requires additional revenue and cost inputs. Source: [Cross-commodity](skills/commodity-cross-commodity/SKILL.md).

<details>
<summary>Show the calculation</summary>

```text
Initial margin proxy = 7,200 − 3 × 2,200 − 450 = 150 CNY/tonne of product
Change = 90 − 3 × 50 = −60 CNY/tonne of product
New margin proxy = 150 − 60 = 90 CNY/tonne of product
```

</details>

## Skill catalog

### Research guide

| Skill | Purpose |
|---|---|
| [Research guide](skills/commodity-research-guide/SKILL.md) | Method selection, terminology, and cross-topic coordination |

### Fundamentals & drivers

| Skill | Purpose |
|---|---|
| [Fundamental thesis](skills/commodity-fundamental-thesis/SKILL.md) | Fundamentals, inventories, profits, and falsifiable theses |
| [Oils](skills/commodity-oils/SKILL.md) | Soybean, palm, and rapeseed oil fundamentals and physical markets |
| [Macro](skills/commodity-macro/SKILL.md) | Macro and policy transmission to commodity demand and costs |
| [Weather](skills/commodity-weather/SKILL.md) | Weather effects on production, logistics, and timing |
| [FX](skills/commodity-fx/SKILL.md) | Currency drivers, payment exposures, and hedging costs |

### Pricing, structure & risk

| Skill | Purpose |
|---|---|
| [Basis](skills/commodity-basis/SKILL.md) | Physical pricing, basis trades, and combined physical–futures P&L |
| [Metals spreads](skills/commodity-metals-spread/SKILL.md) | Metals calendar spreads, carry costs, and import parity |
| [Delivery structure](skills/commodity-delivery-structure/SKILL.md) | Warehouse receipts, deliverable supply, and contract structure |
| [Cross-commodity](skills/commodity-cross-commodity/SKILL.md) | Relative value, processing margins, co-products, and substitution |
| [Trade risk](skills/commodity-trade-risk/SKILL.md) | Performance, credit, ownership, settlement, and funding risk |

### Supporting workflows: balance sheets

| Skill | Purpose |
|---|---|
| [Balance-sheet build](skills/commodity-balance-sheet-build/SKILL.md) | Build a supply–demand model from reports, historical data, and assumptions |
| [Balance-sheet maintain](skills/commodity-balance-sheet-maintain/SKILL.md) | Update existing balances and verify periods, capacity, and formula dependencies |

## Install and start

Get the repository:

```bash
git clone https://github.com/AY-kkk/commodity-skill.git
```

Copy the required **complete skill folders** from `commodity-skill/skills/` into your agent’s skill directory. Preserve `SKILL.md`, `references/` and any `agents/` metadata. Use the installation path configured for your client; review existing folders before replacing them.

Start a new task with a question, source materials and cutoff date:

```text
Use $commodity-fundamental-thesis to analyze the monthly reports I provide.
Product: methanol. Scope: national. Observation cutoff: as stated in the reports.
Explain the divergence between inventories and profits. Separate facts from
assumptions and state counter-evidence and invalidation conditions.
```

Use `$commodity-research-guide` when unsure which method to choose. Skill instructions are primarily in Chinese. Data retrieval, PDF and Excel tasks require appropriate tools in the client.

## Repository structure

```text
commodity-skill/
├── README.md                         # Chinese entry
├── README.en.md                      # English
├── assets/skill-collaboration.png     # Research collaboration diagram
└── skills/
    ├── commodity-research-guide/      # Guide and references
    ├── commodity-fundamental-thesis/  # One domain skill
    ├── commodity-*/                   # Other domain skills
    ├── commodity-balance-sheet-build/ # Build balances
    ├── commodity-balance-sheet-maintain/ # Maintain balances
    ├── BUILD_MANIFEST.json            # Original research pack build record
    └── capability-destinations.json   # Original capability mapping
```

## Sources and boundaries

Each skill retains source references and scope limits. Keep historical teaching parameters separate from current market inputs; verify current rules, contracts and costs as of the research date. State how research conclusions can be tested. Respect the user’s file-editing authorization and obtain consent before creating files or worksheets.

<details>
<summary>Build provenance and metadata scope</summary>

Metadata for the original guide and 10 domain skills records [cangjie-tools v2.5.0](https://github.com/kangarooking/cangjie-skill) as the generating tool. `BUILD_MANIFEST.json` and `capability-destinations.json` cover those 11 entrypoints. The two balance-sheet workflows are later additions. The tool version is not this library’s version.

</details>
