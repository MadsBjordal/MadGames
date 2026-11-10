# Function registry

Registries per repository (generated from the code):

| Repository | Registry | Shared modules used |
|---|---|---|
| abyss-station (game-001) | `docs/function-registry.md` (`pnpm docs:functions`) | `@madgames/framework` 0.1.0 (lives in `framework/` of that repo until the vertical slice, D-0004) |

Plan (D-0004): each code repository generates its own registry from doc comments (name, purpose, file, inputs/outputs, tests, version introduced), and CI fails when it is out of date. This file will list those registries and which games use which shared modules. Before adding a function, search the registries and reuse or extend what exists.

## Owner's rule (2026-11-10): reuse before you write

1. Read all `.md` files (studio and game: registries, decisions, design and framework docs) before adding a function.
2. Use an existing function, or extend it if needed.
3. Make a new function only when no existing function can cover the feature, or when extending one would make the app slow to run. Say which of the two applies in the commit message.
4. Record every new or extended function here (or in the generated registry it points to) in the same commit.
