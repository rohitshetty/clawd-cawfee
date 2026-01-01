---
description: View analytics and insights about your coffee journey — favorites, spending, preferences evolution
---

# Coffee Stats

You analyze the user's coffee journey and present insights from their profile and feedback history.

## Data Sources

Read both files:
1. `coffee/profile.md` — Preferences and profile data
2. `coffee/feedback-log.md` — All feedback entries

If no profile exists:
> You haven't set up your coffee profile yet. Run `/know-me` to get started!

If profile exists but no feedback:
> Your profile is set up, but you haven't logged any coffee feedback yet. After you try a coffee, use `/feedback-log` to record your experience. Then I can show you insights!

## Analytics to Calculate

### Overview Stats

```markdown
## Your Coffee Journey

### Overview
- **Total coffees tried:** [count unique coffees from feedback log]
- **Total entries:** [count all entries, including dial-in attempts]
- **Unique roasters:** [count]
- **Date range:** [first entry date] → [most recent]
- **Average rating:** [X.X / 5]
```

### Top Performers

```markdown
### Favorites

**Top-Rated Coffees (5 stars):**
1. [Coffee] — [Roaster] — [date]
2. [Coffee] — [Roaster] — [date]

**Most Repurchased:**
1. [Coffee] — [X times]

**Current Wishlist** (high-match coffees not yet tried):
_Based on your recent /find-me-coffee searches, these matched well but you haven't tried them:_
1. [Coffee] — [Roaster] — [match score]%
```

### Preference Analysis

```markdown
### Preference Evolution

**Origins Explored:**
| Origin | Times Tried | Avg Rating | Verdict |
|--------|-------------|------------|---------|
| Ethiopia | 5 | 4.2 | ⭐ Favorite |
| Brazil | 3 | 3.0 | 👍 Decent |
| Colombia | 2 | 2.5 | 👎 Not for you |

**Roast Level Distribution:**
- Light: [X]% of tries, [avg rating]
- Medium: [X]% of tries, [avg rating]
- Medium-Dark: [X]% of tries, [avg rating]
- Dark: [X]% of tries, [avg rating]

**Processing Preference:**
- Washed: [count], avg [rating]
- Natural: [count], avg [rating]
- Honey: [count], avg [rating]
```

### Flavor Profile

```markdown
### Your Flavor Profile

**Most Loved Notes** (from positive reviews):
1. [Note] — appeared in [X] favorites
2. [Note] — appeared in [X] favorites
3. [Note] — appeared in [X] favorites

**Notes to Avoid** (from negative reviews):
1. [Note] — mentioned in [X] dislikes

**Preference Confidence:**
| Preference | Data Points | Confidence |
|------------|-------------|------------|
| Ethiopian naturals | 5 | High |
| Medium roast | 8 | High |
| Fruity notes | 4 | Medium |
| Avoid earthy | 2 | Low |
```

### Roaster Analysis

```markdown
### Roaster Report Card

| Roaster | Tries | Avg Rating | Notes |
|---------|-------|------------|-------|
| Blue Tokai | 4 | 4.3 | Consistent quality |
| Subko | 2 | 4.5 | Excellent but pricey |
| Third Wave | 3 | 3.7 | Hit or miss |
```

### Spending Analysis

```markdown
### Spending Patterns

- **Average price per bag:** ₹[X]
- **Total estimated spend:** ₹[X] (across [N] purchases)
- **Price vs Rating correlation:** [Do you rate pricier coffees higher?]

**Best Value Coffees** (high rating, reasonable price):
1. [Coffee] — ₹[price] — ⭐⭐⭐⭐⭐
2. [Coffee] — ₹[price] — ⭐⭐⭐⭐
```

### Recent Activity

```markdown
### Recent Activity

**Last 5 Coffees:**
1. [Coffee] — [Roaster] — [rating] — [date]
2. ...

**Dial-in Progress:**
_Coffees you're currently dialing in (multiple attempts):_
- [Coffee]: Attempt 1 → 3★, Attempt 2 → 4★ (improving!)
```

## Insights & Recommendations

Based on the data, offer actionable insights:

```markdown
### Insights

💡 **You might like:** Based on your love for [pattern], consider trying [suggestion]

📈 **Improvement:** Your average rating has [increased/decreased] over the last month. [Interpretation]

🎯 **Profile accuracy:** Your feedback [confirms/contradicts] your stated preferences for [X]. [Suggestion to update profile?]

⚠️ **Watch out:** You've rated [roaster] coffees lower than average. Consider removing from trusted list?
```

## Output Format

Present all stats in a clean, readable format. Use tables where appropriate. Include emoji sparingly for visual scanning.

If they haven't logged enough data for meaningful stats:
> You've only logged [N] coffees so far. After about 10 entries, I'll be able to show you more meaningful patterns. Keep logging!

## Follow-up Options

After presenting stats:
> **What's next?**
> - `/find-me-coffee` — Get new recommendations based on these patterns
> - `/know-me` — Update your profile if your tastes have changed
> - `/feedback-log` — Log another coffee

