# SUNDT_DW_CICD_PIPELINE

Centralized CI/CD platform repository for Sundt Data Warehouse deployments.

## Purpose

This repository provides reusable GitHub Actions workflows, deployment controls, and operational runbooks for Databricks Asset Bundle delivery.

## Goals
- Enable safe, repeatable, and auditable Databricks deployments
- Enforce automated validation before production promotion
- Reduce manual deployment effort and production incidents
- Standardize CI/CD practices across data warehouse repositories

## What lives here
- Reusable GitHub Actions workflows (`.github/workflows`)
- Example consuming workflow templates (`examples/consuming-repo`)
- Security and operations documentation (`docs/`)

## What does not live here
- Business transformation logic
- Domain-specific Databricks notebooks from product teams
- Environment-specific secret values

## Branching and promotion model
- Feature branches -> PR -> `dev`
- `test` branch runs integration checks and validation gates
- `prod` deploys only after controlled promotion and approvals

See `docs/branching-and-promotion.md` for details.
See `docs/branch-protection-checklist.md` for branch and approval controls.
See `docs/workflow-validation-runbook.md` for dev/test validation runs.

## Security model
- No plaintext secrets in source control
- GitHub Environment scoping for deployment credentials
- Runtime data secrets resolved from Azure Key Vault where possible

See `docs/security-and-secrets.md` for the detailed model.

## Current status

Reusable Databricks workflow foundation is in place and ready for consuming repositories.
