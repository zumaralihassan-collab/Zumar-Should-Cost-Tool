# 🎓 AI Procurement Knowledge Base

## 27+ Frameworks Embedded in the Strategist Chatbot

### **Sourcing Strategy & Planning**

#### 1. **Kraljic Portfolio Matrix**
- **What:** Segment all purchases on two axes: **Profit Impact** (how material) × **Supply Risk** (vulnerability)
- **Output:** 4 quadrants with different sourcing strategies
  - **Strategic** (high/high): Long-term partnerships, dual sourcing, joint cost-down workshops, NPI collaboration
  - **Bottleneck** (low/high): Buffer stock, qualify alternates, design-out, reduce dependency
  - **Leverage** (high/low): Competitive bidding, e-auctions, exploit buying power, aggressive cost reduction
  - **Routine** (low/low): Automate, P-card, catalog buying, consolidate suppliers
- **Real-world impact:** Zumar used this at Nykaa to segment sourcing spend and deliver **$300K+ in savings**

#### 2. **Category Management**
- **Cycle:** Understand demand → Analyze supply market → Assess current state → Develop strategy → Execute → Measure
- **Typical result:** 8–12% cost savings per category per year
- **Cadence:** Annual strategy refresh with quarterly business reviews

#### 3. **ABC Analysis (Pareto 80/20)**
- **A items** (~10% of SKUs, ~70% of spend) → daily management
- **B items** (~20% of SKUs, ~20% of spend) → weekly reviews
- **C items** (~70% of SKUs, ~10% of spend) → monthly or auto-replenishment
- **Benefit:** Differentiate effort and inventory policy by business impact

#### 4. **Make-vs-Buy Analysis**
- **Buy when:** Vendor has scale, it's non-core IP, demand is volatile, or internal TCO is high
- **Make when:** Core IP, vendor margins excessive, lead times unacceptable, or need tight quality control
- **Method:** NPV comparison over 5 years including capex, ramp-up, exit costs
- **Refresh cadence:** Every 2–3 years as market conditions shift

#### 5. **Multi-sourcing Strategy**
- **Single source** → Max leverage, lowest TCO at scale, but highest risk
- **Dual source** (60/40 or 70/30 split) → Standard for Strategic quadrant items
- **Multi-source** (3+) → For Bottleneck items and during geopolitical instability
- **Best practice:** Always maintain a qualified Plan B even if you buy 100% from Plan A

---

### **Analysis & Costing**

#### 6. **Should-Cost / Clean-Sheet Analysis**
- **Definition:** Build cost from first principles (materials, labor, energy, equipment depreciation, facility, overhead, margin) instead of accepting a supplier quote
- **Power:** Exposes hidden cost even when engineering hasn't given full specs
- **Typical finding:** Pure unit price misses 8–15% of true cost
- **Tool:** This entire Should Cost AI app is a should-cost engine

#### 7. **Total Cost of Ownership (TCO)**
- **Formula:** Acquisition + Operating + Quality + Risk + End-of-life
- **Typical breakdown:** Unit price = 30–60%, everything else = 40–70%
- **Components:** Freight, duty, financing, FX, defect cost, downtime, rework, switching cost, disposal, ESG penalties
- **Benchmark:** Building a TCO model for Strategic suppliers exposes 8–15% hidden cost

#### 8. **Spend Analysis & Spend Cube**
- **Dimensions:** Category × Supplier × Business Unit × Region × Cost Center
- **Insights:** Find tail spend to consolidate, maverick spend to eliminate, risk concentration
- **Typical finding:** 80% of suppliers = 20% of spend; consolidate the tail
- **Cadence:** Quarterly refresh; act on top 3 anomalies before next quarter

#### 9. **Supplier Risk Assessment**
- **Six dimensions:** Financial (Altman Z), Operational (capacity/dependency), Geopolitical, Cyber, ESG, Single-source
- **Output:** Risk register with probability × impact matrix
- **Control:** Business continuity plan (BCP) per Strategic supplier
- **Real-world:** Zumar built this framework at Cristal across 10+ vendors → **$720K savings** + **95% continuity**

#### 10. **Supplier Scorecard**
- **Standard weights:** 40% Quality (PPM, RMA) · 30% OTIF · 20% Cost vs benchmark · 10% Sustainability
- **Cadence:** Monthly reporting with traffic lights
- **Outcome:** Visibility alone improves supplier performance ~15%
- **Best practice:** Share with suppliers; it drives behavioral change faster than negotiation

---

### **Procurement Operations**

#### 11. **Economic Order Quantity (EOQ)**
- **Formula:** EOQ = √(2DS / H) where D = annual demand, S = order cost, H = holding cost/unit/year
- **Example:** D=50,000, S=$120, H=$2.5 → EOQ ≈ 2,191 units/order
- **Benefit:** Minimizes total of ordering + holding cost
- **Constraint:** Works best for stable demand, routine items

#### 12. **Safety Stock & Service Level**
- **Formula:** SS = Z × σ × √LT where Z is based on target service level
- **Z-scores:** 90% → 1.28, 95% → 1.645, 97.5% → 1.96, 99% → 2.33
- **Trade-off:** Higher service level = more cash tied up in inventory
- **Best practice:** Set differentiated SLs by ABC class (A=98%, B=95%, C=90%)

#### 13. **Reorder Point (ROP)**
- **Formula:** ROP = (Average Daily Demand × Lead Time) + Safety Stock
- **Purpose:** When inventory hits ROP, place next order
- **Benefit:** Prevents stockouts while minimizing excess inventory

#### 14. **Just-In-Time (JIT)**
- **Concept:** Pull material to point-of-use only when needed
- **Requirement:** Reliable lead times (low σ), short distances, trusted suppliers
- **Trade-off:** Zero inventory ↔ High disruption risk
- **Suitability:** Works in stable demand; hybrid JIT + buffer in volatile periods

#### 15. **Vendor-Managed Inventory (VMI)**
- **Model:** Supplier owns inventory at buyer's site until consumption; buyer pays only on draw
- **Benefit:** Reduces working capital + eliminates stockouts simultaneously
- **Requirement:** Strong EDI/data sharing, predictable SKUs
- **Best for:** High-velocity items from Strategic suppliers

#### 16. **Bullwhip Effect & Mitigation**
- **Problem:** Small demand changes at customer end amplify upstream because each tier adds safety buffer + reacts to noise
- **Cures:** POS data sharing, VMI, smaller batch sizes, everyday low pricing (no promo spikes)
- **Outcome:** Sharing end-customer demand with Tier 1 kills bullwhip at source

#### 17. **Lead Time Optimization**
- **Reality:** 50%+ of total lead time is queue/wait, not production
- **Method:** Map every step; attack largest queues first
- **Outcome:** 30% lead-time cut typically enables 40% inventory cut at same service level

---

### **Sourcing Execution**

#### 18. **RFI / RFQ / RFP Strategy**
- **RFI** (Request for Information): Early-stage market discovery; capabilities, financials, references
- **RFQ** (Request for Quotation): Known spec, price-driven, commodity-like buys
- **RFP** (Request for Proposal): Complex, solution-driven; weighted scoring across cost + technical + service + sustainability
- **Guideline:** Use RFP for Strategic/Bottleneck; RFQ for Leverage; skip the RFx entirely for Routine (use punchout catalogs)

#### 19. **Reverse Auctions**
- **Best for:** Leverage spend with 4+ qualified suppliers, well-defined specs, low switching cost
- **Typical savings:** 8–25% on first event, less on follow-ups
- **Never use for:** Strategic suppliers — destroys relationship value

#### 20. **Negotiation Tactics**
- **#1 Anchor with should-cost** — Open with your built-up cost, not their quote
- **#2 Bundle & unbundle** — Combine volume across BUs, or separate line items to find soft spots
- **#3 Index-linked pricing** — Tie raw material to LME/PIX/commodity indices; kill speculation
- **#4 Term & volume commitments** — Trade longer contract for lower unit price
- **#5 BATNA** — Always know your walk-away alternative
- **#6 Open-book costing** — For Strategic suppliers, share P&L and co-engineer cost down
- **Mindset:** Never negotiate price alone — negotiate TCO levers (lead time, MOQ, payment terms, FX, scrap rate)

#### 21. **Supplier Relationship Management (SRM)**
- **Not vendor management** — It's tiered engagement per supplier tier
  - **Tactical** (transactional) → ad-hoc contact
  - **Preferred** (commercial focus) → Quarterly business reviews
  - **Strategic** (joint roadmaps) → Monthly ops review + QBR + NPI collaboration
- **Best practice:** Invest SRM bandwidth in top 20 suppliers (Pareto applies to relationships too)

#### 22. **Maverick Spend & Tail Spend Consolidation**
- **Maverick** = off-contract buying (destroys negotiated pricing)
- **Tail** = bottom 80% of suppliers that drive 20% of spend but most admin work
- **Solutions:** Catalog/punchout, P-cards, group purchase orgs, BPO consolidation
- **Target:** Cap tail spend at <5% of total transactions through automation

---

### **Planning & Forecasting**

#### 23. **Demand Forecasting — ARIMA & Exponential Smoothing**
- **Exponential Smoothing:** Works for stable, seasonal SKUs; simple and interpretable
- **ARIMA(p,d,q):** Captures trend + seasonality + autocorrelation; great for medium-volatility SKUs
- **Validation metric:** MAPE (Mean Absolute Percentage Error) on holdout sample
- **Real-world:** Zumar combined ARIMA + Exp Smoothing + ChatGPT-assisted demand sensing for Toyota SKUs → **15% forecast error reduction**

#### 24. **Demand Sensing & AI-Assisted Forecasting**
- **Concept:** Incorporate external signals (economic indicators, competitor moves, social media, ChatGPT insights) into demand models
- **Benefit:** Catches demand spikes before they hit ERP
- **Cadence:** Weekly/bi-weekly refresh during volatile periods

---

### **Geopolitics & Risk**

#### 25. **Tariff Impact Simulation**
- **Levers when tariffs hit:**
  1. **Shift origin** to non-tariffed country (e.g., Vietnam/Mexico from China)
  2. **Tariff engineering** — Minor design tweak changes HTS code
  3. **Foreign Trade Zones / bonded warehouses**
  4. **Share the cost** with supplier & customer
  5. **Forward buy** ahead of effective date if cash/warehouse permit
- **Regression model:** 25% China tariff + elasticity -1.3 → ~32% volume decline if unmitigated
- **Real project:** Zumar's "Tariff Wars Impact on Global Sourcing" identified geopolitical shocks on supply chains

#### 26. **ESG & Sustainable Procurement**
- **Reality:** Scope 3 emissions (supply chain) = 70%+ of most companies' carbon footprint
- **Tools:** CDP / EcoVadis ratings, ISO 14001 certification for Strategic suppliers
- **Weighting:** Make sustainability 10–15% of supplier selection — buyer choices drive supplier behavior faster than regulation
- **Benefit:** Compliance + brand protection + cost avoidance on carbon-border adjustments

---

### **Process Excellence**

#### 27. **Lean & Six Sigma in Procurement**
- **DMAIC Cycle:** Define, Measure, Analyze, Improve, Control
- **Common targets:** Reduce PO cycle time, eliminate maverick spend, standardize part numbers, reduce approvals
- **Finding:** Value stream mapping usually shows 60%+ of cycle time is wait, not actual work
- **Combined power:** Pair Lean PM tools with Six Sigma analytics — process improvement + statistical validation

---

## 💡 How the Knowledge Base Powers the Chatbot

When you ask the AI Strategist a question like:

- **"Explain Kraljic Matrix"** → Returns framework definition + 4 quadrants + strategy per quadrant + real example
- **"How to negotiate with a strategic supplier?"** → Returns 6-step negotiation playbook + TCO approach + index-linking + contract elements
- **"Show spend by category as pie"** → Detects visualization intent, renders pie chart of the embedded sample data
- **"What's the difference between RFQ and RFP?"** → Compares all three (RFI, RFQ, RFP) with use cases
- **"How do I mitigate tariff impact?"** → Returns 5 levers + regression model + forward-buy calculation

---

## 🎯 Frameworks by Business Problem

**"We're spending too much on this category"**
- Should-cost teardown (clean-sheet) + Supplier quote comparison → Negotiate with anchor

**"Our supplier is unreliable"**
- Supplier risk assessment (financial + operational + geo) + Kraljic positioning + Dual-source plan

**"We need to optimize inventory"**
- EOQ solver + Safety stock formula + ABC class differentiation + Demand forecasting (ARIMA)

**"We don't know where our risk sits"**
- Spend analysis (spend cube) + Risk heatmap (probability × impact) + Tail consolidation

**"How do I source this new product?"**
- Kategorize in Kraljic + Design RFx approach + Build should-cost + Compare quotes + Negotiate TCO

**"Tariff war just hit"**
- Tariff impact simulator + Origin-shift analysis + Cost-share negotiation + Forward-buy strategy

---

## 📚 References & Further Reading

- **Kraljic, P.** (1983). "Purchasing must become supply management." *Harvard Business Review*
- **Monczka, R., Handfield, R., Giunipero, L., & Patterson, J.** (2015). *Purchasing and Supply Chain Management*
- **Bensaou, M.** (1999). "Portfolios of buyer–supplier relationships." *MIT Sloan Management Review*
- **Christopher, M., & Holweg, M.** (2011). "Supply chain 2.0 revisited." *MIT Sloan Management Review*

---

**All 27 frameworks embedded in the Should Cost AI chatbot are battle-tested in real sourcing at Amazon, Cristal Constructions, and Nykaa.**
