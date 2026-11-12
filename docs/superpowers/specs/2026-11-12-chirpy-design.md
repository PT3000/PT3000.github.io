# Chirpy theme integration

The user selected cotes2020/jekyll-theme-chirpy and requested installation on their existing public GitHub Pages blog. Preserve the repository history and https://pt3000.github.io address. Use the officially recommended chirpy-starter rather than maintaining a fork of the theme source.

Import the starter's Jekyll entry point, theme dependency, configuration, tabs, plugin, data, tools, license, and deployment workflow. Set Korean UI, Asia/Seoul timezone, PT3000 identity, and an empty baseurl. Retain system light/dark preference and the theme's responsive layout. Remove example social identities; show only GitHub and RSS contacts. The About page should identify this as PT3000's blog without inventing personal details. Do not publish invented posts.

Use the theme gem's compiled assets and default CDN dependencies; the optional assets submodule is unnecessary. Preserve upstream licensing. Document post creation and local preview in a Korean README.

GitHub Actions builds Jekyll and runs the upstream HTMLProofer internal-link check on pull requests before publication. Only main can deploy. Switch Pages from legacy branch builds to Actions once the proposed build passes, then publish and check the live homepage, tabs, CSS, and JavaScript. Ruby is unavailable locally, so use the Linux Actions runner for the actual build. Run UTF-8 validation and git diff checks locally.
