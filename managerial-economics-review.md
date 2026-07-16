# Managerial Economics — Rapid Brush-Up Guide

A condensed review of a standard managerial economics course. Each section gives the core concepts, key formulas, and the managerial takeaway — enough to refresh before an exam, interview, or business decision.

---

## 1. What Managerial Economics Is

Managerial economics applies microeconomic theory and quantitative methods to business decision-making. It answers questions like:

- What price should we charge?
- How much should we produce?
- Should we enter (or exit) a market?
- How do we respond to a competitor's move?

**Core principle:** decisions are made **at the margin** — compare *marginal benefit* to *marginal cost*, and ignore **sunk costs** (money already spent that can't be recovered). Always account for **opportunity cost**: the value of the best alternative forgone.

---

## 2. Demand Analysis and Elasticity

### Demand basics
- **Law of demand:** price ↑ → quantity demanded ↓ (movement *along* the curve).
- **Shifts** of the demand curve come from income, prices of related goods, tastes, expectations, and number of buyers.

### Elasticity — the workhorse concept

| Elasticity | Formula | Interpretation |
|---|---|---|
| Price elasticity of demand (Ed) | %ΔQd ÷ %ΔP | \|Ed\| > 1 elastic; < 1 inelastic; = 1 unit elastic |
| Income elasticity (Ey) | %ΔQd ÷ %ΔIncome | > 0 normal good; < 0 inferior; > 1 luxury |
| Cross-price elasticity (Exy) | %ΔQd of X ÷ %ΔP of Y | > 0 substitutes; < 0 complements |

**Arc (midpoint) elasticity:** Ed = [(Q₂−Q₁)/((Q₁+Q₂)/2)] ÷ [(P₂−P₁)/((P₁+P₂)/2)]

### The revenue rule (most-tested idea)
- Demand **elastic** → cutting price **raises** total revenue.
- Demand **inelastic** → raising price **raises** total revenue.
- **Marginal revenue:** MR = P(1 + 1/Ed). Revenue is maximized where Ed = −1 (MR = 0).

**Managerial takeaway:** never raise price on an elastic product to boost revenue; never discount an inelastic one.

### Demand estimation & forecasting
- Regression analysis (interpret coefficients, R², t-stats).
- Time-series methods: trend projection, moving averages, exponential smoothing.
- Qualitative: surveys, market experiments, Delphi method.

---

## 3. Consumer Behavior (quick refresher)

- **Utility maximization rule:** spend so that MUx/Px = MUy/Py (equal marginal utility per rupee/dollar).
- **Indifference curves** + budget line: optimum where MRS = Px/Py.
- **Substitution effect** vs **income effect** of a price change.

---

## 4. Production Theory

- **Production function:** Q = f(L, K, …).
- **Short run:** at least one input fixed. **Law of diminishing marginal returns:** adding more of a variable input eventually yields smaller increases in output.
- Key measures: Total product (TP), Average product (AP = Q/L), Marginal product (MP = ΔQ/ΔL). MP cuts AP at AP's maximum.
- **Three stages of production:** rational production occurs in Stage II (MP falling but positive, AP falling).
- **Long run:** all inputs variable. **Returns to scale:** increasing / constant / decreasing.
- **Optimal input mix (least-cost rule):** MPL/w = MPK/r — the marginal product per unit of cost must be equal across inputs. Graphically: isoquant tangent to isocost line (MRTS = w/r).

---

## 5. Cost Analysis

### Cost concepts
- **Explicit vs implicit costs** → economic profit = revenue − explicit − implicit costs (accounting profit ignores implicit costs).
- **Fixed (FC)** vs **variable (VC)**; TC = FC + VC.
- **Marginal cost:** MC = ΔTC/ΔQ. **Average cost:** ATC = TC/Q, AVC = VC/Q, AFC = FC/Q.
- MC intersects AVC and ATC at their **minimum points**.

### Cost curves
- Short-run ATC is U-shaped (diminishing returns).
- Long-run average cost (LRAC) is the envelope of short-run curves.
- **Economies of scale:** LRAC falls as output grows (specialization, indivisibilities, bulk buying). **Diseconomies:** LRAC rises (coordination costs). **Economies of scope:** producing two goods together is cheaper than separately.

### Breakeven & contribution analysis
- **Breakeven quantity:** Q* = FC ÷ (P − AVC), where (P − AVC) is the **contribution margin** per unit.
- **Operating leverage:** high fixed costs → profits more sensitive to sales volume.

---

## 6. Market Structures

| Feature | Perfect competition | Monopolistic competition | Oligopoly | Monopoly |
|---|---|---|---|---|
| Firms | Very many | Many | Few | One |
| Product | Homogeneous | Differentiated | Either | Unique |
| Entry | Free | Easy | Barriers | Blocked |
| Price power | None (price taker) | Some | Considerable | Maximum |
| LR economic profit | Zero | Zero | Possible | Possible |

**Universal profit-maximizing rule: produce where MR = MC** (and P ≥ AVC in the short run, else shut down).

- **Perfect competition:** P = MR = MC; long-run entry/exit drives economic profit to zero; P = min ATC (allocative + productive efficiency).
- **Monopoly:** MR < P; produces less and charges more than competition; creates **deadweight loss**. Watch for natural monopoly (falling LRAC over entire market).
- **Monopolistic competition:** short-run profits eroded by entry; competes on differentiation, branding, advertising; excess capacity in long run.
- **Oligopoly:** strategic interdependence. Models: **kinked demand** (price rigidity), **Cournot** (quantity competition), **Bertrand** (price competition), **Stackelberg** (leader–follower), **cartel/collusion** (unstable — incentive to cheat).

---

## 7. Game Theory Essentials

- **Dominant strategy:** best regardless of rival's choice.
- **Nash equilibrium:** no player can gain by unilaterally deviating.
- **Prisoner's dilemma:** individually rational choices → collectively worse outcome (explains why cartels break down and price wars start).
- **Repeated games:** cooperation can be sustained (tit-for-tat, trigger strategies).
- **Sequential games:** solve by **backward induction**; first-mover advantage; credible vs empty threats (commitment matters).

---

## 8. Pricing Strategies

- **Cost-plus (markup) pricing:** P = ATC × (1 + markup). Optimal markup relates to elasticity: **P = MC × [Ed/(Ed+1)]** — more elastic demand → smaller markup.
- **Price discrimination** (requires market power, segmentation, no resale):
  - 1st degree: charge each buyer their willingness to pay.
  - 2nd degree: quantity discounts, versioning, block pricing.
  - 3rd degree: different prices to different groups (student fares) — charge more where demand is less elastic: set MR₁ = MR₂ = MC.
- **Peak-load pricing:** higher prices when capacity is scarce.
- **Two-part tariff:** entry fee + per-unit price (gym membership).
- **Bundling:** pure vs mixed — extracts surplus when valuations are negatively correlated.
- **Penetration pricing** (low to build share) vs **price skimming** (high to early adopters).
- **Transfer pricing:** price internal transactions at marginal cost (or market price if an external market exists).

---

## 9. Risk, Uncertainty, and Decision-Making

- **Expected value:** EV = Σ (probability × payoff).
- **Risk measured by** variance / standard deviation; **coefficient of variation** (σ/EV) compares risk across projects of different sizes.
- **Risk attitudes:** risk-averse (diminishing marginal utility of money), risk-neutral, risk-seeking. Risk-averse managers use **expected utility**, not expected value.
- **Decision trees** for sequential decisions under uncertainty.
- Criteria without probabilities: **maximin** (pessimist), **maximax** (optimist), **minimax regret**.
- **Asymmetric information:** adverse selection (hidden information — lemons problem), moral hazard (hidden action). Remedies: signaling, screening, warranties, incentive contracts.

---

## 10. Capital Budgeting & Long-Run Investment

- **Time value of money:** PV = FV ÷ (1+r)ⁿ.
- **NPV = Σ [CFt/(1+r)ᵗ] − initial outlay.** Accept if NPV > 0 — the gold-standard rule.
- **IRR:** discount rate making NPV = 0; accept if IRR > cost of capital (beware multiple/no IRR with non-conventional cash flows).
- **Payback period:** simple but ignores time value and post-payback flows.
- **Cost of capital:** WACC = weighted average of debt and equity costs; used as the hurdle rate.

---

## 11. Macro Environment for Managers (brief)

- **GDP, inflation (CPI/WPI), unemployment, interest rates, exchange rates** — how each affects demand forecasts and costs.
- **Business cycles:** expansion, peak, recession, trough — cyclical vs defensive industries.
- **Fiscal policy** (government spending/taxes) and **monetary policy** (central bank rates, money supply) — impact on borrowing costs and consumer demand.

---

## 12. Government and Market Failure

- **Externalities:** negative (pollution → tax, e.g., Pigouvian tax) and positive (education → subsidy). **Coase theorem:** private bargaining can fix externalities if property rights are clear and transaction costs low.
- **Public goods:** non-rival, non-excludable → free-rider problem.
- **Price controls:** ceilings (shortages) and floors (surpluses).
- **Antitrust/competition policy:** limits collusion, predatory pricing, anticompetitive mergers.

---

## Formula Cheat Sheet

| Concept | Formula |
|---|---|
| Price elasticity | Ed = %ΔQ ÷ %ΔP |
| Marginal revenue | MR = P(1 + 1/Ed) |
| Profit maximization | MR = MC |
| Optimal markup | P = MC · Ed/(Ed + 1) |
| Least-cost input mix | MPL/w = MPK/r |
| Breakeven quantity | Q* = FC ÷ (P − AVC) |
| Economic profit | Revenue − explicit costs − implicit costs |
| Expected value | EV = Σ pᵢ·xᵢ |
| NPV | Σ CFt/(1+r)ᵗ − C₀ |
| Shut-down rule (SR) | Produce only if P ≥ AVC |

---

## Self-Test (10 quick questions)

1. If demand elasticity is −0.5, does a price increase raise or lower revenue? *(Raise — inelastic.)*
2. Why are sunk costs irrelevant to decisions? *(They're unrecoverable regardless of the choice.)*
3. Where does a monopolist produce, and why is there deadweight loss? *(MR = MC; P > MC means some mutually beneficial trades don't happen.)*
4. State the least-cost input rule. *(MPL/w = MPK/r.)*
5. What's the difference between accounting and economic profit? *(Economic profit subtracts implicit/opportunity costs.)*
6. In a prisoner's dilemma, why do cartels collapse? *(Cheating is each member's dominant strategy.)*
7. When should a firm shut down in the short run? *(When P < AVC.)*
8. Third-degree price discrimination: which segment pays more? *(The less elastic one.)*
9. NPV vs IRR — which do you trust when they conflict? *(NPV.)*
10. What does an income elasticity of 1.8 tell you? *(Luxury/normal good — demand grows faster than income; cyclical exposure.)*
