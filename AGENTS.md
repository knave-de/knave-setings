# Knave Settings Agent Instructions

Knave Settings is the desktop settings application for the Knave Desktop
Environment. Keep changes focused on this repository. The application can be
run and reviewed directly in this checkout; do not require a multi-repository
development workspace or a VNC setup.

## Startup and investigation

Before editing:

1. Read this file and the relevant project documentation.
2. Inspect the repository status and preserve unrelated user changes.
3. Inspect the complete module or feature being changed and search for its
   consumers.
4. Identify whether the change affects application behavior, configuration,
   dependencies, packaging, or user-facing documentation.
5. For changes that affect a shared Knave contract, inspect the contract and
   its consumers before editing. Keep cross-repository coordination out of
   routine local work; document any actual dependency when one is needed.

## Product and implementation guidance

- Keep the settings application focused on editing Knave settings through the
  supported configuration or desktop APIs. Do not create a competing source
  of user configuration.
- Preserve existing user settings and report validation errors clearly.
- Keep README instructions short, accurate, and executable. Do not document
  commands or behavior that have not been verified.
- Prefer small, focused changes. Comments should explain invariants or
  non-obvious reasons rather than restating the code.

## Git and GitHub workflow

- Create a focused branch for each task and preserve unrelated working-tree
  changes.
- Use Conventional Commits, commit coherent changes when the task calls for a
  commit, and inspect the complete diff before committing.
- When the user asks to merge a branch or pull request, treat that as
  authorization to squash-merge it and delete the merged source branch. Do not
  merge without an explicit user request. Passing checks or approving a pull
  request does not authorize a merge.
- Before committing, verify the effective author and committer with
  `git var GIT_AUTHOR_IDENT` and `git var GIT_COMMITTER_IDENT`. Use the human
  contributor's established identity; never invent an identity or add
  assistant attribution.
- After committing, inspect the complete commit with
  `git show --no-patch --format=fuller HEAD`. Before pushing, review all
  outgoing commits. Do not push or publish unless the user requested it.

## Verification

- Run the checks relevant to the changed code. Do not add or run unrelated
  expensive checks without a task reason.
- For documentation-only changes, inspect the rendered text and run
  `git diff --check`; a build is unnecessary.
- For application behavior changes, run the app directly from this checkout
  when practical and verify the affected interaction. Do not require a remote
  desktop, VNC, or SSH tunnel for ordinary app checks.
- Inspect the final diff, check generated and untracked files, and report any
  behavior that was not verified.
