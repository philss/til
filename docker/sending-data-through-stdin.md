# Sending data to a Docker container through STDIN

This is a very useful technique to get data from STDIN using pipes or redirection ( << ).

Suppose you have a Postgres container in development running on Docker.
You want to copy some table to the local database from production, and production is a Heroku app.

You can do:

```
$ heroku pg:psql -c "COPY (SELECT * from table) TO STDOUT" | docker exec -i my_container /usr/bin/psql -h db -U postgres -d my_db -c "COPY table FROM STDIN"
```

Awesome!

The key here is that we are piping the contents of the output of heroku psql command and
using the `docker exec` with the -i (--interactive) flag that keeps the STDIN open to receive that
content.

You can also do redirection, like this:

```
$ docker exec -i my_container /usr/bin/psql -h db -U postgres -d my_db -c "COPY table FROM STDIN" < dumps/table.dump
```

