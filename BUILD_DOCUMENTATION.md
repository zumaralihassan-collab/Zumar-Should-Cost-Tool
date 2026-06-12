# Should Cost AI — Technical Build Documentation

> A complete walkthrough of how this Procurement & Supply Chain Intelligence Suite was conceptualized, architected, built, and deployed.

**Author:** Mohammed Zumar Ali Hassan
**Program:** MS Supply Chain Management (STEM), The University of Texas at Dallas
**Live demo:** https://zumaralihassan-collab.github.io/Zumar-Should-Cost-Tool/
**Repository:** https://github.com/zumaralihassan-collab/Zumar-Should-Cost-Tool

---

## 1. Project Overview

### The problem statement
Procurement and sourcing managers are routinely asked to negotiate prices on products for which they have neither a clean bill of materials nor a credible cost benchmark. Engineering teams hand procurement an incomplete specification — a sketch, a part number, a brief description — with no breakdown of what should drive the cost. Without an independent cost anchor, the buyer's negotiation leverage collapses to a 2–3% concession at best. With a defensible should-cost model, the same negotiation typically yields 8–15% savings.

### What this tool does
Should Cost AI is an interactive, browser-based procurement intelligence suite that accepts a free-form product description (e.g., *"red sand brick 230×110×75 mm"*), classifies the product across 12+ industries, proposes every relevant cost driver from a built-in knowledge base, applies regional/volume/quality multipliers, and produces a unit cost, an order total, a visual breakdown, and a six-step negotiation playbook.

### Scope
The deployed version is a fully functional proof-of-concept and a UX target for an enterprise build. It demonstrates the architecture and user experience that would carry over to a production system integrated with SAP S/4HANA, Ariba, and live commodity price feeds.

---

## 2. Architecture — The Five-Stage Pipeline

The entire tool is structured as a five-stage pipeline. The same architecture would scale to enterprise data sources by swapping the inputs and persistence layer; the logical flow stays the same.

```
┌─────────────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────────────┐   ┌──────────────┐
│  ① INPUT    │ → │ ② ANALYZER   │ → │ ③ COST       │ → │ ④ INTELLIGENCE   │ → │ ⑤ OUTPUT     │
│             │   │              │   │   ENGINE     │   │   LAYER          │   │              │
│ Product     │   │ Keyword      │   │ Parameter    │   │ Insights         │   │ Unit cost    │
│ Region      │   │ classifier   │   │ engine       │   │ Dashboard        │   │ Order total  │
│ Volume      │   │ Template     │   │ Sensitivity  │   │ AI Strategist    │   │ Charts       │
│ Quality     │   │ loader       │   │ layer        │   │ Chart renderer   │   │ Excel export │
│ Quantity    │   │ Multipliers  │   │ Margin       │   │ Recommendations  │   │ Playbook     │
│ Chat query  │   │ Intent router│   │ Currency FX  │   │                  │   │              │
└─────────────┘   └──────────────┘   └──────────────┘   └──────────────────┘   └──────────────┘
        ↑                                                                                │
        └────────────────── USER FEEDBACK LOOP (instant recalculation) ──────────────────┘
```

### Stage 1 — Input
The procurement manager describes what they're sourcing. Free-form name, industry category, region, production volume, quality tier, and order quantity. The chatbot tab accepts natural-language strategy questions.

### Stage 2 — AI Analyzer
A deterministic keyword classifier matches the product description to one of the built-in templates. The cost-driver library loads the relevant 20–40 parameters per template. Context multipliers adjust labor, utility, facility, equipment, and material rates based on region/volume/quality. The intent router (for the chatbot) decides whether the user wants explanation, chart, or both.

### Stage 3 — Cost Engine
The parameter engine multiplies qty × rate for every line item. The sensitivity layer applies live what-if adjustments (±30% on materials, labor, energy). Subtotal plus supplier margin gives the unit should-cost. Currency conversion is applied based on user choice across INR, USD, EUR, GBP, AED, and SAR.

### Stage 4 — Intelligence Layer
The insights engine generates strategic recommendations including Kraljic positioning and top-cost-driver identification. The dashboard and supply chain analytics modules surface KPIs, supplier scorecards, ABC analysis, an EOQ optimizer, and a tariff impact simulator. The AI Strategist bot answers procurement questions from a 27-topic knowledge base and renders charts on demand.

### Stage 5 — Output
Live unit cost and total order cost in the chosen currency. Visual cost breakdown with category legend. Six-step negotiation playbook with target margin, walk-away point, and contract clauses. Excel export of the full should-cost report. Scenarios saved for side-by-side supplier comparison.

### The feedback loop
The user iterates continuously — adjusts a rate, changes a region, runs a what-if, saves a scenario — and the entire pipeline recalculates instantly. This is the difference between a one-shot report and an interactive intelligence tool.

---

## 3. Technology Stack

The architecture is deliberately a *no-backend, no-build-step single-file application*. Every choice below was made to optimize for portability, zero hosting cost, instant load time, and resilience.

### Frontend layer

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Structure | HTML5 (single `index.html`, ~118 KB, 1,444 lines) | One file = zero deployment complexity. Anyone can open it locally. |
| Styling | Tailwind CSS via CDN | Utility-first framework — saves writing custom CSS for ~95% of the layout. |
| Custom styling | Small `<style>` block | Gradient header, chat bubbles, Kraljic quadrant colors, watermark, print styles. |
| Logic | Vanilla JavaScript (no React/Vue/Angular) | ~1,000 lines for calculator, classifier, dashboard, chatbot, insights. No build step needed. |

### Visualization layer

| Library | Version | Purpose |
|---------|---------|---------|
| **Chart.js** | 4.4.1 | Every chart in the app — cost-breakdown doughnut, dashboard Pareto, savings bar chart, raw-material trend lines, supplier bubble chart, ABC analysis, geographic bar, lead-time chart, and the chatbot's on-demand pie/line/scatter/bar/pareto visualizations. |

### Export layer

| Library | Version | Purpose |
|---------|---------|---------|
| **SheetJS (xlsx)** | 0.18.5 | Generates `.xlsx` downloads for should-cost reports and dashboard exports. |

### Persistence layer

| Mechanism | Purpose |
|-----------|---------|
| `localStorage` | Saved scenarios persist across browser sessions. Single-user only by design (v1). |

### Icons

| Mechanism | Purpose |
|-----------|---------|
| Inline SVG | All icons (lightning bolt, gear, charts) are hand-drawn inline SVG. No icon library dependency. |

### Hosting / deployment

| Service | Role |
|---------|------|
| **GitHub** | Source control + collaboration |
| **GitHub Pages** | Static file hosting — free, fast, served directly from the repository's main branch |

### Build tools

**None.** No `npm install`, no Webpack, no Vite, no Babel, no PostCSS. The HTML file is the application. Open it in any browser and it runs.

### Why this stack?

1. **Portability** — The entire application is a single HTML file. You can email it, store it on a USB drive, or open it from any folder.
2. **Zero hosting cost** — GitHub Pages serves the file for free.
3. **Resilience** — No backend means no server downtime, no database failure, no API rate limits.
4. **Instant load** — All assets load from public CDNs (Cloudflare, jsDelivr). Page loads in under 2 seconds on any connection.
5. **Demonstrable** — Recruiters and interviewers can interact with the live tool without any setup, account, or login.

---

## 4. Development Approach — AI-Assisted Software Engineering

### Honest disclosure
This tool was conceptualized, designed, and architected by me. The procurement frameworks, cost-driver libraries, Kraljic logic, EOQ formulas, and chatbot knowledge base were specified by me. The line-by-line JavaScript and HTML was written through prompt-engineered collaboration with **Claude (Anthropic)** — used as a coding pair-programmer in the same way modern engineering teams use GitHub Copilot, Cursor, or Claude Code.

### What I personally contributed
- **The product idea** — Should-cost as a category, identified from procurement pain points at Amazon, Cristal Constructions and Nykaa
- **The architecture** — Five-stage pipeline; 5-tab module layout; feedback loop
- **The cost-driver knowledge base** — Every parameter list for the 6 product templates (brick, perfume, t-shirt, PCBA, plastic bottle, generic) reflects manufacturing economics I learned through coursework and prior work
- **The chatbot knowledge base** — All 27 procurement topics with strategies (Kraljic, EOQ, RFQ/RFP/RFI, TCO, negotiation, supplier risk, forecasting, tariffs, SRM, Lean/Six Sigma, contracts, etc.) were curated from real procurement frameworks
- **The Kraljic positioning logic, EOQ formulas, Safety Stock formula, Tariff Simulator regression** — all from procurement and operations research methodology
- **The 6-step negotiation playbook** — distilled from real sourcing strategies I've executed
- **The UX choices** — tab layout, sensitivity sliders, "About the Creator" modal, watermark
- **The deployment strategy** — GitHub Pages, single-file approach

### What AI provided
- Translation of my design specifications into syntactically correct JavaScript and HTML
- Suggested specific libraries (Tailwind CDN, Chart.js, SheetJS) appropriate to the no-backend constraint
- Debugged JavaScript issues that arose during iteration

### Why this matters
In 2026, software is increasingly built through human-AI collaboration. The skill being demonstrated here is **prompt engineering at a domain-expert level** — the ability to specify requirements precisely, evaluate AI output critically, and iterate toward a working product. This is the modern equivalent of using StackOverflow, library documentation, or a senior engineer for syntax help — except faster.

### Tools used in development
- **Claude (Anthropic)** — primary code generation and debugging pair
- **GitHub web editor + Upload Files flow** — version control and deployment
- **Chrome browser** — testing
- **macOS Finder + VS Code** — local file management and inspection

---

## 5. File Structure

```
Zumar-Should-Cost-Tool/
├── index.html                # The entire application (118 KB, 1,444 lines)
├── README.md                 # Project description and quick links
└── BUILD_DOCUMENTATION.md    # This file
```

That's it. One application file, two documentation files. The minimalism is intentional.

---

## 6. How Each Module Works

### Module 1 — Should Cost Calculator
The core engine. The user types a product name and selects context. A keyword classifier (`detectTemplate()` function) matches against a `KEYWORD_MAP` array to pick the right template from the `TEMPLATES` object. Context multipliers from `REGION_MULT`, `VOLUME_MULT`, and `QUALITY_MULT` adjust the rates. The `recalc()` function multiplies qty × rate across every line, applies sensitivity sliders, adds margin, converts currency, and updates the doughnut chart via Chart.js.

### Module 2 — Executive Dashboard
Hardcoded sample data (`DASH_CATEGORIES`, `DASH_REGIONS`, `DASH_SAVINGS`, `DASH_TREND`, `SUPPLIERS`) representing a $24.8M procurement portfolio. The dashboard renders 7 charts including a Pareto spend chart with cumulative-percent overlay, a regional doughnut, a savings-vs-target bar, a multi-line raw-material trend, a supplier bubble chart, a sortable scorecard table, and a 12×5 risk heatmap rendered as a CSS grid with conditional cell coloring.

### Module 3 — Supply Chain Analytics
Interactive Kraljic Matrix with sample items in each quadrant. ABC analysis chart showing percent-of-SKUs vs percent-of-spend. Geographic sourcing footprint with single-country risk flag. **EOQ & Safety Stock Optimizer** — a live calculator implementing `EOQ = √(2DS/H)`, `Safety Stock = Z × σ × √LT`, and `Reorder Point = avg daily demand × LT + SS`. **Tariff Impact Simulator** — multiplies tariff rate by import value for direct cost increase, and uses an elasticity parameter to forecast volume decline.

### Module 4 — AI Procurement Strategist (Chatbot)
A 27-topic deterministic knowledge base (`KB` array). Each topic has trigger keywords, a title, an HTML body, a strategy callout, and an optional chart spec. The `respondTo()` function routes user queries through three checks: (1) is it a question prefix like "explain"/"what is"/"how do" → search KB; (2) does it match a visualization intent ("pie", "line", "pareto", etc.) and a dataset name → render chart; (3) fallback to general KB lookup. The chart engine supports pie/doughnut, line, scatter, bar, and pareto types using Chart.js.

### Module 5 — Insights & Recommendations
The `initInsights()` function reads the current `currentParams` array, sums category totals, calculates ratios (material %, labor %, logistics %, overhead %), and generates strategic recommendations including:
- Kraljic positioning (Leverage / Strategic / Bottleneck / Routine based on cost composition)
- Top cost driver identification with quantified savings opportunity
- Margin pressure flag if supplier markup exceeds market norms
- Logistics optimization recommendation if logistics > 12%
- Low-cost-country sourcing recommendation if labor > 20% in a high-wage region
- Overhead reduction levers (VMI, consignment, tooling absorption)
- A 6-step negotiation playbook with computed target margin, walk-away point, and contract clauses

---

## 7. Future State — Enterprise Production Architecture

For a Tesla-scale build (e.g., the power distribution team's 10 commodity families, hundreds of suppliers, multi-region sourcing), the five-stage pipeline stays the same — but every tier upgrades:

| Tier | v1 (current) | v2 (enterprise) |
|------|--------------|----------------|
| Input | User form | SAP S/4HANA + Ariba via OData APIs |
| Knowledge base | In-code templates | Versioned database (Snowflake / Databricks) |
| Cost engine | Browser JavaScript | Python FastAPI service |
| Intelligence | Static logic | ARIMA + Prophet + XGBoost ML pipeline |
| Frontend | Single HTML file | Next.js + React + Recharts |
| Persistence | localStorage | PostgreSQL + Redis cache |
| Auth | None | OAuth/SAML SSO via Azure AD or Okta |
| Hosting | GitHub Pages | AWS / Vercel / internal Kubernetes |
| Refresh | Manual | Nightly batch + intraday commodity feeds |

### Phased rollout (estimated 6–12 months)

**Phase 1 — Data Foundation (8 weeks)**
Land SAP S/4HANA and Ariba historical data into Snowflake. Build supplier master, spend cube, commodity price feed. No UI yet — analysts use SQL and Power BI.

**Phase 2 — Should-Cost Engine (10 weeks)**
Build Python cost engine as FastAPI service. Migrate templates from in-code to versioned database records. Add EOQ, safety stock, and tariff simulator modules. Expose REST endpoints.

**Phase 3 — Intelligence (10 weeks)**
ARIMA / Prophet / XGBoost models for cost forecasting per commodity. Should-cost vs actual variance engine. Supplier mix optimizer (linear programming via PuLP or OR-Tools).

**Phase 4 — UI (12 weeks)**
Rebuild front-end in Next.js with same look but live data. Add SSO, RBAC, scenario approval workflows, audit trail, comments.

**Phase 5 — Adoption (ongoing)**
Train the category teams, tune models against negotiated outcomes, expand to adjacent commodity families.

---

## 8. Academic Learnings & Reflections

### Procurement domain learnings
Building this tool reinforced how **frameworks become operational** when translated into software. The Kraljic Matrix, EOQ formula, Safety Stock equation, and ABC analysis are textbook concepts in every supply chain program — but coding them into a working application forced me to confront edge cases (e.g., what Kraljic quadrant applies when material < 35% AND labor > 30%?) that classroom case studies don't surface.

### Software engineering learnings
- **Architecture clarity beats code volume.** The five-stage pipeline took less than an hour to design but defined every subsequent technical choice.
- **Constraints drive elegant solutions.** Choosing "no backend, no build step" eliminated entire categories of complexity (no DevOps, no environment variables, no deployment pipelines).
- **AI-assisted development is a force multiplier for domain experts.** The same project would have taken me weeks in vanilla JavaScript without AI; with prompt engineering, the working prototype took days.

### Methodological learnings
- **Should-cost is procurement's most underused negotiation lever.** Walking through every line item in the build forces a buyer to think about what *actually* drives cost — which is the entire point of the negotiation.
- **The user experience of "instant recalculation" changes how analysts think.** When the unit cost updates the moment you move a slider, you stop asking "what if" and start exploring the cost space.

### Limitations of v1
- Single-user (localStorage doesn't sync across devices)
- Static templates (categories are hardcoded; can't add new ones without editing the source file)
- No actual machine learning — the "AI classifier" is a deterministic keyword matcher
- No data validation against real supplier quotes
- The chatbot's knowledge base is curated, not generative — it can't answer arbitrary procurement questions

### What I would do differently
- Build the database schema first (suppliers, categories, parameters, multipliers) before writing any UI
- Use TypeScript instead of vanilla JavaScript for type safety on a project this large
- Add unit tests for the cost calculations
- Implement actual NLP for the chatbot using a small LLM (e.g., Claude Haiku API)

---

## 9. Acknowledgments

### Inspiration drawn from
- **Procurement work at Nykaa** (Sourcing Analyst Intern, Jan – May 2021) — first exposure to Kraljic-driven sourcing strategy; delivered $300K+ in savings
- **Supplier risk framework at Cristal Constructions** (Supply Chain Analyst, May 2021 – Apr 2023) — risk heatmap concept; delivered $720K in savings
- **KPI dashboards at Amazon** (Operations & Logistics Analyst, May 2023 – Aug 2024) — dashboard design pattern; unlocked $200K in annual savings
- **Inventory optimization research at UT Dallas** (Supply Chain Research Assistant, Jun 2025 – Present) — EOQ and Safety Stock formulas; reduced inventory costs by 22%
- **Tariff war regression research** (Spring 2026 project) — Tariff Impact Simulator logic

### Tools and libraries gratefully used
- **Anthropic Claude** — AI coding partner
- **Tailwind CSS** — utility-first styling framework
- **Chart.js** — open-source charting library
- **SheetJS** — open-source spreadsheet library
- **GitHub Pages** — free static hosting

### Academic guidance
This project was completed as a portfolio piece during my MS Supply Chain Management (STEM) program at The University of Texas at Dallas. The build documentation was added at the recommendation of my faculty advisor to demonstrate transparency about the development process and the tech stack — an academic and professional best practice.

---

## 10. Contact

**Mohammed Zumar Ali Hassan**
MS Supply Chain Management (STEM), UT Dallas

📧 mohammedzumarali.hassan@utdallas.edu
📞 414-317-5496
🔗 [linkedin.com/in/zumarali15](https://linkedin.com/in/zumarali15)

---

© 2026 Mohammed Zumar Ali Hassan — All rights reserved.
*This documentation is part of the Should Cost AI project portfolio.*
