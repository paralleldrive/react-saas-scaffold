---
name: react-guidance
description: >
  React, React Router v7, ShadCN/ui, Tailwind v4, forms (react-hook-form +
  Zod), a11y, and i18n conventions for this codebase. Use when writing or
  reviewing .js, .jsx, or .tsx UI.
---

# React guidance

Act as a senior engineer with strong React ecosystem experience for this fullstack app.

## Before writing code

- Read relevant existing code in the repo first.
- Match existing style, patterns, and conventions unless the user explicitly overrides them.

## Principles

- Display/container pattern: pure display components (props to JSX); optional stateful containers wrapping one display component; compose in parent or route.

Constraints {
  Be concise.
  This stack uses React Router v7 (successor to Remix).
  Use ShadCN/ui; install a component if it is missing.
  Modularize by feature; one concern per file or component; prefer named exports.
  TailwindCSS v4: container queries and child selectors are available.
}

NamingConstraints {
  Use clear, descriptive, consistent naming.
  Postfix components with `Component`.
  Props types: component name + `ComponentProps` (e.g. `UserMenuComponentProps`).
}

TypeConstraints {
  Use proper React TypeScript types: MouseEventHandler<HTMLButtonElement>, ChangeEventHandler<HTMLInputElement>, ReactNode, React.Ref<T>, ComponentProps<'element'>, etc. Avoid generic () => void or (event: any) => void.
  When extending HTML elements or components, use ComponentProps: ComponentProps<'input'>, ComponentProps<'button'>, ComponentProps<typeof ExistingComponent>.
  Prisma-backed props: use entity types, e.g. Pick<UserAccount, 'id' | 'name' | 'email'> combined with handlers and related fields.
  Server return types: Awaited<ReturnType<typeof serverFunction>>; wrap with NonNullable<> when the value is guaranteed.
}

FormConstraints {
  react-hook-form + Zod:
    - Export schema types: export type Schema = z.infer<typeof schema>
    - Export error types: export type SchemaErrors = FieldErrors<Schema>
    - Optional intent: intent: z.literal('actionName')
    - Validation messages: translation keys, not literal translated strings
  Loading/submission:
    - Naming: isSubmitting = false, isLoading{Action} = false, is{Action}ing{Entity} = false
    - Default values in function signatures
    - Disable forms with <fieldset disabled={isSubmitting || isLoading}> rather than many per-field disabled props
  Form components:
    - errors?: SchemaErrors (optional)
    - children?: ReactNode for composition
    - FormProvider at parent; useFormContext in nested fields
    - Complete defaultValues in useForm for every field
}

AccessibilityConstraints {
  Interactive components: default aria-related props where useful:
    - *AriaLabel for screen readers (e.g. countryAriaLabel = 'Select country')
    - *Placeholder for empty states
    - FormControl handles aria-describedby and aria-invalid where applicable
}

InternationalizationConstraints {
  useTranslation with namespace and keyPrefix: const { t } = useTranslation('namespace', { keyPrefix: 'section' });
  Trans for interpolation with links or components.
  FormMessage translates error keys as configured in the project.
}
