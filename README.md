# bmad-planning-artifacts

**What the BMAD Method actually writes to disk — a product brief, an architecture spine and their decision logs, produced by the workflows rather than by hand.**

BMAD installs as agent skills and its output is plain Markdown in your repository. This repo is that output, kept verbatim from a real run so you can see the shape before you install anything.

Produced on September 23, 2026 with BMAD **6.13.0-next**, installed by [skills CLI](https://www.npmjs.com/package/skills) 1.7.0 into a scratch project, hosted by Claude Code on Node 22 and `uv` 0.11.6.

> **Read the article:** [How to Install and Run the BMAD Method in an AI Editor](https://www.back4app.com/blog/install-and-run-the-bmad-method-in-an-ai-editor)

## What is in here

```
planning-artifacts/
  briefs/brief-bmad-demo-2026-09-23/
    brief.md          the product brief the workflow wrote
    .memlog.md        the decision log beside it
  architecture/architecture-bmad-demo-2026-09-23/
    ARCHITECTURE-SPINE.md   invariants only — the calls a future builder can't
                            read off compliant code
    .memlog.md
bmad-config.toml      where BMad puts things (_bmad/config.toml)
skills-lock.json      the skills installed, pinned by SHA-256
```

The memlogs are the part worth looking at twice. The brief says *what* the product is; the memlog records *which alternatives were closed, and when* — the context that normally evaporates when a chat window closes.

## Reproduce it

```bash
# Node.js, npm, Git and uv are required — the workflows are Python.
npx skills add bmad-code-org/BMAD-METHOD \
  --skill bmad --skill bmod-core-tools --skill bmod-method \
  --skill bmad-build --skill bmad-agent-analyst \
  --skill bmad-agent-architect --skill bmad-brainstorming
```

Then ask the `bmad` skill for `bmad status`, install whatever it recommends, and run `bmad setup`. Thirteen skills installed in under seven seconds total; setup created `_bmad/` with 19 files.

## The spine passes its own linter

The architecture skill ships `scripts/lint_spine.py`, which checks that every decision carries its required fields and that decision ids ascend and are never reused.

```bash
uv run .agents/skills/bmad-architecture/scripts/lint_spine.py \
  --workspace planning-artifacts/architecture/architecture-bmad-demo-2026-09-23
```

`{"ok": true, "total_findings": 0}` on the spine in this repo. A clean pass from a linter that never fires would prove nothing, so the same file was corrupted deliberately — a duplicated decision id and a removed rule — and returned three high-severity findings, each naming the line.

## Two things to know

`npx skills add` installs from the repository's **`main` branch**, so the skills here report `6.13.0-next` while npm's `bmad-method` sits at `6.12.0`. If you need a pinned release, take it from npm or a plugin marketplace instead.

Skills execute with your agent's full permissions — the installer says so itself. BMAD's own setup script is legible and uses no shell execution, but read what you install; `skills-lock.json` pins each skill by SHA-256 so you can tell when one changes.

## Upstream

BMAD Method is an independent open-source project: <https://github.com/bmad-code-org/BMAD-METHOD> (MIT). This repo only holds the artifacts one run produced.

## License

MIT.
