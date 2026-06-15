# @aauth/proxy

## Publishing a new version

Never run `npm publish` locally. Publishing goes through GitHub Actions with OIDC trusted publishing and signed provenance attestation.

**Release flow:**

1. Bump `version` in `package.json`, commit, and push to `main`.
2. Tag the commit to match:
   ```
   git tag v0.2.1 && git push origin v0.2.1
   ```
3. The `publish.yml` workflow triggers on the `v*.*.*` tag, runs `typecheck` + `test`, then publishes with `--provenance` via npm OIDC (no stored token needed).
