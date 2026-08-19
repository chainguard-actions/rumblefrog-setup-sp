<!-- markdownlint-disable -->

# Hardening Report: rumblefrog--setup-sp/v1.2.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **rumblefrog--setup-sp/v1.2.3** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow steps use mutable tag/branch refs instead of pinned full-length SHA commit hashes, making the action vulnerable to supply-chain attacks if the referenced tag or branch is moved or overwritten.

- `.github/workflows/dev_workflow.yml`: `uses: actions/checkout@v1` (tag `v1`, not a SHA)
- `.github/workflows/workflow.yml`: `uses: actions/checkout@v1` (tag `v1`, not a SHA)
- `.github/workflows/workflow.yml`: `uses: rumblefrog/setup-sp@master` (branch `master`, not a SHA)

All three should be pinned to a full 40-character hex commit SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/dev_workflow.yml:11`
- `.github/workflows/workflow.yml:11`
- `.github/workflows/workflow.yml:15`

### missing-permissions (severity: medium)

Neither workflow file defines a top-level `permissions:` block, and no job in either file defines its own `permissions:` block. Without explicit permissions, GitHub Actions grants the default token permissions (which may include `write` access to repository contents and other scopes depending on the organisation/repository settings), violating the principle of least privilege. A minimal `permissions: {}` or specific scopes (e.g. `contents: read`) should be added.

Locations:

- `.github/workflows/dev_workflow.yml:1`
- `.github/workflows/workflow.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both workflow files (.github/workflows/dev_workflow.yml and .github/workflows/workflow.yml):
1. Pinned actions/checkout@v1 to SHA 50fbc622fc4ef5163becd7fab6573eac35f8462e in both files.
2. Pinned rumblefrog/setup-sp@master to SHA 99bd7a13a9abba3823345930178a635bac70fb89 in workflow.yml.
3. Added top-level `permissions: {}` block to both workflow files to enforce least privilege and prevent default write access.

