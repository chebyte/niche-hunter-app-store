# NicheHunter App Store

Full-pipeline skill for discovering underserved niches in the App Store, analyzing competitor gaps, and generating revenue-validated opportunity reports with MVP PRDs.

## What This Skill Does

```
Define Category → App Store Charts → Competitor Deep-Dive → Gap Analysis → Top 3 Report → PRD
```

This skill helps you:
- Find profitable app ideas in any category
- Analyze App Store charts for underserved opportunities
- Research competitor apps (ratings, reviews, revenue gaps)
- Generate a top-3 opportunity report with revenue validation
- Write detailed MVP PRDs optimized for [Rork](https://rork.com/) prototyping

## Quick Start

```bash
# Install the skill
npx clawhub@latest install nichehunter-app-store
```

## Prerequisites

- **WebFetch** and **WebSearch** tools available (standard in Claude Code)
- **Optional**: [Rork](https://rork.com/) account for building prototypes from the PRD

## Usage

Trigger phrases:
- "find app opportunities"
- "app store research"
- "what app should I build"
- "research this app category"
- "find a gap in the app store"

## Example Output

### Top 3 Opportunity Report

```markdown
# Top 3 App Opportunities in Health & Fitness

## Opportunity 1: AR Rep Counter (RECOMMENDED)
**One-line pitch:** AI-powered AR app that counts workout reps using camera
**The gap:** No AR rep counter exists in top 25 fitness apps
**Target user:** Home workout enthusiasts who want form correction
**Revenue model:** $6.99/mo subscription
**Competition:** Fitbod (no AR), Strava (no rep counting)
**Confidence:** HIGH - clear gap, proven willingness to pay
```

## Categories Available

Health & Fitness, Productivity, Finance, Lifestyle, Photo & Video, Education, Entertainment, Food & Drink, Social Networking, Travel, Utilities

## Revenue Benchmarks

| App Type | Solo Dev Benchmark |
|----------|-------------------|
| Niche utility | $1-5K/mo |
| Habit/tracker | $5-15K/mo |
| Gamified self-care | $10-50K/mo |
| Productivity | $3-10K/mo |
| AI-powered tool | $5-30K/mo |

## Pricing Sweet Spots (2025)

| Tier | Monthly | Best For |
|------|---------|----------|
| Impulse | $2.99-4.99 | Simple utilities |
| **Standard** | **$5.99-6.99** | **Most indie apps** |
| Premium | $9.99-14.99 | AI-heavy |

## Session Output

A complete session produces:
1. **Top 3 Opportunity Report** — saved to `research/top-3-opportunities-{category}.md`
2. **MVP PRD** — saved to `PRD-{AppName}.md`, ready to paste into Rork

## License

MIT
