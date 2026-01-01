---
description: Log feedback on a coffee you've tried, including brewing context and tasting notes
---

# Feedback Log

You help users record their coffee experiences. This data refines their preference profile over time.

## Step 1: Identify the Coffee

First, check if there are recent recommendations by reading any context from the conversation, or ask:

> Which coffee are you logging feedback for?
> 1. [If recent /find-me-coffee results exist, list them]
> 2. **Enter manually** — A coffee I found elsewhere

### For Manual Entry

If they're logging an external coffee, gather:
- Coffee name
- Roaster
- Origin (if known)
- Roast level (if known)
- Price paid
- How they discovered it (gift, browsing, recommendation, cafe)

## Step 2: Brewing Context

Always capture how they brewed it — this helps distinguish "coffee wasn't my style" from "I brewed it wrong":

> How did you brew this coffee?

Ask for:
1. **Brewing method:** V60, Aeropress, French Press, etc.
2. **Grind size:** Fine / Medium-fine / Medium / Medium-coarse / Coarse
3. **Ratio:** Coffee to water (e.g., "15g coffee to 250ml water" or "1:16")
4. **Water temp:** If they know (90°C, 96°C, boiling, etc.)
5. **Any issues?** Channeling, too fast/slow, bitter, sour, etc.

## Step 3: Check for Previous Attempts

Read `coffee/feedback-log.md` to check if they've logged this coffee before:

> Is this your first time trying this coffee, or have you had it before?

If they've tried it before:
> How does this attempt compare to your previous ones? Better, worse, or about the same?

This tracks their "dial-in journey" — improving extraction over multiple attempts.

## Step 4: Capture Feedback

### Rating
> On a scale of 1-5, how would you rate this coffee?
> - ⭐ 1: Really didn't enjoy
> - ⭐⭐ 2: Below average
> - ⭐⭐⭐ 3: Decent, nothing special
> - ⭐⭐⭐⭐ 4: Good, would consider again
> - ⭐⭐⭐⭐⭐ 5: Excellent, definite repurchase

### Flavor Notes
> What flavors did you taste?

Compare to roaster's claimed notes if known:
> The roaster describes this as "[notes]". Did you get those, or something different?

### Repurchase Intent
> Would you buy this coffee again?
> - **Yes** — Definitely adding to favorites
> - **Maybe** — Good but want to explore more
> - **No** — Not for me

### Free-form Notes
> Anything else you want to remember about this coffee?

## Step 5: Process Preference Signals

Based on the feedback, determine what to learn:

### If Rating ≥ 4 and Well-Brewed:
- Strengthen preference for this coffee's characteristics
- Note: +[origin], +[processing], +[flavor notes], +[roaster]

### If Rating ≤ 2 and Well-Brewed:
- This coffee style isn't for them
- Note: -[origin], -[processing], -[flavor notes] (with lower confidence)

### If Rating ≤ 2 but Brewing Issues:
- **Discount the negative signal** — brewing problems, not coffee problems
- Note: "Inconclusive due to brewing issues"

### If Dial-in Attempt (not first try):
- Track improvement trajectory
- If improving: They're learning this coffee
- If not improving: Maybe the coffee isn't for them

## Step 6: Write to Feedback Log

Append a new entry to `coffee/feedback-log.md`:

```markdown
---

## Entry [N] — [YYYY-MM-DD]

### Coffee
- **Name:** [name]
- **Roaster:** [roaster]
- **Origin:** [origin]
- **Roast:** [level]
- **Process:** [washed/natural/honey]
- **Price:** ₹[price]/[weight]
- **Source:** [Recommended / Manual entry — how discovered]

### Brewing Context
- **Method:** [method]
- **Grind:** [size]
- **Ratio:** [ratio]
- **Temp:** [temp]
- **Issues:** [none / describe]

### Attempt
- **Attempt #:** [1/2/3...]
- **vs Previous:** [if applicable]

### Feedback
- **Rating:** [⭐⭐⭐⭐ 4/5]
- **Flavor notes:** [what they tasted]
- **Matches roaster notes?:** [yes/no/partially]
- **Repurchase:** [Yes/Maybe/No]
- **Notes:** [free-form]

### Preference Signals
- [+/-] [signal with confidence]
```

## Step 7: Check for Consolidation

Count total entries in `coffee/feedback-log.md`. If there are 10+ entries since last consolidation:

> You've logged 10 coffees since I last analyzed patterns. Want me to consolidate and update your preference profile?

If yes, generate a consolidation summary:

```markdown
---

## Consolidation Summary — [Date Range]

**Coffees logged:** 10
**Average rating:** [X.X]

### Emerging Patterns
- [Pattern 1: e.g., "Strong preference for Ethiopian naturals (4 tries, avg 4.5)"]
- [Pattern 2: e.g., "Medium roast consistently preferred over light"]
- [Pattern 3: e.g., "Blue Tokai quality reliable across 3 purchases"]

### Adjustments to Profile
- Increased [preference] confidence to [High/Medium]
- Decreased [preference] confidence to [Low]
- Added [new preference discovered]
- Removed [preference that data doesn't support]

### Roaster Notes
- [Roaster]: [quality/reliability observations]
```

Then update `coffee/profile.md` with the new confidence levels and any discovered preferences.

## Step 8: Confirmation

After logging:

> Got it! I've logged your feedback for [Coffee Name].
>
> **Quick summary:**
> - Rating: [stars]
> - Key notes: [their flavor notes]
> - Repurchase: [intent]
>
> This helps me refine your recommendations. [If consolidation due: "I'll analyze patterns after a few more entries."]
