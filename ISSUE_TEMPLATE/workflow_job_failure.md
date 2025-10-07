# Issue Title: Workflow Job Fails Due to Repository Rule Violations on Push to Main

## Description:
A recent workflow job ([job logs](https://github.com/ShaftHQ/testng-archetype/actions/runs/18303467898/job/52115670964)) failed when trying to push changes to the `main` branch. The error encountered was:

```
remote: error: GH013: Repository rule violations found for refs/heads/main.
! [remote rejected] main -> main (push declined due to repository rule violations)
error: failed to push some refs to 'https://github.com/ShaftHQ/testng-archetype'
```

This indicates that the repository has branch protection rules or other push restrictions configured for `main`. These rules may require status checks, enforce pull requests, restrict commit authors, or impose other conditions that were not met by the workflow.

## Steps to Reproduce:
1. Trigger the workflow defined in `.github/workflows/sync-versions.yml` ("Sync Project Version with SHAFT Engine").
2. Observe that the workflow attempts a direct push to `main` after syncing the project version.
3. The push is rejected due to repository rule violations, causing the job to fail.

## Logs and References:
- Full job logs are available [here](https://github.com/ShaftHQ/testng-archetype/actions/runs/18303467898/job/52115670964) (ref: d0d6a44177b67532ca18d4d7edb89a292d000b34).
- Workflow file: `.github/workflows/sync-versions.yml`
- Repository rules: https://github.com/ShaftHQ/testng-archetype/rules?ref=refs%2Fheads%2Fmain

## Suggested Solution:
- Update the workflow so it does not push directly to `main`. Instead, create a pull request with the changes so that repository rules and protections are respected (example: use `peter-evans/create-pull-request` action).
- Review branch protection and repository rules to ensure the workflow complies.
- Document the required rules/checks for future contributors or workflow updates.

## Additional Context:
- The workflow attempted to sync the project version to `9.4.20251007` and committed this change, but was unable to push to `main` due to the restrictions.
- This issue can block automated updates and version syncing, impacting development velocity and CI/CD reliability.

---

Please investigate and resolve so automated project version syncing can function without violating repository rules.