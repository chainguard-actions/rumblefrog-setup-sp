<!-- markdownlint-disable -->

# Hardening Report: rumblefrog--setup-sp/v1.3.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **rumblefrog--setup-sp/v1.3.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files use unpinned `uses:` references with mutable tags or branch names instead of full 40-character commit SHAs. In dev_workflow.yml: `uses: actions/checkout@v1` (tag). In workflow.yml: `uses: actions/checkout@v1` (tag) and `uses: rumblefrog/setup-sp@master` (branch). These can be silently updated by the upstream repository, enabling supply-chain attacks.

Locations:

- `.github/workflows/dev_workflow.yml:12`
- `.github/workflows/workflow.yml:12`
- `.github/workflows/workflow.yml:15`

### missing-permissions (severity: medium)

Neither workflow file defines a top-level `permissions:` key, and no job in either file defines a job-level `permissions:` key. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/dev_workflow.yml:1`
- `.github/workflows/workflow.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both workflow files: (1) Pinned actions/checkout@v1 to SHA 50fbc622fc4ef5163becd7fab6573eac35f8462e in both dev_workflow.yml and workflow.yml; pinned rumblefrog/setup-sp@master to SHA 99bd7a13a9abba3823345930178a635bac70fb89 in workflow.yml. (2) Added top-level `permissions: contents: read` block to both workflow files to enforce least-privilege token access.

