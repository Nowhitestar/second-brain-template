# Skill: /intake — Knowledge Weaving Workflow

## Trigger
User says: "intake" or `/intake`

## Goal
Scan Inbox, archive raw materials into Resources/, then weave insights into Wiki/ (organized by entity/concept/analysis/overview, not by source domain).

---

## Steps

### Step 1 — Scan Inbox
List all files in `Inbox/` (excluding README.md).
If empty, output "No files to process" and stop.

### Step 2 — Archive Raw Materials to Resources/

For each file:
1. Read content, determine domain (customize domains to your needs)
2. Add frontmatter (para: resource, domain, type, tags, summary)
3. Move to `Resources/<domain>/`
4. Update `Resources/<domain>/README.md` member list

Resources is an immutable raw material layer — preserve original text, no modifications.

### Step 3 — Knowledge Weaving (Core Step)

Read `Wiki/index.md` first to locate related pages, then:

**3a. Named Entity Recognition**
Does the new content reference specific named entities (protocols, people, companies, projects)?
- Yes → Find or create `Wiki/entities/<entity-name>.md`, append new info, update cross-references

**3b. Core Concept Identification**
Does the new content carry independently-standing concepts or frameworks? (often cross-domain)
- Yes → Find or create `Wiki/concepts/<concept-name>.md`, integrate new perspectives
- If a concept spans multiple domains, note the cross-domain connections in the page

**3c. Analysis Output**
If conversation with user produced valuable analytical conclusions:
- File to `Wiki/analyses/<analysis-title>.md`

**3d. Overview Update**
If new content significantly expands coverage of a domain:
- Update `Wiki/overviews/<domain>-Overview.md`

**Page creation principles**:
- Entity: every named entity deserves a page
- Concept: wait for 3+ Resources before creating a page, otherwise accumulate
- Analysis: every good conversation can file back
- Overview: one per major domain, create when coverage is sufficient

### Step 4 — Update Tracking & Index

1. **Weaving tracker**: Mark processed Resources files as done in `System/weaving-tracker.md`, note contributed Wiki pages
2. **Global index**: Update `Wiki/index.md` with new/updated Wiki page entries
3. **Operation log**: Append to `System/log.md`

### Step 5 — Feedback Loop Check
- L3: Is new file metadata complete?
- L2: Has directory README been updated?
- L1: Has directory structure or classification system changed?

---

## Wiki Page Frontmatter Standard

```yaml
---
type: entity | concept | analysis | overview
sources:
  - Resources/Domain/xxx.md
  - Resources/Domain/yyy.md
updated: YYYY-MM-DD
summary: One-line description, used by AI to judge relevance
---
```

## Output Format

```
Intake + Weaving Complete
━━━━━━━━━━━━━━━
✅ Resources/
  - file1.md → Resources/Domain/

🕸️ Wiki Weaving
  - Wiki/entities/Example.md (updated)
  - Wiki/concepts/Example-Concept.md (new, references Domain1 + Domain2)

📋 index.md updated

Pending
  - file2.md: [needs user decision on classification]
```
