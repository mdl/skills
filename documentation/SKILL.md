---
name: documentation
description: Create, update, and find project documentation. Use when writing code that needs docs, bootstrapping docs for a new project, searching for existing docs, or deciding where/how to document something.
---

# Documentation Skill

Hierarchical markdown docs so any agent can build context fast.

## Structure

```
project-root/
├── docs/
│   ├── README.md               ← Project overview + doc index
│   └── <topic>/README.md       ← Area-specific index
├── src/<module>/
│   ├── README.md               ← Module overview
│   └── docs/<topic>.md         ← Deep-dive doc
```

- **Module overviews** → `<module>/README.md`
- **Deep dives** → `<module>/docs/<topic>.md` (kebab-case)
- **Cross-cutting topics** → `docs/<topic>/`
- Every doc links back to its parent README.

## Rules

1. **Update docs for significant changes.** New modules, API changes, architectural shifts, non-obvious fixes. Skip for trivial refactors and self-explanatory changes.
2. **Fix stale docs on sight.**
3. **Inline comments for brief "why"; MD files for anything structured.**

## Finding docs

1. Start at `docs/README.md` — follow links.
2. Check `<module>/README.md` for module context.
3. Grep/Glob for specific content.

## Writing docs

Use `assets/doc-template.md` for content docs, `assets/index-template.md` for READMEs. Link every new doc from its parent README.

### Frontmatter (required)

```yaml
---
title: <Title>
scope: <relative/path/to/code>
type: overview | flow | api | convention | guide
last_updated: <YYYY-MM-DD>
related:                          # Optional
  - <path/to/related/doc.md>
---
```

### Writing rules

- Lead with 2-3 sentence summary
- Concrete file paths, not vague references
- Under 200 lines — split if longer

## Bootstrap (no docs exist yet)

1. Create `docs/README.md` — project name, tech stack, folder table
2. Create `<module>/README.md` for each major module
3. Breadth first — detailed docs come with future tasks
