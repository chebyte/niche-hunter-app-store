# NicheHunter Ultra — App Store Market Intelligence

Investor-grade App Store opportunity intelligence engine for OpenClaw (VPS).

NicheHunter Ultra detects underserved niches, analyzes competitors, validates monetization signals, scores opportunities quantitatively, and generates build-ready MVP PRDs.

Designed for headless execution and Telegram interaction.

---

## What This Skill Does

Category Definition  
→ Market Demand Discovery  
→ Competitor Intelligence  
→ Gap Pattern Extraction  
→ Quantitative Scoring  
→ Market Intelligence Report  
→ MVP PRD (Rork-ready)

This is not an idea generator.  
It is a structured market analysis engine.

---

## Installation

```bash
npx clawhub@latest install niche-hunter-app-store
```

---

## Runtime Requirements

Built for:

- OpenClaw running in a VPS (headless)
- Telegram-based execution

### Required

At least ONE of the following tools must be available:

- `web_search`
- `web_fetch`

If neither is available, the skill cannot operate.

No interactive browser required.

---

## Adaptive Tool Behavior

- If `web_search` is available → used for market discovery.
- If `web_fetch` is available → used for structured data extraction.
- If both are available → discovery + extraction combined.
- If only one is available → the skill adapts automatically.

---

## Quantitative Scoring Model

Each opportunity is evaluated across:

- Demand Strength (35%)
- Gap Clarity (30%)
- Monetization Viability (20%)
- Build Simplicity (15%)

Weighted formula:

(demand × 0.35) +
(gap × 0.30) +
(monetization × 0.20) +
(build × 0.15)

All scores must be justified with observed evidence.

---

## Revenue Estimation Logic

If direct revenue data exists → used directly.

Otherwise:

Freemium:
Estimated installs ≈ ratings × 100

Paid:
Estimated installs ≈ ratings × 40

Revenue estimate:
installs × 3% × subscription price

All proxy data clearly labeled with confidence level.

---

## Output Structure

Each session produces:

1) Market Intelligence Report (ranked top 3 opportunities)
2) Quantitative scoring breakdown
3) Monetization logic explanation
4) Strategic conclusion
5) Investor-grade MVP PRD (after selection)

Outputs are optimized for Telegram:
- Vertical layout
- No ASCII tables
- No wide formatting
- Structured blocks

---

## Ideal For

- Indie founders validating app ideas
- AI builders searching monetizable verticals
- Telegram-based research workflows
- OpenClaw autonomous market analysis

---

## Philosophy

NicheHunter Ultra enforces:

- Evidence-based reasoning
- Quantitative scoring
- Revenue validation
- Structured reporting
- Confidence labeling

No hype. Only signals.

---

## License

MIT
