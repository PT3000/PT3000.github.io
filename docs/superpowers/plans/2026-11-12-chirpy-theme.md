# Chirpy Theme Implementation Plan

> **For agentic workers:** Use subagent-driven-development to implement the integration, then review and publish.

**Goal:** Apply Chirpy to the existing blog at https://pt3000.github.io.

**Architecture:** Import the official starter at beffc88713242da8bf49325674be38d171071213, use its theme gem, and deploy with GitHub Actions. Preserve existing Git history.

**Tech Stack:** Jekyll, jekyll-theme-chirpy ~> 7.6, Ruby 3.4 on Linux, GitHub Actions, HTMLProofer.

## Global Constraints

- Preserve https://pt3000.github.io with url https://pt3000.github.io and baseurl "".
- Use lang ko-KR, timezone Asia/Seoul, and PT3000 as title, author, and GitHub username.
- Preserve Chirpy's standard responsive design and automatic light/dark mode.
- Remove placeholder Twitter/email identities; show GitHub and RSS contacts.
- Do not invent personal information or publish sample blog posts.
- Preserve upstream MIT license attribution.
- Build and run HTMLProofer before publication; deploy only main.
- Write text as UTF-8 and preserve Korean correctly.

## Task 1: Integrate the official starter

**Files:** Import .editorconfig, .gitattributes, .gitignore, .nojekyll, Gemfile, LICENSE, _config.yml, index.html, _data/, _plugins/, _posts/.placeholder, _tabs/, tools/, .github/workflows/pages-deploy.yml. Update README.md. Do not import .git, .gitmodules, optional assets/lib, editor settings, or devcontainer files.

**Interfaces:** Reads the official starter clone at C:/Users/okay3/AppData/Local/Temp/pt3000-chirpy-starter-20261112. Produces a standard Jekyll source tree and a pull-request/main workflow.

- [ ] Copy the listed official source files byte-for-byte, then apply focused UTF-8 patches.
- [ ] Set config lang ko-KR, timezone Asia/Seoul, title PT3000, tagline 기록하고 공유하는 공간, description PT3000의 기록을 담는 블로그입니다., url https://pt3000.github.io, github.username PT3000, social.name PT3000, social.links [https://github.com/PT3000], avatar https://github.com/PT3000.png. Clear social.email and twitter.username; retain baseurl "".
- [ ] Keep only GitHub and RSS in _data/contact.yml; replace About placeholder with PT3000의 블로그입니다.
- [ ] Extend the upstream workflow with pull_request targeting main. Guard the deploy job with github.ref == 'refs/heads/main' && github.event_name != 'pull_request'. Retain upstream Ruby, build, HTMLProofer, artifact and deploy steps. Add docs/** to ignored changes, and retain main as the push branch.
- [ ] Write a Korean README describing the live URL, Chirpy source, _config.yml, _tabs/about.md, and _posts/YYYY-MM-DD-title.md front matter and local bundle install / bundle exec jekyll serve. Include one fenced example, not a published post.
- [ ] Validate UTF-8 with the preserve-html-encoding script and git diff --check. No new unit tests are needed for imported upstream code and configuration; the upstream Jekyll build and HTMLProofer provide integration checks.
- [ ] Commit the integration and write a concise implementation report to .git/chirpy-task-report.md. Do not push or change Pages settings; the parent handles remote build and deployment.

## Task 2: Review, verify and publish (parent)

- [ ] Review the integration and source diff. Push the feature branch and create a PR to trigger the build and HTMLProofer. Fix any observed failure before publishing.
- [ ] After a passing build, set GitHub Pages build_type to workflow, merge into main, and push.
- [ ] Wait for successful production deployment. Check HTTP 200, ko-KR, PT3000 title, Chirpy markup, each tab, CSS and JavaScript. Inspect desktop and mobile layout in the browser if available.
- [ ] Return the live URL and the path for adding posts.
