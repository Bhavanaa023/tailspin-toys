---
description: 'Comment, documentation, and TypeScript conventions'
applyTo: '**/*.{ts,astro}'
---

# Code Style and Documentation

## Comments

- Comment intent, constraints, and non-obvious decisions: explain **why** the code exists or why an approach was chosen.
- Do not restate readable code or describe routine control flow. If the code changes, update or remove comments that are no longer true.
- Keep comments close to the decision they explain. Prefer a concise comment over a large explanatory block.
- Use TSDoc (`/** ... */`) for public TypeScript APIs. Inline comments are appropriate only for local, non-obvious logic.

## Data-layer API documentation

- Every exported function in `db/` and `src/lib/` must have a TSDoc/JSDoc comment.
- Document the function's purpose, every parameter (including the injectable `db` argument), and its return value. Describe meaningful `null` or error behavior.
- Keep explicit parameter and return types on exported functions. ESLint enforces explicit module-boundary types for these directories.
- Pure transforms in `db/` should document their input and output without implying database access. Data-access helpers should identify ordering, lookup, or relation behavior that callers rely on.

## Astro component contracts

- Every reusable `.astro` component must define a `Props` interface (or type) in its frontmatter.
- Document non-obvious props and component-wide invariants with TSDoc. Use descriptive property names and types so the component contract is understandable without reading its markup.
- Pages and layouts are components too: document their props when they accept them, while page-only frontmatter values do not need a public API comment.

## TypeScript formatting

- Use four-space indentation, single quotes, semicolons, trailing commas in multiline lists, and one statement per line.
- Prefer `import type` for type-only imports and keep imports grouped at the top of the file.
- Keep explicit types on exported functions and on data-layer helpers, fixtures, and callback parameters where inference would obscure the contract.
- Prefer narrow types and null checks over casts. Do not use `any` to bypass a type error.
