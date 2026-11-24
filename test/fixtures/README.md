# Test fixtures

`osv-vulnerable/package-lock.json` pins lodash 4.17.15, which has known
vulnerabilities at CVSS >= 7. It is never installed: `security-check.yml` scans it
to prove that `security.yml` detects findings and applies the CVSS threshold.
The repo's own scan (`osv-path: .github`) leaves it out.
