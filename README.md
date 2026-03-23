# Awesome Claude Code Skills

Skills that fix common AI agent blind spots.

AI agents have blind spots. These skills fix them.

## AI doesn't run code

Claude Code reads code but doesn't execute it. Tests can silently skip, smoke scripts can exit 0 without verifying anything, and security gates can check the wrong env var -- all invisible to a read-only review.

- [adversarial-audit](https://github.com/jkgdq789-blip/adversarial-audit-skill) -- Makes Claude execute every test and smoke script the repo claims to have, then check skip counts and assert statements.
- [verify-by-execution](https://github.com/jkgdq789-blip/verify-by-execution-skill) -- 6 rules that stop Claude from saying "looks correct" without running it. Requires execution proof for every conclusion.

## AI reviews files in isolation

Claude reviews `auth.ts` and says it looks fine. Reviews `ws-relay.ts` and says it looks fine. But the bug is in the handoff between them -- a stale token, a unit mismatch, a missing event subscription.

- [trace-interaction](https://github.com/jkgdq789-blip/trace-interaction-skill) -- Tells Claude to follow data from entry point through every downstream consumer. Finds bugs that live between files.

## AI checks one thing at a time

Claude picks one angle per review -- maybe types, maybe logic, maybe naming. It does not systematically check all of them in one pass.

- [seven-lens-review](https://github.com/jkgdq789-blip/seven-lens-review) -- Forces 7 overlapping checks (contracts, state, boundaries, security, consistency, dead code, test gaps) in a single pass.

## How to install any skill

```bash
cp SKILL.md ~/.claude/commands/<skill-name>.md
```

Then use `/<skill-name>` in Claude Code.

## Contributing

PRs welcome. Add your skill with a one-line description of what blind spot it fixes.
