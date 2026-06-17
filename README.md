# jaffle-lightdash

A Jaffle Shop semantic layer defined with **Lightdash YAML** (the dbt-less
approach) instead of a dbt project. Models live in `lightdash/models/*.yml` and
point directly at warehouse tables via `sql_from`, with metrics and dimensions
declared at the top level of each file.

This is a test twin of `charliedowler/jaffle` (which uses dbt) used to compare
how Lightdash behaves — AI writeback / `editDbtProject`, project refresh, and
the semantic layer — when the source is Lightdash YAML rather than dbt.

## Layout

```
lightdash.config.yml        # warehouse type
lightdash/models/
  orders.yml                # sql_from: jaffle.orders
  customers.yml             # sql_from: jaffle.customers
  payments.yml              # sql_from: jaffle.payments
```

## Validate / deploy

```bash
lightdash lint
lightdash deploy --create --no-warehouse-credentials
```
