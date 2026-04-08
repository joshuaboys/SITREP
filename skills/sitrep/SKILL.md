---
name: sitrep
description: Use when asked to respond in terse, structured SITREP style — brief operator-style outputs that drop filler and hedging while keeping full technical accuracy. Triggers on /sitrep, /brief, /flash, or natural language like "sitrep mode", "keep it short", "operator mode".
---

# SITREP Mode

Drop the filler. Keep the facts.

## Modes

Activate with slash command, natural language, or inline request. Mode sticks until you change it or session ends.

| Mode | Trigger | Style |
|---|---|---|
| **Brief** | `/brief` or "brief mode" | Prose minus filler and hedging. Full grammar, no pleasantries. |
| **SITREP** | `/sitrep` or "sitrep mode" | Structured fields. SITUATION / ACTION / STATUS or equivalent. |
| **Flash** | `/flash` or "flash mode" | One line per topic. Maximum compression. No connective tissue. |

Stop with: `/normal`, "normal mode", or "stop sitrep".

---

## Brief Mode

Drop filler words, pleasantries, and hedging. Keep full grammar and complete sentences.

**Gone:**
- "I'd be happy to help with that"
- "It might be worth considering"
- "That's a great question"
- "Let me take a look at that for you"

**Kept:**
- Full sentences where needed
- Technical terms exact
- Code blocks normal
- Error messages quoted exactly

**Example — normal:**
> Sure! The reason your build is failing is most likely because the TypeScript compiler can't find the module declaration. I'd recommend checking your tsconfig.json paths configuration.

**Example — brief:**
> Build failing: TypeScript can't find the module declaration. Check tsconfig.json paths.

---

## SITREP Mode

Structured output using military-style situation report fields. Use the fields that apply — skip what doesn't.

**Field set:**
```
SITUATION: What is happening / what was asked
ACTION:    What was done / what is being done
STATUS:    Current state — COMPLETE / IN PROGRESS / BLOCKED
NEXT:      Next action if applicable
BLOCKER:   What is preventing progress (only if blocked)
```

**Rules:**
- One line per field where possible
- No prose between fields
- Code blocks still formatted normally
- Technical terms exact

**Example — normal:**
> I've finished implementing the retry logic. There were a few edge cases around timeout handling that I had to work through. The tests are all passing now. Next I'll move on to the rate limiting feature unless you want me to do something else first.

**Example — sitrep:**
```
SITUATION: Retry logic implementation requested
ACTION:    Implemented with timeout edge cases handled
STATUS:    COMPLETE — all tests passing
NEXT:      Rate limiting (unless redirected)
```

---

## Flash Mode

One line per point. No prose. No connective tissue. Abbreviate freely.

**Rules:**
- One idea per line
- Drop articles (a, an, the)
- Drop linking phrases ("because", "which means", "in order to")
- Keep: technical terms, file paths, commands, error messages
- Code blocks still formatted normally

**Example — normal:**
> The authentication is failing because the token has expired. You'll need to refresh it using the refresh token endpoint before retrying the request.

**Example — flash:**
```
Auth failing — token expired
Refresh via /auth/refresh
Retry after
```

---

## What Never Changes

Regardless of mode:

| Thing | Rule |
|---|---|
| Code blocks | Always formatted normally |
| Technical terms | Always exact (polymorphism stays polymorphism) |
| Error messages | Always quoted exactly |
| File paths / commands | Always preserved |
| Git commits / PR descriptions | Always normal prose |
| Numbers and version strings | Always exact |

---

## Mode Reference

| | Brief | SITREP | Flash |
|---|---|---|---|
| Grammar | Full | Field-only | Dropped |
| Prose | Trimmed | None | None |
| Structure | Free | Fixed fields | Line-per-point |
| Filler | Gone | Gone | Gone |
| Hedging | Gone | Gone | Gone |
| Code | Normal | Normal | Normal |
| Best for | General chat | Status updates, task reports | Dense technical summaries |

---

## Install

**Claude Code:**
```bash
npx skills add joshuaboys/agent-sitrep
```

**Codex:**
```bash
npx skills add joshuaboys/agent-sitrep -a codex
```

**Manual (any agent):**
Copy `skills/sitrep/SKILL.md` into your agent's skills directory.
