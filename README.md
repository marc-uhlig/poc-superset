# poc-superset

* [Install superset](https://superset.apache.org/docs/installation/docker-compose)
* Docker compose problem with version 24.x:
    * `env_file` key in `superset/docker-compose.yml`: change to `env_file: docker/.env`
* `docker compose up -d`
* Port `5432` must be free (Postgres)
    * check for local running Postgres server
* login with `admin` / pw `admin`