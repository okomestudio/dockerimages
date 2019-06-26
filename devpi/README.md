# devpi

Build an image:

```bash
$ docker-compose -f docker-compose-build.yml build dev
```

The very first container run will initialize the `devpi`
server. Supply the server root password and directory:

```bash
$ docker run -e 'DEVPI_ROOT_PASSWORD=mypassword' \
             -v "/local/path/to/serverdir:/data/server" \
             -p 3141:3141 \
             okomestudio/devpi:latest
```

Subsequent runs will not need the root password, so long as the same
server directory is used:

```bash
$ docker run -v "/local/path/to/serverdir:/data/server" \
             -p 3141:3141 \
             okomestudio/devpi:latest
```
