---
name: tee-time
description: "Plan a golf day with weather-first recommendations."
---

# Tee Time

## Overview

Given a target date or "when should I golf next", this skill fetches weather for the next 5-7 days and recommends the best window for a round. It checks Woodbury, MN weather (closest to Lake Elmo) and can optionally look up nearby courses.

## Weather Priority (Decision-Weighted)

| Factor | Weight | Notes |
|--------|--------|-------|
| Precipitation | High | No rain/lightning in forecast window |
| Wind | Medium | >15 mph is a dealbreaker for enjoyment |
| Temperature | Low | >50F is playable, >60F is good |
| UV/Cloud | Low | Sunny >50F beats rainy 70F every time |

## Workflow

1. Determine target date or date range from user prompt.
2. Check weather for Lake Elmo / Woodbury, MN for the next 5-7 days.
3. Score each day 1-5 on golf-playability.
4. Recommend top 2 windows with reasons.
5. If asking about a specific course, optionally pull ratings from Google Maps.

## Output Format

```
Best days: Mon (5/18) and Wed (5/20)
Mon: 68F, 8mph WNW - Great day
Wed: 71F, 12mph SW - Good, slightly windy
Avoid: Tue (light rain), Thu (20mph gusts)
```

## Requirements

- Web access for weather and course info
- No credentials needed
