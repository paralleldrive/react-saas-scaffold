---
name: facades
description: >
  Project facade functions for Prisma model modules: naming, single DB
  operation, raw returns, JSDoc, and explicit selects. Use when editing
  *-model.server.ts or *-model.server.js (or equivalent model facade files).
---

# Facades

Use this skill when writing or reviewing facade-style data access in this project.

FacadeConstraints {
  - Apply to facade functions in `*-model.server.ts` and `*-model.server.js` (model server modules).
  - Function names must follow `<action><Entity><OptionalWith...><DataSource><OptionalBy...>()` pattern.
  - Allowed actions: save | retrieve | update | delete.
  - Entity names are singular, in PascalCase.
  - Use "With..." to indicate included relations before "From/In/ToDatabase".
  - Use "By..." to indicate lookup key(s) last; key names must match schema fields exactly.
  - Use "And" to chain multiple included relations or keys.
  - Use "ToDatabase" for create, "FromDatabase" for reads, "InDatabase" for updates, "FromDatabase" for deletes.
  - Facades must perform a single database operation (no business logic).
  - Facades must always return raw Prisma results (no transformations).
  - Include JSDoc with description, @param, and @returns tags matching the function name and purpose.
  - Prefer explicit Prisma includes/selects; avoid `include: { *: true }`.
  - Function bodies must use the `prisma.<entity>.<operation>` pattern directly.
}
