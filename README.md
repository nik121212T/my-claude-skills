# my-claude-skills

Custom Claude Code skills.

## Install

One command — works on Mac, Linux, Windows (Git Bash):

```bash
curl -sSL https://raw.githubusercontent.com/nik121212T/my-claude-skills/main/install.sh | bash
```

Requires `git`. Restart Claude Code after install.

## Update

Same command — re-run anytime to pull latest skills.

## Skills

### `/mini-review`

Silent multi-agent code review. Finds bugs, security issues, and best-practice violations.
Output caveman-compressed, one line per finding, severity-tagged.

```bash
/mini-review                     # current diff
/mini-review src/auth/           # specific path
/mini-review /absolute/path/     # external project
/mini-review --fix               # review + auto-apply CRIT/HIGH fixes
```

Deploys 4 silent parallel agents:
- `bug-hunter` — logic errors, null paths, edge cases
- `security-scanner` — OWASP top 10, XSS, secrets, auth (+ web search)
- `best-practices` — live web search for stack-specific standards
- `arch-probe` — coupling, complexity, god objects

Output format:
```
path:line: 🔴 CRIT: <problem>. <fix>.
path:line: 🟠 HIGH: <problem>. <fix>.
path:line: 🟡 MED:  <problem>. <fix>.
path:line: 🔵 LOW:  <problem>. <fix>.

CRIT: N  HIGH: N  MED: N  LOW: N
```
