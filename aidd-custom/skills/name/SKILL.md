---
name: name
description: Naming guidance for functions and variables. Use when choosing names for code, especially facades, factories, and booleans.
---

## Competencies

Act as a top-tier software engineer who knows how to give clear, descriptive names to functions and variables.

When asked for names, apply the relevant constraint sets below, list possible names, then give one recommendation with reasoning.

## Constraints

Facade (only for facade functions in `-model` files):

- Function names follow `<action><Entity><OptionalWith...><DataSource><OptionalBy...>()`.
- Allowed actions: save | retrieve | update | delete.
- Entity names are singular, PascalCase.
- Use `With...` for included relations before `From` / `In` / `ToDatabase`.
- Use `By...` for lookup keys last; key names match schema fields exactly.
- Use `And` to chain multiple relations or keys.
- Use `ToDatabase` for create, `FromDatabase` for reads, `InDatabase` for updates, `FromDatabase` for deletes.

Factory (only for factory functions in `-factories` files):

- Names start with `createPopulated` for base or compound entities.
- Use explicit entity suffixes (e.g. Product, Price, Subscription, SubscriptionItem, SubscriptionSchedule, SubscriptionSchedulePhase) matching database models.
- Compound names list included relations in order, joined with `With...And...` (e.g. `createPopulatedStripeSubscriptionWithItemsAndPriceAndProduct`).

Boolean (only for functions that return boolean):

- Variables returned from the function: active voice for entity state (e.g. `isActive`, `hasExpired`, `isDeactivated`).
- Standalone or computed checks: prefix with `get` (e.g. `getIsActive(entity)`, `getHasExpired(date)`).

General:

- Active voice; clear, consistent naming.
- Functions are verbs (e.g. `increment()`, `filter()`).
- Booleans read like yes/no questions (e.g. `isActive`, `hasPermission`).
- Prefer standalone verbs over `noun.method` (e.g. `createUser()` not `User.create()`).
- Avoid noun-heavy redundant names (e.g. `filter(fn, array)` not `matchingItemsFromArray(fn, array)`).
- Avoid `doSomething` style; prefer `notify()` over `Notifier.doNotification()`.
- Lifecycle: prefer `beforeX` / `afterX` over `willX` / `didX` (e.g. `beforeUpdate()`).
- Prefer strong negatives (e.g. `isEmpty(thing)` over `!isDefined(thing)`).
- Mixins and decorators: `with${Thing}` (e.g. `withUser`, `withFeatures`, `withAuth`).
- Follow framework conventions (e.g. React components PascalCase, hooks prefixed with `use`).

## Commands

None. Follow user requests to name or rename symbols using the constraints above.
