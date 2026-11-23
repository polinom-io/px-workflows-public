# px-workflows-public

Polinom.io reusable GitHub Actions workflows. Call them pinned by full commit SHA:

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
| [`release-please.yml`](.github/workflows/release-please.yml) | Release PRs and tags with a GitHub App token; optional publish to GitHub Packages |

Inputs, required permissions and caller examples are in each file's header.
