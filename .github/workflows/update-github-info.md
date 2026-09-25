---
name: update-github-info
model: gpt-5.4
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
tools:
  github:
    mode: remote
    toolsets: [repos]
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical guidance for developers.

1. Read `notes/mona-notes.md` and `site/content/github-info.md` before making any changes.
2. Use `web-fetch` to read https://github.blog/latest/, https://github.blog/changelog/, and https://awesome-copilot.github.com/workflows/.
3. Use the GitHub repository API tools to read any repository guidance or reference files needed to understand the website and its content conventions. Do not use terminal, CLI, or sandboxed commands for that repository guidance.
4. Select only useful, recent updates that fit Mona's editorial angle. Keep summaries short and practical, and cite whether each update came from the GitHub Blog or GitHub Changelog.
5. Edit `site/content/github-info.md` with the selected updates. Preserve the existing structure and do not change unrelated content.
6. Review the resulting change for accuracy, source attribution, and concise wording.
7. Use the `create-pull-request` safe output to open one pull request containing the proposed update for Mona to review. Do not write directly to the default branch. Include a summary of the updates and their official source URLs in the pull request body.