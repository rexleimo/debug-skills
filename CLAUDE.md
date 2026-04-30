# CLAUDE.md

Reusable AI agent skills published from a single repository.

## Repository Structure

- `skills/<name>/SKILL.md` — each skill's workflow and guardrails
- `skills/<name>/agents/` — optional runtime metadata (openai.yaml)
- `skills/<name>/references/` — optional reference docs
- `skills/<name>/scripts/` — optional runtime scripts
- `docs/` — install guide, images
- `tasks/` — AIOS task management (pending/completed)

## Current Skills

| Skill | Purpose |
|---|---|
| comment-strategist | Add high-value code comments |
| git-commit | Draft Conventional Commit messages |
| split-commits | Split mixed working tree into focused commits |
| debug | Evidence-first runtime debugging |
| grill-me | Pressure-test plans/designs |
| hack-review | Review for brittle hack-like shortcuts |
| receiving-hack-review | Consume hack-review reports |
| regression-review | Review for user-visible behavioral regressions |
| receiving-regression-review | Consume regression-review reports |

## Skill Format

Each skill follows this structure:
- Frontmatter: `name`, `description` (YAML between `---` fences)
- Sections: Workflow, Guardrails, optional Host adaptation
- References link to `./references/*.md`
- Scripts live in `./scripts/`

## Conventions

- Skills are independently installable and versioned
- Root-level files describe the collection; skill-specific detail stays in the skill folder
- Shared assets (screenshots) go in `docs/images/`
- `.debug-logs/` and `__pycache__/` are gitignored
- No runtime dependencies beyond Python 3 standard library for scripts

## Common Commands

```bash
# List skills
npx skills@latest add JUNERDD/skills --list

# Install a skill
npx skills@latest add JUNERDD/skills --skill <name>

# Smoke test the debug collector
mkdir -p .debug-logs
python3 skills/debug/scripts/local_log_collector/main.py \
  --log-file "$PWD/.debug-logs/demo.ndjson" \
  --ready-file "$PWD/.debug-logs/demo.json" \
  --session-id "demo-session"
```
