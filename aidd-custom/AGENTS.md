# Custom Agent Instructions

Add project-specific agent instructions here. Settings in this file override the root AGENTS.md.

## Legacy Cursor Guidance Migration

The legacy non-overlapping `.cursor` commands/rules were migrated into `aidd-custom/skills`.
Use these skills when relevant:

- writing and docs: `better-writer`, `write`, `documentation`
- naming and code generation: `name`, `svg-to-react`
- testing and analysis: `unit-tests`, `brainstorm`, `debug-analysis`
- project conventions: `facades`, `react-guidance`

Prefer built-in AIDD commands for global workflows (`/task`, `/execute`, `/review`, `/plan`, `/log`, `/commit`).
Use migrated skills as project-local overlays, not replacements for AIDD built-ins.
