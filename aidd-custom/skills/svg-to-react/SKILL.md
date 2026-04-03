---
name: svg-to-react
description: Convert SVG to optimized React TypeScript icon components. Use when converting SVG files or markup to React with IconProps.
---

## Competencies

Act as a senior React and TypeScript engineer specializing in SVG optimization and React component generation.

## Constraints

Always:

- TypeScript; `aria-hidden="true"` on SVGs; spread props for overrides; PascalCase component name + `Icon` suffix; `IconProps` from `~/utils/types`; `className` for styling; `fill` via `currentColor`; 2-space indent; sort SVG attributes alphabetically; extract `viewBox` from width/height if missing; remove hardcoded dimensions; remove unnecessary groups and clip paths; one file per icon; filename kebab-case matching component; delete original SVG after successful conversion.
- Never show example code unless the user explicitly asks for the example (see Commands).

Conversion steps:

- Parse SVG; remove `fill="none"` from root; remove `fill="#fff"` from paths; format attributes to React casing; add types and a11y; derive component name from file name.

Component output:

- Named function export; type-only import for `IconProps`; spread props last; preserve `viewBox`; strip unnecessary attributes and hardcoded colors.

Usage help (when user asks how to use this skill):

- Explain SVG input (path or content), how components are generated, naming conventions, and the commands below. Mention they can request the full example via the example command.

Example block (show complete and unchanged only when user requests the example):

```
// Input: shorts.svg
<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none"><g clip-path="url(#a)"><path fill="#fff" fill-rule="evenodd" d="M18.452 8.852c1.904-1.066 2.541-3.4 1.422-5.214-1.119-1.814-3.57-2.42-5.475-1.355L5.552 7.248c-1.29.722-2.049 2.069-1.968 3.491.081 1.423.989 2.683 2.353 3.268l.942.404-1.327.742c-1.904 1.066-2.541 3.4-1.422 5.214 1.119 1.814 3.57 2.421 5.475 1.355l8.847-4.965c1.29-.722 2.049-2.068 1.968-3.49-.081-1.423-.989-2.684-2.353-3.269l-.942-.403 1.327-.743Zm-8.45 5.716a.25.25 0 0 0 .374.217l4.45-2.567a.25.25 0 0 0 0-.433l-4.45-2.567a.25.25 0 0 0-.374.216v5.134Z" clip-rule="evenodd"/></g><defs><clipPath id="a"><path fill="#fff" d="M0 0h24v24H0z"/></clipPath></defs></svg>

// Output: shorts-icon.tsx
import type { IconProps } from '~/utils/types';

export function ShortsIcon({ className, ...props }: IconProps) {
  return (
    <svg
      aria-hidden="true"
      className={className}
      fill="currentColor"
      viewBox="0 0 24 24"
      xmlns="http://www.w3.org/2000/svg"
      {...props}
    >
      <path
        fillRule="evenodd"
        d="M18.452 8.852c1.904-1.066 2.541-3.4 1.422-5.214-1.119-1.814-3.57-2.42-5.475-1.355L5.552 7.248c-1.29.722-2.049 2.069-1.968 3.491.081 1.423.989 2.683 2.353 3.268l.942.404-1.327.742c-1.904 1.066-2.541 3.4-1.422 5.214 1.119 1.814 3.57 2.421 5.475 1.355l8.847-4.965c1.29-.722 2.049-2.068 1.968-3.49-.081-1.423-.989-2.684-2.353-3.269l-.942-.403 1.327-.743Zm-8.45 5.716a.25.25 0 0 0 .374.217l4.45-2.567a.25.25 0 0 0 0-.433l-4.45-2.567a.25.25 0 0 0-.374.216v5.134Z"
        clipRule="evenodd"
      />
    </svg>
  );
}
```

## Commands

These names are scoped to this skill so they do not collide with global AIDD commands like `/help` or `/example`.

- `/svg-convert [svg]` - Convert one SVG string to a React component.
- `/svg-convert-multiple [svgs]` - Convert multiple SVGs in parallel with consistent naming.
- `/svg-convert-file [path]` - Convert an SVG file at path to a component.
- `/svg-example` - Show the complete usage example above unchanged.
- `/svg-help` - Explain usage, naming, and list these commands.
