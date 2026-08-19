---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    labels: [documentation]
    draft: true
    max: 1
---

# Update GitHub Info

Keep Mona's GitHub Info website current with concise, practical updates from official GitHub sources.

## Required research

1. Read `notes/mona-notes.md`.
2. Use the `web-fetch` tool to fetch and read https://github.blog/latest/.
3. Use the `web-fetch` tool to fetch and read https://github.blog/changelog/.
4. Use the `web-fetch` tool to fetch and read https://awesome-copilot.github.com/workflows/.
5. Use the GitHub repository API tools to read repository guidance and reference files, including `README.md`, `site/content/github-info.md`, and any relevant files under `notes/`. Do not use the terminal, GitHub CLI, bash, or sandboxed shell commands for these repository reads.

## Update task

Review the fetched official sources, including Awesome Copilot workflows at https://awesome-copilot.github.com/workflows/, and update `site/content/github-info.md` only when there is a useful, well-supported change. Keep summaries short and practical for developers, cite the relevant GitHub Blog, Changelog, or Awesome Copilot source for every new item, and preserve the existing editorial structure.

Use the `edit` tool to make the file change. Then use the `create-pull-request` safe output to open a draft pull request containing the proposed update for Mona to review. Do not write directly to `main`. If no meaningful update is supported by the sources, do not create a pull request and report that no change was needed.
