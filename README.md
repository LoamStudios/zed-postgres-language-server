# Postgres Language Server for Zed

To install navigate to: **Zed** > **Extensions**. Or use the command palette ([macOS](https://github.com/zed-industries/zed/blob/main/assets/keymaps/default-macos.json#L581), [Linux](https://github.com/zed-industries/zed/blob/main/assets/keymaps/default-linux.json#L459)) to search `extensions`.

This extension integrates the [Postgresql Language Server](https://github.com/supabase-community/postgres-language-server).

## Project Setup

The language server will not provide diagnostics, autocomplete, or hover until it finds a configuration file. **You must create a `postgres-language-server.jsonc` file at the root of your project** and fill in your database connection details.

### 1. Create `postgres-language-server.jsonc` at the project root

```jsonc
{
  "$schema": "https://pg-language-server.com/latest/schema.json",
  "linter": {
    "enabled": true,
    "rules": {
      "recommended": true
    }
  },
  "db": {
    "host": "127.0.0.1",
    "port": 5432,
    "username": "postgres",
    "password": "postgres",
    "database": "postgres",
    "connTimeoutSecs": 10,
    "allowStatementExecutionsAgainst": ["127.0.0.1/*", "localhost/*"]
  }
}
```

Replace the values under `db` with your own connection details. Use the discrete fields shown above.

### 2. Reload Zed

Reopen the workspace (or restart Zed) so the language server picks up the new configuration.

For the full configuration reference (linter rules, formatter, type checking, etc.) see the upstream [Postgres Language Server documentation](https://pg-language-server.com/latest/).
