---
name: niche-hunter-app-store
description: NicheHunter — Full-pipeline App Store opportunity research. Discovers underserved niches, analyzes competitor gaps, produces revenue-validated top-3 opportunity reports, and writes MVP PRDs ready for Rork — all automated through web research.
metadata:
  tags: app-store, research, mobile-app, competitor-analysis, market-research, prd, prototype, rork, indie-hacker, startup
---

## When to Use

Use this skill when the user wants to:
- Find profitable app ideas in a category or niche
- Research App Store charts for underserved opportunities
- Analyze competitor apps (ratings, reviews, revenue, gaps)
- Generate a top-3 opportunity report with revenue validation
- Write a detailed MVP Product Requirements Document (PRD)

Trigger phrases: "find app opportunities", "app store research", "what app should I build", "research this app category", "find a gap in the app store"

## Prerequisites

- **WebFetch tool** — for browsing App Store pages and competitor sites
- **WebSearch tool** — for finding revenue data, reviews, and market intel
- **Write tool** — for saving research outputs and PRD
- No API keys required — all research is done through live web interaction

## Tools You Will Use

| Tool | Purpose |
|------|---------|
| `WebFetch` | Navigate App Store pages, read app listings, scrape competitor info |
| `WebSearch` | Find revenue data, Trustpilot reviews, market research, news |
| `Write` | Save the Top 3 Report and PRD as files |

**IMPORTANT:** Do NOT use Bash, browser tools, or any other tool for web research. `WebFetch` and `WebSearch` are the only tools needed for gathering data.

## Pipeline Overview

```
Define Category → App Store Charts → Competitor Deep-Dive → Gap Analysis → Top 3 Report → PRD
```

---

## Step 1: Define the Category

Ask the user what space they want to explore. Help them narrow down:

- **Too broad:** "Health apps" (thousands of competitors)
- **Good:** "Sleep + anxiety apps for consumers" (specific intersection)
- **Good:** "Habit tracking for fitness beginners" (audience + niche)
- **Good:** "AI-powered journaling apps" (tech angle + category)

**Key questions to ask:**
1. What category or problem space interests you?
2. Consumer or B2B? (Consumer is easier to validate quickly)
3. Any budget constraints? (No-AI = cheaper to build, AI = higher ceiling)
4. Target revenue? ($1K/mo hobby vs $10K/mo business)

---

## Step 2: App Store Charts Research

Browse the App Store charts in the relevant category using `WebFetch`:

### How to navigate

Use `WebFetch` to load the chart page and extract the app list:

```
WebFetch url="https://apps.apple.com/us/charts/iphone/{category-slug}/{category-id}"
  prompt="List the top 25 apps showing: position, app name, rating count, star rating, price/monetization, and brief description"
```

### Common category URLs (US market)

| Category | URL path |
|----------|----------|
| Health & Fitness | `/health-fitness-apps/6013` |
| Lifestyle | `/lifestyle-apps/6012` |
| Productivity | `/productivity-apps/6007` |
| Education | `/education-apps/6017` |
| Medical | `/medical-apps/6020` |
| Entertainment | `/entertainment-apps/6016` |
| Finance | `/finance-apps/6015` |
| Photo & Video | `/photo-video-apps/6008` |
| Food & Drink | `/food-drink-apps/6023` |
| Social Networking | `/social-networking-apps/6005` |
| Travel | `/travel-apps/6003` |
| Utilities | `/utilities-apps/6002` |

Full URL format: `https://apps.apple.com/us/charts/iphone/{category-slug}/{category-id}`

### What to document for each app

- App name and chart position
- Rating count (proxy for install base)
- Star rating
- Price/monetization model (free, freemium, paid, subscription)
- Brief description

### How to read the patterns

| Rating Count | Signal |
|-------------|--------|
| >100K ratings | Saturated — dominated by a major player |
| 1K-50K ratings | Proven demand, beatable by a better product |
| <500 ratings | Possible new/underserved niche or low demand |

---

## Step 3: Competitor Deep-Dive

For each promising niche area, deep-dive into 5-8 competitor apps.

### How to research each app

1. **App Store listing** — Use `WebFetch` on the app's App Store URL:
   ```
   WebFetch url="https://apps.apple.com/us/app/{app-slug}/{app-id}"
     prompt="Extract: app name, rating count, star rating, price/subscription, key features from description, and notable points from screenshots"
   ```

2. **Reviews and reputation** — Use `WebSearch` to find external reviews:
   ```
   WebSearch query="{app name} trustpilot reviews"
   WebSearch query="{app name} app review 2025"
   ```

3. **Revenue data** — Use `WebSearch` for revenue estimates:
   ```
   WebSearch query="{app name} revenue ARR"
   WebSearch query="{app name} app revenue estimate"
   ```

### Data to collect per app

| Field | Source |
|-------|--------|
| Name | App Store listing (WebFetch) |
| Ratings count | App Store listing (WebFetch) |
| Star rating | App Store listing (WebFetch) |
| Price / subscription | App Store listing (WebFetch) |
| Trustpilot score | WebSearch "{app name} trustpilot" |
| Estimated revenue | WebSearch "{app name} revenue" |
| Key features | App Store description (WebFetch) |
| Top complaints | WebSearch "{app name} complaints" or 1-star reviews |
| Missing features | Compare across competitors |

### Revenue Estimation Techniques

- **Direct sources:** WebSearch "{app name} revenue", "{app name} ARR"
- **Proxy calculation:** `rating_count * 40-80 = approximate installs` (rule of thumb)
- **Industry benchmarks:** 2-5% of free users convert to paid
- **Comparable apps:** Find similar apps with known revenue

### Red Flags (Avoid These Niches)

- Top app has 1M+ ratings (dominated by a giant)
- Category requires hardware integration (Apple Watch data, etc.)
- Heavy regulation (medical devices, financial trading)
- All competitors are free with no monetization path

### Green Flags (Pursue These Niches)

- Top competitors have poor reviews (< 3.0 Trustpilot)
- Solo devs making $50K+/yr (proves indie viability)
- "Editors' Choice" app exists with < 20K ratings (Apple promotes the niche)
- Users complain about the same missing feature across multiple apps
- Clear $5-15/mo willingness to pay

---

## Step 4: Gap Analysis

Create a **feature comparison matrix** across the top competitors:

```markdown
| Feature | App A | App B | App C | App D | YOUR APP |
|---------|-------|-------|-------|-------|----------|
| Core Feature 1 | Yes | Yes | No | Yes | YES |
| Core Feature 2 | No | Yes | Yes | No | YES |
| Missing Feature | No | No | No | No | YES |
| Price | $14.99 | $9.99 | Free | $6.99 | $5.99 |
| UX Quality | Poor | Good | OK | Good | Premium |
```

The winning opportunity is where:
1. Multiple competitors exist (proven demand)
2. They all miss the same 1-2 features
3. Users vocally complain about the gap
4. Pricing is high enough to support indie revenue

---

## Step 5: Top 3 Opportunity Report

Produce a ranked report with this structure and **save it as a file**:

```markdown
# Top 3 App Opportunities in {Category}

## Opportunity 1: {App Name} (RECOMMENDED)
**One-line pitch:** {What it does in 10 words}
**The gap:** {What's missing in the market}
**Target user:** {Who and why they'd pay}
**Revenue model:** {Price point and conversion assumptions}
**Revenue path:** {How to reach $X/mo}
**Competition:** {Who exists, why you win}
**Build complexity:** {Low/Medium/High}
**Confidence:** {High/Medium/Low with reasoning}

## Opportunity 2: {App Name}
...

## Opportunity 3: {App Name}
...

## Recommendation
{Why #1 is the best bet, with specific reasoning}
```

**Save using:** `Write` tool to `{project-dir}/research/top-3-opportunities-{category}.md`

**Present this to the user and get their pick before proceeding to the PRD.**

---

## Step 6: Write the MVP PRD

Once the user selects an opportunity, write a comprehensive PRD with these sections:

1. **Executive Summary** — One paragraph pitch
2. **Market Opportunity** — Problem, market size, competitive landscape table, revenue validation
3. **Target Users** — 2-3 personas with name, pain points, willingness to pay
4. **MVP Feature Set** — 5-8 feature groups with specs and UI behavior
5. **Screen Map & User Flow** — All screens with parent/child relationships and primary user journey
6. **Monetization** — Free vs Premium feature split, pricing, trial strategy
7. **Tech Stack** — Framework, libraries, state management, persistence
8. **Design Direction** — Color palette (hex codes), typography notes, component style
9. **Success Metrics** — KPIs with specific targets
10. **Risks & Mitigations** — Top 5 risks with solutions

**Save using:** `Write` tool to `{project-dir}/PRD-{AppName}.md`

### PRD optimized for Rork

The PRD should be written in a way that the user can copy its content directly into [Rork](https://rork.com/) to generate a working prototype. To make this work:

- Include specific hex color codes in Design Direction
- Be explicit about navigation structure (tab names, icons)
- Describe each screen with concrete UI elements
- Mention Expo SDK 52+, TypeScript, and Expo Router as tech stack
- Include mock data examples for key screens

---

## Revenue Validation Benchmarks

Use these benchmarks to reality-check opportunity viability:

| App Type | Solo Dev Benchmark | Small Team | Reference |
|----------|-------------------|------------|-----------|
| Niche utility | $1-5K/mo | $5-20K/mo | Rootd ($1M+ total, 1 person) |
| Habit/tracker | $5-15K/mo | $20-80K/mo | Daylio ($50K/mo) |
| Gamified self-care | $10-50K/mo | $100K+/mo | Finch ($2M/mo) |
| Meditation/wellness | $5-20K/mo | $50-500K/mo | Calm ($100M+/yr) |
| Productivity | $3-10K/mo | $20-100K/mo | Various |
| AI-powered tool | $5-30K/mo | $50-300K/mo | Emerging category |

## Pricing Sweet Spots (2025)

| Tier | Monthly | Annual | Best For |
|------|---------|--------|----------|
| Impulse buy | $2.99-4.99/mo | $19.99-29.99/yr | Simple utilities |
| **Standard** | **$5.99-6.99/mo** | **$34.99-44.99/yr** | **Most indie apps** |
| Premium | $9.99-14.99/mo | $59.99-99.99/yr | AI-heavy or professional |

## Marketing Channel Playbook

| Channel | Best For | Cost | Time to Results |
|---------|----------|------|-----------------|
| TikTok organic | Consumer apps, visual demos | Free | 2-4 weeks |
| Reddit (niche subs) | Technical/niche apps | Free | 1-2 weeks |
| Product Hunt | Productivity/dev tools | Free | Launch day spike |
| Apple Search Ads | Any iOS app | $0.50-3/tap | Immediate |
| Instagram Reels | Lifestyle/wellness apps | Free | 2-6 weeks |
| Twitter/X | Dev tools, indie hackers | Free | Ongoing |

---

## Example Session Output

A complete session produces:
1. **Top 3 Opportunity Report** — saved to `research/top-3-opportunities-{category}.md`
2. **MVP PRD** — saved to `PRD-{AppName}.md`, ready to paste into Rork
3. **Go-to-market notes** — pricing, channels, launch plan embedded in the PRD
