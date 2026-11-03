# Backlog

This is the shared list for the coder, editor and ideation roles. Each role picks up `ready` items in its own section.

**Statuses:** `idea` (not defined enough to act on) → `ready` → `in progress` → `done`

**Entry format:**
```
### <ID>: <short title>
- **Status:** ready
- **Files:** <post or files involved>
- **What:** <what needs doing and why>
- **Done when:** <concrete, checkable outcome>
- **Notes:** <optional; links, dependencies, outcome when done>
```
IDs use a role prefix and a number: `P` for post ideas, `C` for coder tasks and `E` for editor tasks. Move `done` items to the Done section at the bottom.

---

## Post ideas

### P1: Bear Trap analysis
- **Status:** in progress
- **Files:** `src/content/blog/bear-trap-analysis.md`
- **What:** Follow-up to `bear-trap` covering what the honeypot data shows: traffic volume, source patterns, AWS vs Azure and any signs of AI agents.
- **Done when:** All TODO sections are written by Felix and the post has been through an editor pass.

### P2: Porting Bear Trap to infrastructure as code
- **Status:** idea
- **Files:** none yet
- **What:** A `tech` post building on the "What I want to learn" section of `bear-trap`: rebuilding the honeypot setup with Terraform or OpenTofu so new nodes are easy to add.
- **Done when:** Angle and outline are agreed in an ideation session.

## Coder tasks

### C1: Add a draft flag for blog posts
- **Status:** ready
- **Files:** `src/content.config.ts`, `src/pages/blog/index.astro`, `src/pages/blog/[...slug].astro`, `src/pages/rss.xml.js`, `src/content/blog/bear-trap-analysis.md`
- **What:** Nothing currently stops an unfinished post from going live when `master` is pushed, and `bear-trap-analysis.md` is full of TODOs. Add an optional `draft` field to the blog schema and hide draft posts from production builds.
- **Done when:** `draft: z.boolean().default(false)` is in the schema. Draft posts are left out of the blog index, the post pages and the RSS feed in `npm run build` but still show in `astro dev`. `bear-trap-analysis.md` has `draft: true`. The build passes.

### C2: Content checks in CI
- **Status:** ready
- **Files:** `scripts/check-content.mjs` (new), `package.json`, `.github/workflows/deploy.yml`
- **What:** Automatic checks before every deploy. Unfinished posts with TODOs or empty sections are fine to push, so don't check for those.
- **Done when:** `npm run check:content` exists and warns (but doesn't fail) on likely Oxford commas, such as `, and ` after a list. The deploy workflow runs `npx astro check` and `npm run check:content` before building. A type error from `astro check` blocks the deploy; style warnings don't.

## Editor tasks

### E1: Corrections pass on Bear Trap
- **Status:** ready
- **Files:** `src/content/blog/bear-trap.md`
- **What:** Apply pass 1 corrections. Known issues include "intial", "predfined", "Github", missing commas, trailing whitespace and extra blank lines. Note the empty "How it works" content after the first paragraph, but don't fill it in.
- **Done when:** Corrections are applied and any rewrite suggestions are listed for Felix to review.
- **Notes:** Felix has uncommitted edits in this file. The editor's worktree only sees committed work, so Felix needs to commit his edits before this can start.

---

## Done

_Nothing yet._
