# skill-methodology-absorb

> A WorkBuddy / Claude Code skill for safely absorbing the methodology of open-source skills (Claude/WorkBuddy Skills on GitHub) into your own skills.

## Introduction

When you "absorb" someone else's skill into your own, the biggest risk is not technical — it's design. Mount a module in the wrong place and your main file bloats; hard-merge two skills and their trigger phrases pollute each other. This skill distills a complete engineering discipline for methodology absorption: mirror downloading, full read-throughs, three-list analysis, a hard-merge feasibility framework, iron rules for lazy-load mount points, a main-file size budget, and a pre-delivery verification checklist — all expressed as executable rules and commands.

The skill triggers automatically when the user asks things like:

- "Merge that skill into mine"
- "Absorb this skill's capabilities"
- "Can these two skills be combined?"
- "Help me rework my skill"

Coverage: mirror downloading, a hard-merge feasibility framework, lazy-load mount-point rules, main-file size budgeting, and a pre-delivery verification checklist.

## Features

- **Five Iron Rules** — violate any one and the work must be redone:
  - Modules may only hang on "optional branches," never on the "mandatory path" (otherwise it's fake lazy loading)
  - Check three conflicts before any hard merge (trigger pollution / deliverable conflict / context budget)
  - A strict size budget for the main file (record bytes before, set a hard cap, measure after)
  - Backup policy (skipped by default; only when the user explicitly asks, and never inside the skills directory)
  - Line endings must be normalized after writing (Python text-mode writes on Windows turn LF into CRLF, inflating file size)
- **Five-step standard workflow**: fetch the source skill → read everything and build three lists → present three options for the user to choose → execute per the iron rules → verify item by item before delivery
- **Hard-merge feasibility framework**: if any of the three conflicts holds, abandon "merge into one" and switch to "capability absorption + independent coexistence"
- **Lazy-load mount-point rules**: content that is "always needed" gets compressed and inlined into the main file; "conditionally needed" content becomes standalone optional modules; "historical documents" are always externalized
- **Pre-delivery verification checklist**: file inventory and line endings, main-file size, frontmatter fields, new content in place, paired code fences, original content preserved — everything measured, nothing assumed
- **License & attribution guidance**: check the license before absorbing open-source content and credit the original author in the target skill (e.g., `Methodology adapted from @XXX (MIT)`)

## How It Works

### The Three-Conflict Check (Iron Rule #2)

| Conflict | How to check | Consequence |
|---------|--------------|-------------|
| Trigger pollution | Put both skills' description trigger phrases side by side; look for overlap or inclusion | A request for scenario A gets routed into workflow B |
| Deliverable conflict | What does each skill ultimately produce? Are the forms mutually exclusive (e.g., document vs code)? | Instructions fight each other after a hard merge |
| Context budget | Add up the total size of both skills and compare with the target skill's current size | The main file explodes and trigger quality drops |

### The Three Options (Step 3)

- **Option A: capability absorption + independent coexistence** (usually best)
- **Option B: deep merge into a single skill** (usually not recommended)
- **Option C: a skill family with a master router** (mid-term evolution)

### The Three Lists (Step 2)

1. **Overlap** — what both sides already do (pick the better one and unify)
2. **Complement** — what one has and the other lacks (the real value of merging)
3. **Conflict** — reasons a hard merge won't work (see Iron Rule #2)

## Installation & Usage

Copy the contents of this repository into your skills directory, keeping the folder name `skill-methodology-absorb`:

- WorkBuddy / CodeBuddy: `~/.workbuddy/skills/skill-methodology-absorb/`
- Claude Code: `~/.claude/skills/skill-methodology-absorb/`

Restart the session and the skill will match automatically via its trigger phrases.

Two practical commands the skill uses along the way:

```bash
# Shallow-clone the source skill through a mirror when GitHub is unreachable
git clone --depth 1 https://ghfast.top/https://github.com/<user>/<repo>.git
# Fallback mirror: https://gh-proxy.com/https://github.com/...
```

```python
# A .skill file is really a zip; extract it to inspect the internals
import zipfile
zipfile.ZipFile(r'xxx.skill').extractall('extracted')
```

## Project Structure

```
skill-methodology-absorb/
├── SKILL.md      # The skill: five iron rules + five-step workflow + verification checklist + lessons learned
├── README.md     # Chinese README
└── README_EN.md  # This file
```

## Notes

- **Line-ending checks are non-negotiable**: Python text-mode writes on Windows convert `\n` to `\r\n`, adding one byte per line and potentially faking a "budget exceeded" verdict. Always run the line-ending detection script after edits (built into SKILL.md).
- **Never back up inside the skills directory**: any subdirectory of `~/.workbuddy/skills/` containing a SKILL.md gets scanned as a duplicate skill. Backups must live outside the skills directory, and you should verify MD5 equality before making changes.
- **No backups by default**: the backup step was explicitly retired by the user on 2026-09-30; only back up when the user asks for it.
- **Externalizing historical logs** is the fastest way to free up space in the main file.
- **Verify item by item before delivery** — never rely on "it should be fine." If something is over budget or flawed, say so honestly and fix it.

## License

MIT (declared in the `SKILL.md` frontmatter)

## Author

sheen945
