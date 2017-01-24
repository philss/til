# Upgrade PostgreSQL on Mac

After upgrading with homebrew, you may need to upgrade the data files.
If you don't care about the previous data, just follow this.

## Saving the existing data directory

Move the current data directory to a directory easy to identify for future usage.

```
$ mv /usr/local/var/postgres /usr/local/var/postgres9.5
```

## Setup of new data directory

To start with a new database you need to make sure that postgres is not running,
and that the directory `/usr/local/var/postgres` does not exist.

After that, run:

```
$ initdb -D /usr/local/var/postgres
```

The database should be started again.

## Setting up the right permissions

Some scripts like the `mix ecto.create` (Elixir) requires the `postgres` user to have
permissions that allows database creation.

For that, you only need to login the database and type:

```
CREATE ROLE postgres LOGIN CREATEDB;
```

Done. You are now able to create databases and login. Check more info [here](http://www.phoenixframework.org/docs/mix-tasks#section--ecto-create-).

## Useful commands

- Start postgres: `$ launchctl start ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist`;
- Stop postgres: `$ launchctl stop ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist`;
- Enter postgres console: `$ psql postgres`.
