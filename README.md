# bmad-planning-artifacts

[![Deploy on Back4app](https://img.shields.io/badge/Deploy%20on-Back4app-1568B8?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iI2ZmZiIgZD0iTTEyIDJMMiA3djEwbDEwIDUgMTAtNVY3eiIvPjwvc3ZnPg==)](https://www.back4app.com/signup?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts)

**What the BMAD Method actually writes to disk — a product brief, an architecture spine and their decision logs, produced by the workflows rather than by hand.**  BMAD installs as agent skills and its output is plain Markdown in your repository. This repo is that output, kept verbatim from a real run.

Produced on September 23, 2026 with BMAD **6.13.0-next**, installed by skills CLI 1.7.0: thirteen skills in under **7 seconds** total, and `bmad setup` created `_bmad/` with 19 files. Every number in the article comes from this run.

> **Read the article:** [How to Install and Run the BMAD Method in an AI Editor](https://www.back4app.com/blog/install-and-run-the-bmad-method-in-an-ai-editor?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts)

## What it does

Nothing — it is output, not a program. The point is to see the shape of what BMad produces before you install anything.

```
planning-artifacts/
  briefs/brief-bmad-demo-2026-09-23/
    brief.md          the product brief the workflow wrote
    .memlog.md        the decision log beside it
  architecture/architecture-bmad-demo-2026-09-23/
    ARCHITECTURE-SPINE.md   invariants only
    .memlog.md
```

The memlogs are the part worth looking at twice. The brief says *what* the product is; the memlog records *which alternatives were closed, and when* — the context that normally evaporates when a chat window closes.

## What we measured

| Measurement | Result |
|---|---|
| Skills offered by the repository | 32 |
| Install, 7 skills then 6 more | 3.7 s + 3.3 s |
| `bmad setup` | `_bmad/` with 19 files, 288 KB |
| `lint_spine.py` on the spine here | `{"ok": true, "total_findings": 0}` |
| The same spine, corrupted on purpose | 3 high-severity findings |

A clean pass from a linter that never fires proves nothing, which is why the second row exists.

## Files

- `planning-artifacts/` — the brief, the spine and both memlogs, verbatim.
- `bmad-config.toml` — where BMad puts things (`_bmad/config.toml`).
- `skills-lock.json` — the skills installed, pinned by SHA-256.

## Deploy your own

BMad is an independent open-source project — <https://github.com/bmad-code-org/BMAD-METHOD>, MIT — and runs in your editor rather than on a platform. To reproduce this run you need Node.js, npm, Git and [uv](https://docs.astral.sh/uv/), because the workflows are Python.

```bash
npx skills add bmad-code-org/BMAD-METHOD \
  --skill bmad --skill bmod-core-tools --skill bmod-method \
  --skill bmad-build --skill bmad-agent-analyst \
  --skill bmad-agent-architect --skill bmad-brainstorming
```

Then ask the `bmad` skill for `bmad status`, install whatever it recommends, and run `bmad setup`.

**Two things to know.** `npx skills add` installs from the repository's `main` branch, so the skills here report `6.13.0-next` while npm's `bmad-method` sits at `6.12.0` — take a pinned release from npm or a plugin marketplace instead. And skills execute with your agent's full permissions, which the installer says itself: read what you install.

When the planning is done and the thing needs somewhere to run, a free account is at [https://www.back4app.com/signup?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts](https://www.back4app.com/signup?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts).

## Run locally

```bash
uv run .agents/skills/bmad-architecture/scripts/lint_spine.py \
  --workspace planning-artifacts/architecture/architecture-bmad-demo-2026-09-23
```

## What the platform gives you

The architecture spine in this repo pins a managed backend behind a single gateway layer. Back4app provides that: a managed Parse Server with a database, REST and GraphQL APIs, Cloud Code and a dashboard, plus Containers for anything with a Dockerfile. Documentation: [https://www.back4app.com/docs?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts](https://www.back4app.com/docs?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts) · [https://www.back4app.com/docs-containers?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts](https://www.back4app.com/docs-containers?utm_source=github&utm_medium=repo&utm_campaign=bmad-planning-artifacts).

## License

MIT.
