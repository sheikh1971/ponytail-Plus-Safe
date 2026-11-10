# ponytail-Plus

> Unofficial. Not affiliated with or endorsed by Ponytail or its author.

Production-safe coding rules for AI coding agents. Write the least code that works, reuse what already exists, test every change, and never cut safety, security or least privilege.

Inspired by [Ponytail](https://github.com/DietrichGebert/ponytail), Andrej Karpathy's coding guidelines and [obra/superpowers](https://github.com/obra/superpowers), then customized for real production and regulated (medical, financial) code.

## What is different

| | Ponytail-style minimal coding | ponytail-Plus |
|---|---|---|
| Least code, reuse first, prefer delete | yes | yes |
| Tests | small changes may skip | **every change gets a test**; bug fixes get a failing test first |
| Domain safety (medical, financial) | general never-cut list | safety checks, "unclear" marking, disclaimers, audit records never cut |
| Cloud and CI | not covered | **least privilege**; never broaden a role to make something pass |
| Production changes | not covered | rollback first, change additively, verify, then remove the old |
| Secrets | not covered | never read or print secrets |
| Hooks, scripts, telemetry | session hooks, optional webhook | **none**: one Markdown file, nothing runs, nothing leaves your machine |
| Report | what was skipped | what changed + what was skipped or not checked |

## Install (Claude Code)

```
/plugin marketplace add sheikh1971/ponytail-Plus
/plugin install ponytail-plus@ponytail-plus
```

The skill turns on by itself for coding tasks. You can also call it directly with `/ponytail-plus:ponytail-plus`.

## Other agents

The rules are plain Markdown in [`skills/ponytail-plus/SKILL.md`](skills/ponytail-plus/SKILL.md). Copy the body into your agent's rules file (for example `AGENTS.md`, `.cursorrules` or `.github/copilot-instructions.md`).

## The rules in short

1. Read first, state assumptions, ask when unclear.
2. List every place the change must reach.
3. Pick the first option that works: skip, reuse, standard library, installed dependency, then minimum new code.
4. No speculative code. Prefer deleting. Surgical changes only.
5. Never cut validation, data-loss protection, security, privacy, domain safety, accessibility.
6. Every change gets a test. Run the checks. Never claim what was not run.
7. Least privilege in cloud and CI. Safe production rollouts.
8. End with what changed and what was not checked.

## License

MIT © 2026 Mohammad Ariful Islam
