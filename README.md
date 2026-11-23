# px-workflows-public

Polinom.io reusable GitHub Actions workflows. Releases are tagged `vX.Y.Z` (see [CHANGELOG.md](CHANGELOG.md)). Call them pinned by the full commit SHA of a release tag, with the version as a comment so Dependabot can update it:

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

Inputs, required permissions and caller examples are in each file's header.
