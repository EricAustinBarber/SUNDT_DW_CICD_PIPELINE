# Production Readiness Checklist

Use this checklist before handing the platform and consuming repositories to the Data Engineering team for production operations.

## Signoff

- Owner:
- Date:
- Repository:
- Release/Commit:
- Approvers:
  - Data Platform:
  - DevOps:
  - Data Engineering:

## 1) Workflow health

- [ ] `ci-platform` is passing on `dev`, `test`, `prod`, and `main`
- [ ] Required jobs are passing:
  - [ ] `workflow-lint`
  - [ ] `yaml-lint`
  - [ ] `docs-guard`

## 2) Branch protection

- [ ] Branch protection is configured for `dev`, `test`, `prod`, and `main`
- [ ] Pull request required before merge
- [ ] Stale approvals dismissed on new commits
- [ ] Force pushes blocked
- [ ] Branch deletion blocked
- [ ] CODEOWNERS review required
- [ ] Required checks configured:
  - [ ] `workflow-lint`
  - [ ] `yaml-lint`
  - [ ] `docs-guard`
- [ ] `prod` and `main` require branch up to date before merge

## 3) CODEOWNERS routing

- [ ] `.github/CODEOWNERS` points to active teams/users with write access
- [ ] Test PR confirms automatic CODEOWNERS review requests for workflow/doc changes

## 4) GitHub Environments and approvals

- [ ] `DataBricks-Dev` exists
- [ ] `DataBricks-Test` exists
- [ ] `DataBricks-Prod` exists
- [ ] Approval policy verified:
  - [ ] Dev: no manual approval
  - [ ] Test: optional manual approval
  - [ ] Prod: required manual approval

## 5) Secrets and identity

- [ ] Required environment secrets are configured:
  - [ ] `DATABRICKS_HOST`
  - [ ] `DATABRICKS_TOKEN` (or OIDC equivalent)
- [ ] Optional secrets configured when used:
  - [ ] `DATABRICKS_VALIDATION_CLUSTER_ID`
  - [ ] `DATABRICKS_SQL_WAREHOUSE_ID`
- [ ] Secret names match workflow expectations exactly
- [ ] Credential rotation owner and cadence are documented
- [ ] OIDC federation plan is approved (or already implemented)

## 6) End-to-end execution checks

- [ ] `dev` flow validated (`ci-dev`)
- [ ] `test` flow validated (`ci-test` with validation/smoke settings as configured)
- [ ] `prod` flow validated by PR `test` -> `prod` and merge
- [ ] `cd-prod` confirmed to run only on `prod` push
- [ ] Environment approval gate confirmed on `DataBricks-Prod`

## 7) Databricks compute mapping

- [ ] Validation cluster IDs are confirmed for each environment:
  - [ ] Dev: `0720-012626-pen66ygb`
  - [ ] Test: `0720-015200-svl8c91v`
  - [ ] Prod: `0720-160151-np5pb9p5`
- [ ] SQL warehouse IDs are confirmed for each environment (if SQL smoke enabled):
  - [ ] Dev: `0ce33986b0810363`
  - [ ] Test: `df378c87894172b0`
  - [ ] Prod: `0e60233a0ac64392`

## 8) Security controls

- [ ] Secret scanning enabled
- [ ] Push protection enabled
- [ ] Dependabot alerts enabled
- [ ] Dependabot security updates enabled
- [ ] `.github/dependabot.yml` schedules are active

## 9) Rollback readiness

- [ ] Rollback runbook reviewed: `docs/runbooks/prod-rollback.md`
- [ ] Last-known-good release identification method confirmed
- [ ] Rollback drill performed (tabletop or execution) and documented
- [ ] Post-rollback smoke validation steps confirmed

## 10) Observability and auditability

- [ ] Deployments can be traced end-to-end:
  - [ ] GitHub run ID
  - [ ] Commit SHA
  - [ ] Databricks run IDs
  - [ ] Environment target
- [ ] Logs verified to avoid secret disclosure

## 11) Handoff package

- [ ] `docs/architecture.md` shared
- [ ] `docs/branching-and-promotion.md` shared
- [ ] `docs/security-and-secrets.md` shared
- [ ] `docs/branch-protection-checklist.md` shared
- [ ] `docs/workflow-validation-runbook.md` shared
- [ ] `docs/runbooks/failed-ci-test.md` shared
- [ ] `docs/runbooks/prod-rollback.md` shared
- [ ] Operating ownership and escalation path documented
