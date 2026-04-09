# Skill: /maintain — Health Check

## Trigger
User says: "maintain" or `/maintain`

## Goal
Full vault health scan: structure check + content check + weaving progress, output diagnostic report.

## Steps

### Structure Check
1. Scan all main directories (Inbox, Projects, Areas, Resources, Wiki, Archives, Identity, System)
2. Check each directory has a README.md
3. Check README member lists match actual files
4. Check if Inbox has content older than 30 days

### Content Check
5. **Island detection**: Find zero-inlink notes, judge if they have value
6. **Staleness detection**: Scan notes with status: active and updated > 180 days ago
7. **Broken links**: Scan [[bidirectional links]] pointing to non-existent files
8. **Emptiness detection**: Directories with empty member lists
9. **Redundancy detection**: Notes with highly similar titles (>80% similarity)

### Weaving Progress Check
10. Read `System/weaving-tracker.md`, calculate:
    - Total files / woven / not yet woven
    - Completion rate by domain
    - Identify high-value unwoven files (prioritize)

### Wiki Health Check
11. Check Wiki page `sources` fields point to existing Resources files
12. Check Wiki page `updated` dates are not behind their sources' latest update

## Output Format
```
Health Scan Report
━━━━━━━━━━━━━━━
📊 Overall Status: [Healthy/Warning/Critical]

📈 Weaving Progress
- Woven: X / Y (X%)
- By domain: Domain1 X% | Domain2 X% | ...

✅ Healthy Items
- [items]

⚠️ Warnings
- [description] → [suggested action]

🔴 Critical Issues
- [description] → [suggested action]

🏝️ Island Notes (valuable but zero inlinks)
- [file] → suggest linking to [[Wiki/xxx]]

Pending Actions
- [issue] | Priority: [high/medium/low]
```
