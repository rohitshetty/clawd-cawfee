# Clawd Cawfee

A Claude Code-powered system for discovering and tracking specialty coffee in the Indian market.

## What This Does

- `/know-me` — Build a preference profile (equipment, flavors, budget, trusted roasters)
- `/find-me-coffee` — Get recommendations based on profile + Reddit sentiment
- `/feedback-log` — Log coffee experiences to refine preferences
- `/coffee-stats` — View analytics on your coffee journey

## Key Files

- `coffee/profile.md` — User preferences (built by /know-me)
- `coffee/feedback-log.md` — Logged coffee experiences
- `.claude/commands/` — Slash command definitions

## How Recommendations Work

Scoring: 60% preference match + 40% community sentiment (Reddit).
Freshness enforced — only roast-to-order roasters.
Constraints relax gracefully if no perfect matches exist.

## Communication Style

- Skip obvious observations — assume I already know the basics
- Be direct and helpful, not patronizing
- No excessive enthusiasm or cheerfulness
- Get to the point
