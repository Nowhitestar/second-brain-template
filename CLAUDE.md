# Second Brain Template

## Startup Checklist
On session start:
1. Read Identity/CONTEXT.md for current state
2. Check System/working-memory/tasks.md for pending tasks
3. Check System/pending_approvals.md for pending approvals
4. Output knowledge base health summary (file count, warnings)

## Document Organization
- Bidirectional links: use [[filename]] to create links between documents
- Tag system: use #tags for classification and retrieval
- Frontmatter: add YAML metadata at the top of each document
- Prefer tags and links over deep folder hierarchies

## Memory Rules
- User says "note this" or "remember": preserve original text, don't add TODOs or rewrite
- Important decisions and stable preferences → append to Identity/PROFILE.md (after approval)
- Daily work records → write to System/working-memory/daily/{date}.md
- Modifying Identity files → must notify user

## Safety
- Notify user of specific changes after modifying Identity files
- Never store passwords, API keys, or sensitive info in any file
