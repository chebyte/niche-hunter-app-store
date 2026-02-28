---
name: niche-hunter-app-store
description: NicheHunter Ultra — Headless App Store Market Intelligence engine for OpenClaw (VPS). Uses web_search (+ web_fetch optional) to detect underserved niches, analyze competitors, validate monetization signals, score opportunities quantitatively, and generate investor-grade MVP PRDs. Optimized for Telegram.
metadata:
  tags: app-store, market-intelligence, competitor-analysis, revenue-validation, scoring, prd, rork, openclaw, telegram
---

# NicheHunter Ultra — Market Intelligence Mode

Designed for:
- OpenClaw running in a VPS (headless)
- Telegram interaction
- No interactive browser

---

# Required Tools

| Tool | Requirement | Purpose |
|------|------------|---------|
| web_search | REQUIRED | Discover charts, competitors, reviews, revenue signals |
| web_fetch | Optional | Extract structured content from URLs |

If web_search is unavailable → STOP execution.

---

# Execution Discipline (Strict)

- Max 18 web_search calls
- Max 20 URLs analyzed
- Max 8 competitors per niche
- Max 20 reviews per app (prioritize 1★ and 3★)
- No duplicate queries
- If paywalled → try 1 alternative source only
- Proxy revenue must be labeled with confidence

No speculation presented as fact.

---

# PIPELINE

1) Category Definition  
2) Market Demand Discovery  
3) Competitor Intelligence  
4) Gap Pattern Extraction  
5) Quantitative Scoring  
6) MARKET INTELLIGENCE REPORT (ENFORCED FORMAT)  
7) PRD (after user selection)

Each step must output a checkpoint.

---

# CHECKPOINT FORMAT (MANDATORY)

--- CHECKPOINT ---
Step: {1–7}
Category: {category}
Micro-niches: [...]
Competitors analyzed: [...]
Chosen Opportunity: null | "{name}"
Next: {next step}
--- END CHECKPOINT ---

---

# REVENUE ESTIMATION MODEL

If direct revenue found → use it.

If not:

Freemium:
Estimated installs ≈ ratings × 100

Paid:
Estimated installs ≈ ratings × 40

Revenue:
installs × 3% × subscription price

Confidence must be labeled:
High / Medium / Low

---

# QUANTITATIVE SCORING MODEL

Score 0–10:

Demand Strength (35%)
Gap Clarity (30%)
Monetization Viability (20%)
Build Simplicity (15%)

Weighted Score =
(demand × 0.35) +
(gap × 0.30) +
(monetization × 0.20) +
(build × 0.15)

Scores must be justified with evidence.

---

# OUTPUT ENFORCEMENT BLOCK (CRITICAL)

The assistant MUST output the final opportunity analysis using the exact structure below.
No simplified tables.
No star-only scoring.
No vague summaries.

═══════════════════════════════
📊 MARKET INTELLIGENCE REPORT
Category: {Category}
Research Confidence: {High | Medium | Low}
═══════════════════════════════

## 🥇 Opportunity #1 — {Name}

🎯 Strategic Positioning:
{1 concise positioning sentence}

📈 Demand Evidence:
- Key competitors analyzed:
- Rating ranges:
- Chart presence:
- Growth indicators:

💰 Monetization Evidence:
- Pricing benchmark:
- Revenue signals (direct or proxy):
- Install estimate logic:
- Conversion assumption:

🧩 Gap Evidence:
- Repeated complaints:
- Missing feature overlap:
- UX weaknesses:

⚙️ Build Complexity:
{Low | Medium | High}
Reasoning:

📊 Quantitative Scoring:
Demand: X/10
Gap: X/10
Monetization: X/10
Build Simplicity: X/10
Weighted Score: X.X / 10

Confidence Level: {High | Medium | Low}

───────────────────────────────

## 🥈 Opportunity #2
(Same structure, more concise)

───────────────────────────────

## 🥉 Opportunity #3
(Same structure, more concise)

═══════════════════════════════
🏁 Strategic Conclusion
Data-based reasoning only. No hype.
═══════════════════════════════

After delivering this report, ask the user to choose #1 / #2 / #3 before generating the PRD.

---

# PRD REQUIREMENTS

Once selected, generate:

1) Executive Summary  
2) Market Validation Summary  
3) Target Personas  
4) Core Differentiator (Wedge)  
5) MVP Feature Groups  
6) Screen Architecture (Expo Router structure)  
7) Monetization Strategy  
8) Tech Stack (Expo SDK 52+, TypeScript)  
9) Design System (hex colors mandatory)  
10) KPIs  
11) Risks & Mitigations  

PRD must be:
- Concrete
- UI-specific
- Copy-paste ready for Rork
- No fluff
