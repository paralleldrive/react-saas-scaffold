# Legacy `.cursor` Migration Sub-Agent Prompts

These prompts are written in the same practical pattern used by `ai/skills/aidd-churn/SKILL.md`:

- clear role and objective
- `Competencies { ... }`
- `Constraints { ... }`
- explicit implementation steps
- deterministic validation and git requirements

They also follow AgentSkills-style conventions (frontmatter + structured instructions).

---

## Prompt A — Writing and Documentation Skills Migration

```md
---
name: migrate-legacy-writing-skills
description: Migrate non-overlapping legacy writing/documentation cursor commands into aidd-custom skills for this project.
compatibility: Requires git repository access and ability to edit files in working tree branch cursor/aidd-scaffold-integration-f128.
---

# Migrate Legacy Writing Skills

Act as a top-tier migration engineer. Port the specified legacy `.cursor` command files from `origin/main` into `aidd-custom/skills/*/SKILL.md` while preserving intent and avoiding conflicts with built-in AIDD commands.

Competencies {
  command-to-skill migration
  prompt refactoring and normalization
  AIDD customization patterns
  git hygiene and focused commits
}

Constraints {
  Branch must remain `cursor/aidd-scaffold-integration-f128`
  Only migrate these legacy files:
    - .cursor/commands/better-writer.md
    - .cursor/commands/write.md
    - .cursor/commands/documentation.md
  Source content must be read from `origin/main` via `git show origin/main:<path>`
  Preserve behavior and intent; fix obvious truncation/format issues only when safe
  Do not modify built-in `ai/` skills/commands
  Create one skill per legacy command under `aidd-custom/skills/<skill-name>/SKILL.md`
  Add concise README.md per skill folder explaining when to use it
  Run index generation for aidd-custom if needed so `aidd-custom/index.md` includes new entries
  Commit only your changes with a descriptive commit message
  Do not push
  show your work: 🎯 restate |> 💡 ideate |> 🪞 reflectCritically |> 🔭 expandOrthogonally |> ⚖️ scoreRankEvaluate |> 💬 respond
}

## Steps

1. Confirm current branch and clean working state.
2. Read each legacy source file from `origin/main`.
3. Create migrated skills in:
   - `aidd-custom/skills/legacy-better-writer/`
   - `aidd-custom/skills/legacy-write/`
   - `aidd-custom/skills/legacy-documentation/`
4. Ensure each `SKILL.md` has valid frontmatter (`name`, `description`) and structured guidance.
5. Update `aidd-custom/AGENTS.md` only if needed to note usage preference for these new skills.
6. Regenerate indexes if required.
7. Commit with message:
   - `chore: migrate legacy writing cursor commands to aidd-custom skills`

## Return

Return:
- files changed
- commit hash
- brief notes on any ambiguity handled
```

---

## Prompt B — Engineering Utility Skills Migration

```md
---
name: migrate-legacy-engineering-skills
description: Migrate non-overlapping legacy engineering cursor commands into aidd-custom skills.
compatibility: Requires git repository access and ability to edit files in working tree branch cursor/aidd-scaffold-integration-f128.
---

# Migrate Legacy Engineering Utility Skills

Act as a top-tier migration engineer. Port selected non-overlapping utility commands from legacy `.cursor` into project-local `aidd-custom/skills`.

Competencies {
  command taxonomy and de-duplication
  prompt-to-skill conversion
  codebase-safe incremental edits
  commit discipline
}

Constraints {
  Branch must remain `cursor/aidd-scaffold-integration-f128`
  Only migrate these legacy files:
    - .cursor/commands/brainstorm.md
    - .cursor/commands/debug.md
    - .cursor/commands/name.md
    - .cursor/commands/svg-to-react.md
    - .cursor/commands/unit-tests.md
  Source content must be read from `origin/main`
  Do NOT migrate/restore conflicting built-ins:
    - .cursor/commands/commit.md
    - .cursor/commands/log.md
    - .cursor/commands/plan.md
  Preserve legacy behavior while adapting format to skill-style docs
  Place each migrated artifact in `aidd-custom/skills/<skill-name>/SKILL.md` + `README.md`
  Do not modify built-in `ai/` files
  Commit only your changes with a descriptive message
  Do not push
  show your work: 🎯 restate |> 💡 ideate |> 🪞 reflectCritically |> 🔭 expandOrthogonally |> ⚖️ scoreRankEvaluate |> 💬 respond
}

## Steps

1. Verify branch and read source files from `origin/main`.
2. Migrate into:
   - `aidd-custom/skills/legacy-brainstorm/`
   - `aidd-custom/skills/legacy-debug/`
   - `aidd-custom/skills/legacy-name/`
   - `aidd-custom/skills/legacy-svg-to-react/`
   - `aidd-custom/skills/legacy-unit-tests/`
3. Keep slash-command hints as guidance text rather than hard requirements.
4. Regenerate indexes if required.
5. Commit with message:
   - `chore: migrate legacy engineering cursor commands to aidd-custom skills`

## Return

Return:
- files changed
- commit hash
- any overlap risks noticed with built-in AIDD skills
```

---

## Prompt C — Rule Migration (Project-Specific Rules)

```md
---
name: migrate-legacy-project-rules
description: Migrate legacy project-specific .mdc rules to aidd-custom while avoiding built-in conflicts.
compatibility: Requires git repository access and ability to edit files in working tree branch cursor/aidd-scaffold-integration-f128.
---

# Migrate Legacy Project Rules

Act as a top-tier migration engineer. Move non-overlapping legacy `.cursor/rules` guidance into `aidd-custom` so project-specific behavior remains available after AIDD upgrade.

Competencies {
  rule conflict analysis
  project convention preservation
  minimal-risk documentation migration
  git workflow execution
}

Constraints {
  Branch must remain `cursor/aidd-scaffold-integration-f128`
  Analyze legacy rules from `origin/main`:
    - .cursor/rules/facades.mdc
    - .cursor/rules/jsx-and-tsx.mdc
    - .cursor/rules/js-and-ts.mdc
  Migrate non-overlapping rules:
    - include facades and jsx-and-tsx
  Do NOT duplicate built-in equivalent if already covered:
    - js-and-ts is already represented by built-in `ai/skills/aidd-javascript/SKILL.md`
  Place migrated rule files under `aidd-custom/` as `.mdc` files with clear names
  Update `aidd-custom/AGENTS.md` with concise routing notes for when to apply the migrated rules
  Regenerate index files if needed
  Commit only your changes with message:
    - `chore: migrate legacy project rules into aidd-custom`
  Do not push
  show your work: 🎯 restate |> 💡 ideate |> 🪞 reflectCritically |> 🔭 expandOrthogonally |> ⚖️ scoreRankEvaluate |> 💬 respond
}

## Return

Return:
- files changed
- commit hash
- summary of why js-and-ts was not duplicated
```
