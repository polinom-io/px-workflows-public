# px-workflows-public

Public, generic reusable GitHub Actions workflows (`workflow_call`) for Polinom.io repos.

## Shared context
Polinom.io rules are synced into `.ai/` from px-context; edit them there. If your harness has not already loaded them, read these files before any task:
- `.ai/global.md`
- `.ai/company-public.md`
- `.ai/engineering/engineering.md`

## Architecture
- `.github/workflows/ci-node.yml`: pnpm install, typecheck, lint, test, build, `pnpm audit`.
- `.github/workflows/release-please.yml`: release PR with a GitHub App token; optional publish to GitHub Packages.
- `.github/workflows/release.yml`: releases this repo with its own `release-please.yml`; tags are `vX.Y.Z`.
- `.github/dependabot.yml`: weekly updates of the pinned actions.

## Rules
- This repo is public: no internal detail (accounts, infrastructure, internal repo names, secret names).
- Pin every action by full commit SHA with a `# vX.Y.Z` comment.
- Least privilege: top-level `permissions: contents: read`; each job asks only for what it needs.
- Secrets are declared explicitly under `workflow_call.secrets`; callers never use `secrets: inherit`.
