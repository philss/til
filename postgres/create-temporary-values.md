# Create temporary values with PostgreSQL

It is possible (and very useful) to create a temporary "table" in memory using Postgres.
You basically needs to use `with` along with `values`.

Example:

```sql
WITH temporary (key, value) AS (VALUES ('name', 'Philip'), ('lang', 'Elixir'))
SELECT * FROM temporary;
```

From: https://dba.stackexchange.com/a/86726
