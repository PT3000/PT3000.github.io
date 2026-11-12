# Algorithm Notes Migration Plan

**Goal:** Add an algorithm section to the existing Chirpy blog and migrate the user's algorithm notes from the supplied Notion page.

**Architecture:** Add a standard Chirpy tab at `/algorithms/` listing posts in the `알고리즘` category. Convert each accessible Notion note into a Markdown post, preserving headings, code languages, equations, images, links, and the user's explanations. Keep source links and use actual original dates where available; otherwise clearly record the migration date rather than inventing a source date.

**Constraints:** Preserve the current domain and theme. Use UTF-8 and Korean navigation. Publish only notes obtained from the specified page and its relevant child pages. Do not fabricate notes when source access is unavailable. Do not change Notion sharing settings. Store any source snapshots outside the published source tree.

## Tasks

- [ ] Read the Notion page and enumerate its algorithm notes using an authorized connector or accessible page. If access is missing, request the Notion connection and continue the independent blog work.
- [ ] Add `_tabs/algorithms.md` with title 알고리즘, a code icon, order 0, permalink `/algorithms/`, and a dynamic list of posts categorized 알고리즘. Show an accurate empty state until notes exist.
- [ ] Document the algorithm category convention in README.md.
- [ ] Migrate all obtained notes into `_posts/`, download required accessible images into `assets/img/algorithms/`, rewrite internal cross-links, preserve code and math, and enable math/Mermaid only when source content uses them.
- [ ] Validate UTF-8, Git whitespace, Jekyll production build, and internal links. Review the source changes before merge. Publish and verify the section and migrated posts at the live URL.
- [ ] Report actual migrated note count and any remaining source-access limitation.

**Validation:** Use the existing GitHub Actions Jekyll/HTMLProofer workflow and live HTTP/markup checks. This is a bounded Liquid/Markdown content change; no duplicate unit-test suite is needed.
