# Folder Structure Guide

> How to organize your Cowork folder so governance actually works.

Cowork asks you to "give Claude access to a folder." But it doesn't tell you how to structure that folder. This matters more than you think.

Without clear structure:
- Files multiply and contradict
- Claude references the wrong version
- You lose track of what's authoritative
- Drift becomes invisible

The filesystem IS your governance layer. Treat it that way.

---

## Recommended Structure

```
cowork-folder/
│
├── 00-governance/
│   ├── RUNNING-DOCUMENT.md      ← Session continuity
│   ├── CANONICAL-NUMBERS.md     ← Numeric truth
│   └── FAILURE-RECOVERY.md      ← What to do when things break
│
├── 01-inputs/
│   ├── raw/                     ← Unprocessed files you give Claude
│   └── reference/               ← Source materials Claude can read
│
├── 02-working/
│   └── [active work files]      ← Where Claude does the work
│
├── 03-outputs/
│   ├── drafts/                  ← Work in progress
│   └── final/                   ← Approved, complete work
│
└── 04-archive/
    └── [old files, deprecated]  ← Out of play but preserved
```

---

## Folder Purposes

### `00-governance/`

The control layer. Claude reads these first, every session.

- Never put working files here
- These files govern — they don't get governed

### `01-inputs/`

What you give Claude to work with.

- `raw/` — unprocessed uploads (receipts, screenshots, dumps)
- `reference/` — source materials, background docs, context

### `02-working/`

Where active work happens.

- Claude creates and edits files here
- Treat everything here as in-progress
- Move to outputs when complete

### `03-outputs/`

Finished work.

- `drafts/` — awaiting your review
- `final/` — approved and complete

Nothing goes to `final/` without your explicit approval.

### `04-archive/`

Out of play.

- Deprecated files
- Old versions
- Completed projects

Claude should not reference archived files unless explicitly asked.

---

## Rules

1. **Governance files live in `00-governance/`** — always read first
2. **One canonical version per file** — no duplicates across folders
3. **Working files stay in `02-working/`** — don't let them leak
4. **Nothing is final until you say so** — `final/` requires approval
5. **Archive, don't delete** — preserve history in `04-archive/`
6. **Name files clearly** — `report-v2-DRAFT.md` not `report.md`

---

## Naming Conventions

Use clear, consistent naming:

```
[project]-[type]-[version]-[status].md

Examples:
expenses-q1-v1-DRAFT.md
expenses-q1-v2-FINAL.md
research-notes-v1-WORKING.md
```

Status tags:
- `WORKING` — in progress
- `DRAFT` — ready for review
- `FINAL` — approved
- `DEPRECATED` — no longer active

---

## Session Start Prompt

Point Claude to the structure:

> "Our folder uses this structure: `00-governance/` contains RUNNING-DOCUMENT.md and CANONICAL-NUMBERS.md — read those first. Active work goes in `02-working/`. Final outputs go in `03-outputs/final/` only with my approval. Do not reference files in `04-archive/` unless I ask."

---

## Common Mistakes

| Mistake | Why It Hurts | Fix |
|---------|--------------|-----|
| Governance files mixed with working files | Claude treats them equally | Separate `00-governance/` folder |
| Multiple versions of same file | Claude picks the wrong one | One canonical version, archive the rest |
| No clear final folder | Everything feels in-progress | Explicit `final/` with approval gate |
| Deleting old files | Lose history, can't trace decisions | Archive, don't delete |
| Vague filenames | Confusion about status and version | Use naming convention with status tags |

