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

```bash
npx skills add joshuaboys/agent-sitrep
```

For a specific agent:

```bash
npx skills add joshuaboys/agent-sitrep -a codex
npx skills add joshuaboys/agent-sitrep -a cursor
npx skills add joshuaboys/agent-sitrep -a claude-code
```

Or manually copy `skills/sitrep/SKILL.md` into your agent's skills directory.

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

MIT
