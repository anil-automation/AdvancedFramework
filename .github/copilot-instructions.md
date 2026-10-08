# GitHub Copilot Instructions

## Hard rule: test checks

After any test-file change under `src/tests/**`—including adding, modifying, or deleting a test file—you must run:

```sh
npm run typecheck
npm run lint
```

Both commands must complete successfully with exit code 0 before reporting the work as complete. If either command fails, fix the issue and rerun both checks. Do not claim a check passed unless it was run.

The project currently does not define `typecheck` or `lint` npm scripts. If either command is unavailable, report that clearly rather than treating the checks as passed.
