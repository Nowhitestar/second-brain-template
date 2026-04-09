# Skill: /writing — Writing Mode

## Trigger
User says: "writing" or `/writing`

## Goal
Load user's writing style rules, methodologies, and examples, then execute writing tasks in the user's voice.

## Steps
1. Read System/working-memory/OPERATING_RULES.md "writing rules" section for style rules
2. Determine which style based on writing task nature:
   - Serious/technical/analytical → Report style
   - Essay/personal/casual → Essay style
3. Ask user for specific writing task requirements
4. Execute writing in the appropriate style

## Report Style Guidelines
- Open with direction, clear structure, use tables/numbered lists
- Define before discussing, cite with source and context
- Have a personal stance, avoid empty praise

## Essay Style Guidelines
- Start from detail, conversational tone, short sentences
- Self-deprecation as a regular tool, lucid with slight detachment
- Write sadness without melodrama, don't force neat endings

## Both Styles Prohibit
- Empty modifiers: "core", "empower", "drive", "showcase"
- "It's not... but rather..." constructions
- "In summary", "To conclude"

## Interaction Flow
```
Writing Mode Activated
━━━━━━━━━━━━━━━
Style loaded: Report / Essay (auto-detected based on task)

Describe your writing task:
- Topic:
- Target audience:
- Expected length:
- Special requirements:
```
