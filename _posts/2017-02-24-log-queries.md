When using an ORM such as SQLAlchemy, it is often necessary to view
the actual queries that are being sent to the database, in this case
Postgres. NB: Turning SQLAlchemy logging on does not show you the
actual queries sent. It is a useful feature, but if you want to see how
advanced features are actually working, it is better to look at what
the database is receiving.

With SQLAlchemy, you can simply issue a per-session call to the database:

    db.session.execute("SELECT set_config('log_min_duration_statement', '0', true)")

Using the offical Docker Postgres image, you can simply look at the
Docker logs, and you will now see queries that are slower than '0',
which, is of course all queries.

    $ docker logs -f <your_postgres_container>
