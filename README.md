# Clawd Cawfee

A Claude Code-powered system for discovering and tracking specialty coffee in the Indian market. It learns your preferences, searches for recommendations, and refines suggestions based on your feedback.

## Setup

1. **Install Claude Code** — [anthropic.com/claude-code](https://claude.com/claude-code)

2. **Clone this repo**
   ```bash
   git clone https://github.com/your-username/clawd-cawfee.git
   cd clawd-cawfee
   ```

3. **Start Claude Code in the project directory**
   ```bash
   claude
   ```

4. **Run your first command**
   ```
   /know-me
   ```

That's it. The slash commands are defined in `.claude/commands/` and work automatically.

## Quick Start

```bash
# 1. Build your preference profile
/know-me

# 2. Get coffee recommendations
/find-me-coffee

# 3. After trying a coffee, log your experience
/feedback-log

# 4. View your coffee journey stats
/coffee-stats
```

## Commands

### `/know-me` — Build Your Profile

An interactive interview that captures your coffee preferences across 6 sections:

1. **Equipment** — Your grinder and brewing methods
2. **Flavor Preferences** — What you love and avoid (mapped to SCA flavor wheel)
3. **Roast Level** — Light to dark preferences
4. **Origins & Processing** — Geographic and processing preferences
5. **Budget** — Price ceilings for regular and splurge purchases
6. **Trusted Roasters** — Your curated list of Indian roasters

**Features:**
- Resumable — stop anytime, continue later with `/know-me`
- No jargon — translates specialty terms to sensory descriptions
- Saves progress after each section

### `/find-me-coffee` — Get Recommendations

Searches for coffee matching your preferences and current mood.

**How it works:**
1. Asks what you're looking for (usual match, adventurous, comfort)
2. Searches your trusted roasters' current offerings
3. Searches Reddit (r/IndiaCoffee) for reviews and trending coffees
4. Scores matches: 60% preference alignment + 40% community sentiment
5. Returns 5-7 ranked recommendations with justifications

**Filters applied:**
- Budget constraints
- Roast-to-order freshness (no stale coffee)
- Excludes coffees you've tried in the last 3 months
- Excludes roasters you've blacklisted

### `/feedback-log` — Log Your Experience

Record your experience after trying a coffee.

**Captures:**
- Brewing context (method, grind, ratio, temp)
- Rating (1-5 stars)
- Flavor notes you experienced
- Repurchase intent
- Free-form notes

**Smart features:**
- Tracks dial-in journey (multiple attempts per coffee)
- Discounts negative ratings if brewing had issues
- Supports external coffees (not just recommendations)
- Auto-consolidates patterns every 10 entries

### `/coffee-stats` — View Your Journey

Analytics and insights about your coffee exploration:

- Total coffees tried, unique roasters, date range
- Top-rated and most repurchased coffees
- Origin and roast level preferences (with ratings)
- Flavor profile analysis
- Spending patterns and best-value finds
- Roaster report card
- Implicit wishlist (high-match coffees you haven't tried)

## Workflow

```
┌─────────────┐
│  /know-me   │ ──► Build initial preference profile
└─────────────┘
       │
       ▼
┌─────────────────┐
│ /find-me-coffee │ ──► Get recommendations based on profile
└─────────────────┘
       │
       ▼
   ☕ Try coffee
       │
       ▼
┌───────────────┐
│ /feedback-log │ ──► Log your experience
└───────────────┘
       │
       ▼
┌───────────────┐
│ /coffee-stats │ ──► View patterns & insights
└───────────────┘
       │
       ▼
   (repeat)
```

## File Structure

```
clawd-cawfee/
├── .claude/
│   └── commands/           # Slash command definitions
│       ├── know-me.md
│       ├── find-me-coffee.md
│       ├── feedback-log.md
│       └── coffee-stats.md
├── coffee/                 # Your personal data (gitignored)
│   ├── profile.md          # Preferences (built by /know-me)
│   └── feedback-log.md     # All your feedback entries
├── examples/               # Example files to see the format
│   ├── profile.md
│   └── feedback-log.md
├── CLAUDE.md               # Project instructions for Claude
└── README.md
```

## Your Data

All your data lives in the `coffee/` directory:

- **profile.md** — Your preferences, equipment, budget, trusted roasters
- **feedback-log.md** — Every coffee you've logged with ratings and notes

This is plain markdown — you can read, edit, or backup these files directly. The `coffee/` directory is gitignored so your personal data stays local.

Check `examples/` to see what a filled-out profile and feedback log look like.

## Customization

### Add/Remove Trusted Roasters

Edit `coffee/profile.md` directly, or run `/know-me` and update section 6.

### Adjust Budget

Edit `coffee/profile.md` or re-run the budget section of `/know-me`.

### Reset Everything

Delete the files in `coffee/` to start fresh:
```bash
rm coffee/profile.md coffee/feedback-log.md
```

## Indian Roasters Supported

The system knows about these specialty roasters (and discovers more via Reddit):

| Roaster | Known For |
|---------|-----------|
| Blue Tokai | Nationwide, accessible, consistent |
| Third Wave | Cafe chain with retail |
| Subko | Mumbai, experimental, multi-species |
| Black Baza | Sustainability-focused |
| Araku | Tribal-grown, Andhra Pradesh |
| Bili Hu | Indian estate focus |
| Corridor Seven | Bengaluru |
| KC Roasters | Bengaluru |
| Bloom Coffee | — |
| Bombay Island | Mumbai, small-batch |

## How Recommendations Work

### Scoring (Hybrid Model)

```
Final Score = (Preference Match × 60%) + (Community Sentiment × 40%)
```

**Preference Match considers:**
- Flavor profile alignment (SCA wheel)
- Roast level match
- Origin preferences
- Processing method
- Budget fit
- Equipment compatibility

**Community Sentiment considers:**
- Reddit upvotes and comment tone
- Recency of reviews
- Specificity of praise

### Freshness Requirement

Only recommends roasters known to roast-to-order. No stale coffee.

### Constraint Relaxation

If no perfect matches exist, the system relaxes constraints one at a time:
1. First: Include good-stock-management roasters
2. Then: Stretch budget by ₹50-100
3. Then: Expand to adjacent flavor categories

Always explains what was relaxed.

## Preference Evolution

Your preferences evolve based on feedback:

- **Recent feedback weighs 2×** — Your taste 3 months ago matters less than last week
- **Confidence levels** — Preferences with 5+ data points are "High" confidence
- **Passive contradiction resolution** — If you say you love acidity but keep rating acidic coffees low, the system learns from behavior

## Requirements

- Claude Code CLI
- Internet access (for web search during `/find-me-coffee`)

## Privacy

- All data stored locally in `coffee/` directory (gitignored)
- No external sync — you control backups
- Web searches happen during `/find-me-coffee` only

---

Built with [Claude Code](https://claude.com/claude-code) slash commands.
