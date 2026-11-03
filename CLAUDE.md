## Writing style

- No Oxford (serial) commas in site copy or blog posts, e.g. "products, data and golf" not "products, data, and golf".

## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)

## Roles and workflow

This project uses three agent roles, defined in `.claude/agents/`. Start a session as one with `claude --agent <name>` or @-mention it from any session.

- **coder**: Astro code, config, styling and CI. Does not edit blog prose.
- **editor**: grammar fixes and style-matched rewrites in `src/content/blog/`. Follows `STYLE.md`.
- **ideation**: brainstorming. Writes only to `BACKLOG.md`.

`BACKLOG.md` is the hand-off point between roles. Every role reads it at the start of a session, picks up `ready` items for its own role and updates the status when it starts and finishes. Keep `BACKLOG.md` and `STYLE.md` outside `src/content` so Astro never publishes them.

Pushing to `master` deploys straight to GitHub Pages, so don't push unless explicitly asked.

### Worktrees

The coder and editor work in separate git worktrees so their changes never collide with each other or with Felix's own edits in the main checkout. Ideation stays in the main checkout, since it only touches `BACKLOG.md`.

- Start sessions with `claude --agent coder --worktree coder` and `claude --agent editor --worktree editor`. When @-mentioned as subagents, both create a temporary worktree automatically.
- Worktrees live in `.claude/worktrees/<name>/` on a branch named `worktree-<name>`. They branch from local `HEAD` (set in `.claude/settings.json`), so commit work in the main checkout before starting a session that needs it. Uncommitted changes aren't visible in a worktree.
- `BACKLOG.md` and `STYLE.md` are shared state. Always read and update the copies in the main checkout (`/Users/felixvandoorn/workspace/felixvandoorn.github.io/`), never the copies inside a worktree.
- When the work is done, commit it on the worktree branch. Felix reviews it and merges it into `master` from the main checkout. Pushing `master` then deploys it.
