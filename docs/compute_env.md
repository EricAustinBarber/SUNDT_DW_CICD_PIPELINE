# Databricks Compute Inventory (Serverless Pipeline)

This platform is serverless-first for workflow jobs. Bundle jobs should use Databricks serverless workflow configuration (`environment_key` + `environments`) and should not rely on all-purpose cluster IDs.

## SQL warehouses (for SQL smoke checks)

Use these IDs when `run_sql_smoke=true` and `DATABRICKS_SQL_WAREHOUSE_ID` is required.

### Dev

- Name: `sql-warehouse-dw2023-dev-sdt`
- ID: `0ce33986b0810363`
- Type: Serverless
- Size: `2X-Small`
- Auto stop: `10 minutes`
- Scaling: `min 1`, `max 1`

### Test

- Name: `sql-warehouse-dw2023-test-sdt`
- ID: `df378c87894172b0`
- Type: Serverless
- Size: `Small`
- Auto stop: `30 minutes`
- Scaling: `min 1`, `max 2`

### Prod

- Name: `sql-warehouse-dw2023-prod-sdt`
- ID: `0e60233a0ac64392`
- Type: Serverless
- Size: `X-Small`
- Auto stop: `30 minutes`
- Scaling: `min 1`, `max 1`

## Legacy all-purpose clusters

All-purpose workspace clusters may still exist for interactive work, but they are not required by this CI/CD serverless workflow path.
