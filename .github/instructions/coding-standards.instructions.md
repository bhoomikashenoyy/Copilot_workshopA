---
description: 'Shared TypeScript, documentation, and commenting standards'
applyTo: '**/*.{ts,astro}'
---

# Coding Standards

These rules apply to TypeScript and Astro code throughout the repository. Keep
documentation close to the code it describes and update it whenever the
implementation changes.

## Comments and documentation

- Comment **why**: explain intent, constraints, trade-offs, or a non-obvious
  decision.
- Do not comment **what**: avoid comments that merely paraphrase the next line
  or describe standard syntax.
- Prefer clear names and small functions over explanatory comments for obvious
  mechanics.
- Treat stale comments as bugs. Update or remove a comment in the same change
  that invalidates it.
- Use TSDoc/JSDoc (`/** ... */`) for public APIs, not ordinary line comments.

## Data-layer API documentation

Every exported function in `db/` and `src/lib/` must have a TSDoc/JSDoc
comment that:

- briefly states the function's purpose;
- documents every parameter with `@param`, including the injectable `db`
  argument used by data-access helpers; and
- documents the result with `@returns`, including notable `null` or empty
  collection behavior.

Keep the documented contract aligned with the explicit TypeScript return type.
Pure transforms, database helpers, seed/export functions, and database
factories are all public APIs and follow this rule.

## Astro component contracts

Every reusable component in `src/components/` and `src/layouts/` must define
its props in a frontmatter `interface Props` (or an equivalent named type).
Document non-obvious props with a short TSDoc/JSDoc comment, and keep the
interface accurate when the component API changes. Pages may use a local
`Props` interface when they accept props from a route or layout.

## TypeScript formatting and type safety

- Use two spaces for indentation, single quotes, semicolons, and trailing
  commas in multiline literals and parameter lists, matching the existing
  ESLint configuration.
- Add explicit parameter and return types to exported functions and to
  non-trivial local helpers. Avoid `any`, unnecessary type assertions, and
  broad error catches.
- ESLint enforces explicit return types for TypeScript functions. Run
  `npm run lint` (through the `quality-checks` skill) before submitting changes.
