# Bootstrap Guidelines

## Project Conventions

### Skill Structure
- Each skill lives in `skills/<name>/`
- Required: `SKILL.md` with YAML frontmatter (`name`, `description`)
- Optional: `agents/`, `references/`, `scripts/`, `assets/`
- Skills are independently installable via `npx skills@latest add`

### SKILL.md Format
- Frontmatter between `---` fences with `name` and `description`
- Description should be comprehensive (used for skill discovery)
- Sections: Host adaptation (optional), Workflow, Guardrails
- Reference docs linked as `[text](./references/file.md)`

### Git Conventions
- Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`
- Merge commits from PRs (squash or merge commit style)
- `.debug-logs/` and `__pycache__/` are gitignored

### Quality Bar
- Skills must be self-contained and portable
- No external runtime dependencies beyond Python 3 stdlib for scripts
- Guardrails must be explicit prohibitions, not suggestions
- Workflow steps must be numbered and actionable

## Next Engineering Task

**Task**: Add SKILL.md schema validation script

**Acceptance Criteria**:
1. A script exists at `scripts/validate-skills.py` that checks:
   - Every `skills/*/SKILL.md` has valid YAML frontmatter
   - Frontmatter contains required `name` and `description` fields
   - `name` matches the directory name
   - `description` is non-empty and under 500 chars
   - SKILL.md has at least one `## ` section heading
2. Script exits 0 on success, 1 on failure with clear error messages
3. Script can be run as `python3 scripts/validate-skills.py`
4. All current skills pass validation

**Why**: The `npx skills` installer depends on consistent frontmatter. A validation script prevents broken skills from being published and gives CI a concrete gate.

## Checkpoint

- Created `CLAUDE.md` with project conventions
- Documented skill format and quality bar
- Defined next task: schema validation script
