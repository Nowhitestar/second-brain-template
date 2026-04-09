[English](README.md) · [中文](README.zh.md)

# Second Brain Template

[![Obsidian](https://img.shields.io/badge/Obsidian-483699?style=flat&logo=obsidian&logoColor=white)](https://obsidian.md)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat&logo=anthropic&logoColor=white)](https://claude.ai/code)
[![PARA Method](https://img.shields.io/badge/PARA-Method-4CAF50?style=flat)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

An AI-augmented personal knowledge management system built on **Obsidian** and **Claude Code**. It uses the PARA method for organization, a layered Wiki for knowledge weaving, and AI-driven contextual retrieval — so your notes become a working memory that grows with you.

---

## The Problem

You collect notes, bookmarks, highlights, and ideas — but they sit in folders and never connect. When you need them, you can't find them. When you find them, they lack context.

This template solves that by giving you:

1. **A clear structure** — PARA separates actionable work from reference material
2. **A knowledge layer** — Wiki weaves raw materials into entities, concepts, and analyses
3. **An AI layer** — Claude Code understands your knowledge graph and retrieves relevant context automatically

> Think of it as a memory palace where AI is your librarian.

---

## What You Get

```
Second Brain/
├── Inbox/                  # Capture everything here first
├── Projects/               # Active work with deadlines
├── Areas/                  # Ongoing responsibilities (no end date)
├── Resources/              # Raw materials — articles, reports, notes
├── Archives/               # Completed or paused items
├── Identity/               # Who you are — mission, context, preferences
│   ├── TELOS.md            # Your purpose and goals
│   ├── CONTEXT.md          # Current focus and active projects
│   └── PROFILE.md          # Communication style and preferences
├── System/                 # Operational support
│   └── working-memory/     # Tasks, daily logs, operating rules
│       ├── tasks.md
│       ├── OPERATING_RULES.md
│       └── daily/          # Daily interaction logs
├── Wiki/                   # Woven knowledge (the real value)
│   ├── index.md            # Knowledge map — entry point for AI retrieval
│   ├── entities/           # People, companies, projects (concrete things)
│   ├── concepts/           # Ideas, frameworks, methodologies (abstract things)
│   ├── analyses/           # Deep-dive research reports
│   └── overviews/          # Domain landscape surveys
└── .claude/
    └── CLAUDE.md           # AI system prompt — the brain's operating system
```

---

## How It Works

### 1. Capture

Save anything to `Inbox/` or `Resources/`. Articles, meeting notes, random thoughts — don't organize yet, just capture.

### 2. Weave

AI processes raw materials and weaves them into the Wiki:

```
Raw article about EigenLayer (Resources/)
        ↓ AI processes
Wiki/entities/EigenLayer.md      — structured entity page
Wiki/concepts/Restaking.md       — concept extraction
Wiki/analyses/EigenLayer-Thesis  — investment analysis
        ↓ AI connects
[[EigenLayer]] ←→ [[Ethereum]] ←→ [[DeFi-Core-Concepts]]
```

Each Wiki page includes:
- **Frontmatter** with source tracking, tags, and creation date
- **Bidirectional links** connecting related knowledge
- **Source attribution** back to raw materials in Resources/

### 3. Retrieve

When you ask a question, AI follows a retrieval path:

```
You: "What's the investment thesis for EigenLayer?"
        ↓
AI reads Wiki/index.md → finds [[entities/EigenLayer]]
        ↓
AI reads the entity page → follows links to analyses, concepts
        ↓
AI responds using YOUR knowledge, not generic training data
```

### 4. Evolve

The system maintains itself:
- **Frontmatter consistency** — metadata stays in sync with file locations
- **Index updates** — Wiki/index.md reflects current knowledge
- **Knowledge smells** — AI detects orphaned notes, stale content, broken links
- **Identity tracking** — preferences and operating rules accumulate over time

---

## Prerequisites

### Required

| Tool | Purpose | Install |
|------|---------|---------|
| [Obsidian](https://obsidian.md) | Local-first knowledge vault | Download from official site |
| [Claude Code](https://claude.ai/code) | AI layer — powers retrieval, weaving, and maintenance | `npm install -g @anthropic-ai/claude-code` |

### Required Claude Code Plugin

| Plugin | Purpose | Install Command |
|--------|---------|-----------------|
| [obsidian-skills](https://github.com/kepano/obsidian-skills) | Obsidian Flavored Markdown, JSON Canvas, and Bases format support | `/plugin marketplace add kepano/obsidian-skills && /plugin install obsidian@obsidian-skills` |

### Recommended Claude Code Plugins

| Plugin | Purpose | Install Command |
|--------|---------|-----------------|
| [superpowers](https://github.com/anthropics/claude-code-plugins) | Enhanced planning, debugging, and task management skills | `/plugin install superpowers@claude-plugins-official` |

### Built-in Skills

This template ships with four custom skills in `System/skills/` that power the core workflows:

| Skill | Trigger | What It Does |
|-------|---------|-------------|
| **intake** | `/intake` or "intake" | Scans Inbox → archives to Resources/ → weaves knowledge into Wiki/ |
| **maintain** | `/maintain` or "maintain" | Full vault health scan: structure, content, weaving progress |
| **digest** | `/digest` or "digest" | Reviews AI-observed preference candidates for user approval |
| **writing** | `/writing` or "writing" | Loads your writing style rules, then writes in your voice |

These skills are plain Markdown files — edit them to match your workflow.

### Recommended Obsidian Plugins

| Plugin | Purpose |
|--------|---------|
| **Dataview** | Query and display note metadata |
| **Templater** | Advanced templates for new notes |
| **QuickAdd** | Fast capture workflows |
| **Graph Analysis** | Visualize knowledge connections |

---

## Quick Start

### Step 1: Clone

```bash
git clone https://github.com/Nowhitestar/second-brain-template.git "My Second Brain"
```

### Step 2: Open in Obsidian

1. Open Obsidian → "Open folder as vault"
2. Select the cloned directory
3. Enable community plugins (for Dataview, Templater, etc.)

### Step 3: Install Claude Code Plugins

```bash
# Navigate to your vault
cd "My Second Brain"

# Required: Obsidian format support
/plugin marketplace add kepano/obsidian-skills
/plugin install obsidian@obsidian-skills

# Recommended: Enhanced planning & debugging
/plugin install superpowers@claude-plugins-official
```

### Step 4: Configure Your Identity

The `.claude/CLAUDE.md` file is pre-configured. Customize it:

1. Edit `Identity/TELOS.md` — define your mission and goals
2. Edit `Identity/CONTEXT.md` — describe your current focus
3. Edit `Identity/PROFILE.md` — set your communication preferences

### Step 5: Start Using

```bash
# Open Claude Code in your vault directory
claude

# Try these:
# "Help me organize my Inbox"
# "What do I know about [topic]?"
# "Summarize my active projects"
```

---

## The AI Layer

The `.claude/CLAUDE.md` file turns Claude Code into a knowledge-aware assistant. Key capabilities:

### Contextual Retrieval

AI automatically loads relevant knowledge based on what you're discussing:

```
检索路径 (Retrieval Path):
1. Match topic → PARA directories
2. Read directory README → find member files
3. Match by title and summary
4. Cross-check Resources/ for cross-domain content
5. Search Wiki/index.md → load matching entities/concepts
```

### Three-Layer Memory

| Layer | What | When | Where |
|-------|------|------|-------|
| **Daily fragments** | Conversation logs | Auto, per session | `System/working-memory/daily/` |
| **Weekly distillation** | Pattern recognition | Weekly trigger | Candidate pool |
| **Stable preferences** | Confirmed habits | User approval | `Identity/PROFILE.md` |

### Knowledge Weaving Workflow

```
Inbox/Resources → AI processes → Wiki/ (entities, concepts, analyses)
                                   ↓
                         index.md updated
                                   ↓
                    Bidirectional links created
                                   ↓
                      Frontmatter validated
```

### Change Control

| Type | Action | Approval |
|------|--------|----------|
| **A** | File archiving, tag completion, README sync | Auto |
| **B** | Identity changes, new categories | Required |
| **C** | Top-level directory changes, system prompt changes | Required |

---

## Customization

### Adapt the PARA Structure

Edit the README.md in each PARA directory to match your domains. The template provides a starting point — rename, add, or remove directories as needed.

### Customize Retrieval

Edit the `<RETRIEVAL>` section in `.claude/CLAUDE.md` to change search priorities. For example, if you work primarily in one domain, prioritize that directory.

### Add Your Own Wiki Categories

The default Wiki has four categories: entities, concepts, analyses, overviews. Add more if your work requires it (e.g., `decisions/`, `people/`, `tools/`).

---

## Architecture

### Fractal Three-Layer Design

```
L1  .claude/CLAUDE.md       — Global rules (this is L2/L3 folded up)
L2  Directory README.md     — Local map, member list
L3  Note frontmatter        — Content contract, ownership
```

Each layer is self-similar: L1 is L2 compressed, L2 is L3 compressed. Directory READMEs serve as distributed indexes — no separate index file needed (except Wiki/index.md for AI retrieval).

### The Isomorphism Doctrine

> Structure and content must stay in sync. Any change in one must be reflected in the other.

This means:
- Add a file → update the directory README
- Move a file → update frontmatter + old/new READMEs
- Delete a file → update the directory README
- Create a directory → create its README

### Knowledge Smells (Anti-patterns)

| Smell | Description |
|-------|-------------|
| **Island** | Valuable content with no links to other knowledge |
| **Redundancy** | Same idea duplicated across multiple files |
| **Staleness** | Outdated content still marked as active |
| **Chaos** | Large backlog piled up in Inbox |
| **Breakage** | Links pointing to deleted/moved files |
| **Emptiness** | Directory exists but has no README or members |

---

## Safety & Privacy

- **Local-first**: All data stays in your Obsidian vault
- **No cloud dependency**: Works offline, syncs via iCloud/Git
- **Identity protection**: Changes to Identity files require explicit approval
- **Change audit trail**: B/C type changes go through approval queue

---

## Credits

Inspired by:
- [Tiago Forte's PARA Method](https://fortelabs.com/blog/para/)
- [MemPalace](https://github.com/Nowhitestar/openclaw-memory-palace) — the memory palace concept for AI
- [Obsidian](https://obsidian.md) — local-first knowledge management
- [Claude Code](https://claude.ai/code) — AI-powered development

---

## License

MIT License — See [LICENSE](LICENSE) for details.
