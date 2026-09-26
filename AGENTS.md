# Zod to OpenAPI repository guide

`src/` implements Zod-to-OpenAPI conversion and version-specific generation; tests and type tests protect schema output and the exported TypeScript API. Preserve the distinction between OpenAPI 3.0 and 3.1 and the supported Zod major version. Don't apply instructions for a newer major to this checkout without inspecting the manifest.

Use npm with the tracked lockfile (`npm ci`); CI checks Node 16, 18, and 20. Installation's prepare script builds. `npm run build` runs Rollup, `npm run lint` is a Prettier check, and `npm test` includes Jest plus type tests. Type tests consume `dist/index.d.ts`, so build before interpreting their results. This lint command is formatting validation, not a separate semantic linter.

For conversion changes, use minimal Zod schemas and assert the generated document/refs for each affected OpenAPI version, plus type tests for public API changes. No service or credential is needed for normal library checks. Publishing hooks rebuild/package the library and are separate from validation; don't release merely to test generated declarations.

## Completing work

Carry the authorized change through the relevant checks and repair failures it causes. Make routine, reversible implementation choices using existing patterns; ask only when missing information, a material product decision, or an authorization boundary prevents the next step. Existing authorization remains valid within its scope. If blocked, name the exact action and missing prerequisite, retain concise evidence, and continue independent work.

Choose verification proportional to the change. For instructions or prose, inspect changed paths, links, and local instruction precedence and run `git diff --check -- <changed-paths>`; don't install dependencies or run the application solely for a prose edit. For behavior changes, exercise the affected behavior and applicable checks below, then broaden only for failures or unresolved risk. Report files changed, checks actually run and their results, commands only inspected, and remaining limitations. A build or source inspection alone does not prove runtime behavior. Continue through already-authorized follow-through; stop at explicit review checkpoints or boundaries requiring new authorization.
