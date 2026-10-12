# Shared Workflows

The estate's single source of reusable GitHub Actions workflows and composite actions, edited once and consumed by every Rheged Studio repo through thin per-repo stubs.

## Language

### Layers

**Reusable workflow**:
A `reusable-*.yml` file in this repo that exposes a `workflow_call` trigger and holds the whole job. Each one is a coarse, Layer 2 bundle.
_Avoid_: Shared pipeline, template workflow

**Caller stub**:
The small workflow file in a consumer repo that owns the triggers, `permissions:` and concurrency, and delegates the job to a reusable workflow with `uses:`.
_Avoid_: Wrapper, consumer workflow, thin caller (outside prose that already uses it)

**Layer 1**:
The composite actions under `.github/actions/`, run as steps inside the calling job so splitting them costs no extra runner or install.
_Avoid_: Primitives, helper actions

**Layer 2**:
The coarse reusable workflows that compose Layer 1 actions and pay setup once per job.
_Avoid_: Pipelines, bundles (as a layer name)

**Composite action**:
A Layer 1 directory containing an `action.yml`, referenced cross-repo by SHA. `setup-project` must run before the others.
_Avoid_: Step library, mini-action

### Versioning

**Floating major tag**:
The lightweight `v1`, `v2` tag that `move-floating-major.yml` force-moves onto each stable release, so callers on `@v1` receive non-breaking releases with no SHA bump.
_Avoid_: Moving tag, latest tag, major alias

**Release tag**:
The permanent annotated `vX.Y.Z` tag that carries a release's audit trail, as opposed to the floating major.
_Avoid_: Version tag, pin tag

### Gates

**GO/NO GO**:
The check-run produced by an `if: always()` aggregator job that `needs:` every real CI job in a repo. It is the one required check that merges and releases wait on.
_Avoid_: Build gate, CI gate, Build & Lint

**Aggregator**:
The per-repo job named `GO/NO GO` that reads `toJSON(needs)` and succeeds only if every needed job passed. It lives in each consumer because only the repo can enumerate all its jobs.
_Avoid_: Roll-up job, status job

**Estate ruleset**:
The versioned GitHub ruleset JSON (`trunk.json`) that requires the `GO/NO GO` check pinned to the Actions integration, so a forged commit status cannot satisfy it.
_Avoid_: Branch protection, protection rules

### Lint and test lanes

**Lane**:
One independent check inside the `lint / Lint` or `build-test / Build & Test` job, such as ESLint, markdown, yaml or changelog. Each is switched on or off by an input.
_Avoid_: Stage, step group

**Centralised yamllint config**:
The `.yamllint.yml` held in this repo and injected by `lint-yaml`, so consumers share one rule set and their local config only feeds pre-commit.
_Avoid_: Shared yamllint file, org yamllint

### Changelog and config

**Enrich mode**:
The `mode: enrich` setting of `reusable-changelog-enrich.yml` for deploy targets. It fills post-merge metadata only and never stamps a version.
_Avoid_: Deploy mode

**Finalise mode**:
The `mode: finalise` setting for npm targets. It enriches every merge and stamps `version` when `package.json` carries an untagged release-please version.
_Avoid_: Release mode, stamp mode

**Repo config**:
A consumer's `infrastructure/repo-config.yaml`, allowlist-validated by `load-repo-config` into step outputs.
_Avoid_: Settings file, workflow config

**Fanned payload**:
Content distributed from the estate to consumer repos, such as skills bundles or `.coderabbit.yaml`, which `reusable-validate-payload.yml` checks is present. Callers must name the job `validate-payload`.
_Avoid_: Synced files, distributed config
