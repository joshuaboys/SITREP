# agent-sitrep

> Drop the filler. Keep the facts.

A skill for Claude Code, Codex, Cursor, and other coding agents that switches responses to structured SITREP-style output — terse, accurate, scannable.

Based on the observation that brevity constraints reduce token usage without losing technical substance. Unlike caveman-speak, SITREP mode keeps full grammar and structured fields — better fit for professional engineering contexts.

---

## Modes

| Mode | Trigger | Style |
|---|---|---|
| **Brief** | `/brief` | Prose minus filler and hedging |
| **SITREP** | `/sitrep` | Structured fields: SITUATION / ACTION / STATUS / NEXT |
| **Flash** | `/flash` | One line per point, maximum compression |

Stop with: `/normal`

---

## Install

Copy `skills/sitrep/SKILL.md` into your agent's skills directory.

**Claude Code:** `.claude/skills/sitrep/SKILL.md`
**Codex:** `.codex/skills/sitrep/SKILL.md`
**Cursor:** `.cursor/skills/sitrep/SKILL.md`

Or wherever your agent loads skills from.

---

## Example

**Normal:**
> Sure! The reason your build is failing is most likely because the TypeScript compiler can't find the module declaration. I'd recommend checking your tsconfig.json paths configuration.

**`/brief`:**
> Build failing: TypeScript can't find the module declaration. Check tsconfig.json paths.

**`/sitrep`:**
```
SITUATION: Build failing
ACTION:    Investigated — TypeScript module resolution error
STATUS:    COMPLETE — check tsconfig.json paths
```

**`/flash`:**
```
Build failing — TS module resolution
Check tsconfig.json paths
```

---

## Token Savings vs Baseline

Estimated output token reduction compared to standard Claude Code responses. Based on response structure analysis across common engineering tasks.

| Task type | Brief | SITREP | Flash |
|---|---:|---:|---:|
| Bug diagnosis | 25% | 50% | 65% |
| Implementation status update | 30% | 60% | 70% |
| Code review feedback | 20% | 45% | 60% |
| Architecture explanation | 15% | 40% | 55% |
| Error investigation | 30% | 55% | 70% |
| PR description / commit summary | —\* | —\* | —\* |
| **Average** | **~25%** | **~50%** | **~65%** |

\* Git commits and PR descriptions are always written in normal prose regardless of mode.

> Savings come entirely from output tokens. Input tokens are unaffected.

---

MIT
