# px-workflows-public

Public, generic reusable GitHub Actions workflows (`workflow_call`) for Polinom.io repos.

## Shared context
Polinom.io rules are synced into `.ai/` from px-context; edit them there. If your harness has not already loaded them, read these files before any task:
- `.ai/global.md`
- `.ai/company-public.md`
- `.ai/engineering/engineering.md`

## Architecture
- `.github/workflows/ci-node.yml`: pnpm install, typecheck, lint, test, build, `pnpm audit`.
- `.github/workflows/release-please.yml`: release PR and tag with a GitHub App token; read-only GITHUB_TOKEN.
- `.github/workflows/publish-node.yml`: publish a release tag to GitHub Packages (`packages: write`, only in repos that publish).
- `.github/workflows/release.yml`: releases this repo with its own `release-please.yml`; tags are `vX.Y.Z`.
- `.github/workflows/security.yml`: gitleaks and OSV-Scanner (pinned binaries, sha256-verified); `security-check.yml` runs it on this repo.
- `.github/workflows/pr-standard.yml`: PR title and body against the org PR template; `pr-standard-check.yml` checks this repo's PRs and tests it with fixtures.
- `.github/workflows/lint.yml`: actionlint on PRs that change `.github/`; bump its pinned version and sha256 by hand.
- `.github/dependabot.yml`: weekly updates of the pinned actions.

## Rules
- This repo is public: no internal detail (accounts, infrastructure, internal repo names, secret names).
- Pin every action by full commit SHA with a `# vX.Y.Z` comment.
- Least privilege: top-level `permissions: contents: read`; each job asks only for what it needs.
- Secrets are declared explicitly under `workflow_call.secrets`; callers never use `secrets: inherit`.
