# DeployGuard demo

Live demo of [DeployGuard](https://github.com/adnanmullani/DeployGuard), a GitHub Action that reviews infrastructure changes in every PR and flags deployment risk before merge.

`infra/main.tf` is a small, safe baseline. Open the pull requests to see what DeployGuard does:

- **A risky PR** ([#6](https://github.com/adnanmullani/DeployGuard-demo/pull/6)) makes the database public, turns off encryption and opens SSH to `0.0.0.0/0`. DeployGuard comments with the risk, blast radius and rollback plan, posts one-click fixes, and the check fails so the merge is blocked.
- **Apply the suggested fixes** in one batch and the check turns green, then the PR can be merged.

The whole setup is one step in [.github/workflows/deployguard.yml](.github/workflows/deployguard.yml):

```yaml
- uses: adnanmullani/DeployGuard@v1
  with:
    api-key: ${{ secrets.GEMINI_API_KEY }}
```

No real cloud account is used. Nothing here is ever applied.
