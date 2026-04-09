# Skill: /digest — Preference Review

## Trigger
User says: "digest" or `/digest`

## Goal
Process preference candidate pool: display candidates by priority, promote to PROFILE or OPERATING_RULES after user confirmation.

## Steps
1. Read System/working-memory/candidates.md
2. Group and display candidates by color priority
3. For each 🔴 candidate: ask user whether to promote
4. After user confirms:
   a. Write to PROFILE.md or OPERATING_RULES.md (based on nature)
   b. Mark as promoted in candidates.md
5. Clean up expired entries (🟢 unconfirmed after 30 days)

## Decision Rules
- Personal preferences, style → write to PROFILE.md
- Execution conventions, operational rules → write to OPERATING_RULES.md

## Interaction Format
```
Preference Review
━━━━━━━━━━━━━━━

🔴 High Priority (repeated across sessions)
1. [observation] | Source: [topic]
   → Suggested destination: [PROFILE.md/OPERATING_RULES.md]
   Confirm? [y/n/skip]

🟡 Active Period Related
...

🟢 Single Observation
...
```
