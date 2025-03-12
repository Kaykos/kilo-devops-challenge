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

2.Create a Docker container to run the server.

File `docker-compose.yml` already exists. Updated `enchantments-server.build.context` value to `./py/server` so the
service can properly run. Added `enchantments-server.ports` to be able to reach the Flask application
