DevoOps challenge

#### Docker
1. Create a Docker container to run the server.

Added `py/server/Dockerfile` to define server image.

Image can be built using:
```shell
docker build -t kilo-py-server py/server/.
```
Run container:
```shell
docker run --rm -p 8085:5001 kilo-py-server
```

2. Create a Docker container to run the server.

File `docker-compose.yml` already exists. Updated `enchantments-server.build.context` value to `./py/server` so the
service can properly run. Added `enchantments-server.ports` to be able to reach the Flask application

#### Database

1. Set up a postgres or mysql with docker and get that running.

`docker-compose.yml` already had a `postgres` service definition. Added `.env` file with:
```shell
postgresUser='enchantments'
postgresPassword='some_secure_password'
postgresDb='enchantments'
postgresHost='postgres'
```

3. Change the connector in app.py to use the postgres or mysql database.

Updated `app.py` to build new database connection URL for Postgres.

4.  Run the database from docker-compose.yml.

Database successfully runs when running all services.

5. Hook everything up with environment variables and get things working so you can query the server

⚠️⚠️ Python container fails to connect to database. The module `psycopg2` is not found by Python.
Even when installing the dependencies for `psycopg2` (in Dockerfile), seems that Poetry is not able to install the module.
There is a general error when adding any dependency via Poetry, the process fails installing greenlet: 
`Note: This error originates from the build backend, and is likely not a problem with poetry but with greenlet (2.0.1) not supporting PEP 517 builds.`
