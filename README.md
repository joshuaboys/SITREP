# SITREP

> Drop the filler. Keep the facts.

A skill for Claude Code, Codex, Cursor, and other coding agents that switches responses to structured SITREP-style output — terse, accurate, scannable.

Based on the observation that brevity constraints reduce output tokens without losing technical substance. Unlike other implementations of similar ideas, SITREP mode keeps full grammar and structured fields, which is a better fit for professional engineering contexts.

Follows the [Agent Skills](https://agentskills.io) open standard, so the same `SKILL.md` works across Claude Code, Codex, and Cursor.

---

## Modes

Invoke with `/sitrep [mode]`. With no argument, SITREP mode is the default.

| Mode | Trigger | Style |
|---|---|---|
| **Brief** | `/sitrep brief` | Prose minus filler and hedging |
| **SITREP** | `/sitrep` | Structured fields: SITUATION / ACTION / STATUS / NEXT |
| **Flash** | `/sitrep flash` | One line per point, maximum compression |

Stop with: `/sitrep normal`

---

## Install

Copy `skills/sitrep/SKILL.md` into your agent's skills directory.

| Agent | Project scope | User scope |
|---|---|---|
| **Claude Code** | `.claude/skills/sitrep/SKILL.md` | `~/.claude/skills/sitrep/SKILL.md` |
| **Codex CLI** | `.agents/skills/sitrep/SKILL.md` | `~/.agents/skills/sitrep/SKILL.md` |
| **Cursor** | `.cursor/skills/sitrep/SKILL.md` | `~/.cursor/skills/sitrep/SKILL.md` |

Check your agent's current docs if these paths have moved.

---

## Example

**Normal:**
> Sure! The reason your build is failing is most likely because the TypeScript compiler can't find the module declaration. I'd recommend checking your tsconfig.json paths configuration.

**`/sitrep brief`:**
> Build failing: TypeScript can't find the module declaration. Check tsconfig.json paths.

**`/sitrep`:**
```
SITUATION: Build failing
ACTION:    Investigated — TypeScript module resolution error
STATUS:    DIAGNOSED
NEXT:      Check tsconfig.json paths
```

**`/sitrep flash`:**
```
Build failing — TS module resolution
Check tsconfig.json paths
```

---

## Token Savings vs Baseline

Rough estimates of output token reduction versus a normal Claude Code response. Numbers below are **ballpark targets based on the style rules, not a measured benchmark** — actual savings vary with task, context, and how much of the response is code (code blocks are always formatted normally and do not shrink).

| Task type | Brief | SITREP | Flash |
|---|---:|---:|---:|
| Bug diagnosis | ~25% | ~50% | ~65% |
| Implementation status update | ~30% | ~60% | ~70% |
| Code review feedback | ~20% | ~45% | ~60% |
| Architecture explanation | ~15% | ~40% | ~55% |
| Error investigation | ~30% | ~55% | ~70% |
| PR description / commit summary | —\* | —\* | —\* |

\* Git commits and PR descriptions are always written in normal prose regardless of mode, so the skill does not reduce their size.

> Savings come entirely from output tokens. Input tokens (and the skill itself, once loaded) are unaffected. If you need real numbers for a specific workload, measure it on your own task distribution.

---

MIT
