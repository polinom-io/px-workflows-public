# px-workflows-public

Polinom.io reusable GitHub Actions workflows. Releases are tagged `vX.Y.Z` (see [CHANGELOG.md](CHANGELOG.md)). On 0.x, breaking changes bump the minor version; 1.0.0 is cut deliberately with a `Release-As: 1.0.0` commit. Call them pinned by the full commit SHA of a release tag, with the version as a comment so Dependabot can update it:

```yaml
jobs:
  ci:
    permissions:
      contents: read
    uses: polinom-io/px-workflows-public/.github/workflows/ci-node.yml@<sha> # vX.Y.Z
```

| Workflow | Purpose |
|---|---|
| [`ci-node.yml`](.github/workflows/ci-node.yml) | pnpm + Node CI: typecheck, lint, test, build (each optional), `pnpm audit --audit-level high` |
| [`release-please.yml`](.github/workflows/release-please.yml) | Release PRs and tags with a GitHub App token |
| [`publish-node.yml`](.github/workflows/publish-node.yml) | Publish a release tag to GitHub Packages after the CI gates |
| [`security.yml`](.github/workflows/security.yml) | gitleaks over the full git history (`secrets` job) and OSV-Scanner on lockfiles, failing at CVSS >= 7 (`dependencies` job) |

Inputs, required permissions and caller examples are in each file's header.

## Security scans

Call `security.yml` on pull requests, pushes to main and a weekly schedule. It needs no secrets. The job names `secrets` and `dependencies` are stable, so you can make them required checks:

```yaml
on:
  pull_request:
  push:
    branches: [main]
  schedule:
    - cron: "0 6 * * 1"
permissions:
  contents: read
jobs:
  security:
    permissions:
      contents: read
    uses: polinom-io/px-workflows-public/.github/workflows/security.yml@<sha> # vX.Y.Z
    # with:
    #   osv-min-cvss: 7    # fail threshold
    #   osv-path: .        # directory scanned recursively
    #   osv-scan: false    # e.g. no dependencies at all
```

Repos without a lockfile pass the `dependencies` job with a skip message. Outputs `osv-result` (`none`, `skipped`, `found`), `osv-findings` and `osv-high` report what the scan saw. `osv-enforce: false` reports without failing; this repo's tests use it against `test/fixtures/` so the gate is proven to fire.

