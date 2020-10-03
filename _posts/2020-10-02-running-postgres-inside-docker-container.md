---
layout: post
title: Running PostgreSQL inside a docker container
date: 2020-10-02 12:29 -0500
---
After knowing about docker and how easy it is to use software without
installing, I always want to use a docker version of the software.

Recently I wanted to experiment with PostgreSQL, so naturally, I looked at
PostgreSQL docker image.

But didn't know how to do these things in a docker container
- How to create a database
- How to create a user
- How to set a password

I'll also describe how to persist data across container runs.
To set the database name, user and password you need to set `POSTGRES_DB`
`POSTGRES_USER`, `POSTGRES_PASSWORD` respectively.

These can be passed to the docker run command as below

    docker run --rm -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myuser -e POSTGRES_DB=mydb postgres

To keep your data even after the container exits, you need to use volumes. To create
a volume use the command

    docker volume create pgdata

Now to use the volume we've created modify the run command as below

    docker run --rm -v pgdata:/var/lib/postgresql/data -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myuser -e POSTGRES_DB=mydb postgres

If you want to connect to this container to run SQL queries, I suggest setting a
name to this container. You do this by passing `--name` switch with a value

    docker run --rm --name mypostgres \
    -v pgdata:/var/lib/postgresql/data \
    -e POSTGRES_PASSWORD=mysecretpassword \
    -e POSTGRES_USER=myuser \
    -e POSTGRES_DB=mydb postgres

Connect to the running instance with the following command

    $ docker exec -it mypostgres bash
    # psql -U postgres -d mydb
