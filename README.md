# Commodity Skills

13 agent skills for commodity research and supply–demand modeling: a research guide, ten domain specialists, and two workflows for building and maintaining balance sheets.

![How the commodity skills collaborate](assets/skill-collaboration.png)

## How they work together

Choose the deliverable first. Domain skills define the economic logic and interpret results; workflow skills organize evidence, implement models, and verify calculations. Share variables, units, periods, sources, and assumptions between them.

| Task | Workflow | Domain support |
|---|---|---|
| Build a balance sheet from PDF reports | `commodity-balance-sheet-build` | Fundamental thesis, or Oils for vegetable oils |
| Update an existing workbook | `commodity-balance-sheet-maintain` | Relevant specialist when definitions or assumptions change |
| Explain a market move or test a thesis | Relevant domain skill | Build or Maintain when data work is needed |
| Select a research method or coordinate topics | `commodity-research-guide` | Specialists selected for the deliverable |

Build hands an established model to Maintain for subsequent updates. These are task handoffs, not an automatic multi-agent runtime.

## Skills

| Skill | Purpose |
|---|---|
| [Research guide](skills/commodity-research-guide/SKILL.md) | Method selection, terminology, and cross-topic coordination |
| [Build](skills/commodity-balance-sheet-build/SKILL.md) | Reports → historical data → explicit assumptions → validated model |
| [Maintain](skills/commodity-balance-sheet-maintain/SKILL.md) | Update existing inputs, periods, capacity histories, and formula dependencies |
| [Fundamental thesis](skills/commodity-fundamental-thesis/SKILL.md) | Supply–demand identities, inventory analysis, and falsifiable theses |
| [Oils](skills/commodity-oils/SKILL.md) | Soybean, palm, and rapeseed oil balances and physical-market analysis |
| [Macro](skills/commodity-macro/SKILL.md) | Policy and macroeconomic transmission to demand and costs |
| [Weather](skills/commodity-weather/SKILL.md) | Weather effects on production, logistics, and timing |
| [FX](skills/commodity-fx/SKILL.md) | Currency exposure and hedging costs |
| [Basis](skills/commodity-basis/SKILL.md) | Spot pricing and combined physical–futures P&L |
| [Trade risk](skills/commodity-trade-risk/SKILL.md) | Credit, ownership, settlement, and funding risk |
| [Metals spreads](skills/commodity-metals-spread/SKILL.md) | Calendar spreads, carry costs, and import parity |
| [Delivery structure](skills/commodity-delivery-structure/SKILL.md) | Deliverable supply, warehouse receipts, and contract structure |
| [Cross-commodity](skills/commodity-cross-commodity/SKILL.md) | Processing margins, co-products, substitution, and relative value |

## Use

Copy the required folders from `skills/` into your agent's skill directory. Keep each `SKILL.md`, its references, and any `agents/` metadata together. Review existing installations before replacing them. Skill instructions are primarily in Chinese.

Example requests:

```text
Use $commodity-balance-sheet-build with $commodity-fundamental-thesis
to build a monthly PTA balance from these reports. Separate historical
observations from forecast assumptions and cite the source of each input.

Use $commodity-balance-sheet-maintain to update this workbook from the
latest reports. Preserve its structure and verify downstream calculations.
```

Work within the requested scope. Distinguish facts, assumptions, and missing data; confirm new files or worksheets; preserve existing formulas where required; verify the saved workbook.

Source references remain with each skill. `skills/BUILD_MANIFEST.json` records the original 11-skill research pack; Build and Maintain are separate additions.
