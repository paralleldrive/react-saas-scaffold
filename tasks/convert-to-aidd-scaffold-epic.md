# Convert to AIDD Scaffold Epic

**Status**: ✅ COMPLETED (2026-04-02)
**Goal**: Convert this repository to an AIDD-compatible scaffold.

## Overview

WHY this repository should be reusable as a scaffold for new projects, we need a valid AIDD scaffold manifest and clear usage guidance so consumers can verify and create projects from the repo reliably.

---

## Inventory Existing Cursor Skills

Confirm whether project-local custom `.cursor/skills` exist and preserve only meaningful customizations in `aidd-custom`.

**Requirements**:
- Given the repository root, should detect whether `.cursor/skills` exists
- Given no project-local custom skills are present, should avoid creating redundant migrated skill files
- Given AIDD initialization output, should ensure `aidd-custom` remains available for future project-specific customization

---

## Install and Initialize AIDD Framework

Install AIDD with Cursor integration and add the npm dependency.

**Requirements**:
- Given an existing `.cursor` directory, should initialize AIDD with overwrite enabled
- Given the project dependencies, should install `aidd@latest` in `package.json`
- Given initialized AIDD assets, should expose `/task` and `/execute` command definitions in `ai/commands`

---

## Add Scaffold Authoring Artifacts

Create and validate root scaffold files according to AIDD scaffold-authoring rules.

**Requirements**:
- Given the project root, should include a valid `SCAFFOLD-MANIFEST.yml` with deterministic `run:` steps
- Given repository onboarding docs, should document how to verify and consume this repo as an AIDD scaffold
- Given the authored manifest, should pass `npx aidd verify-scaffold file:///workspace`

---
