nu-docker
==============
Simple docker for project's on Symfony.

# Installation

1. First, clone this repository:

```bash
$ git clone https://github.com/nugato/nu-docker.git
```

2. Create `.env` file from `.env.dist` file and set your environment settings

3. Build containers

```bash
$ docker-compose build
```

4. Run containers

```bash
$ docker-compose up -d
```

> You can enter into php container (ex. for using composer) using this command:
```bash
$ docker-compose exec php sh
```
# Environments variables

| Variable name | Description |
| ------ | ------ |
| PROJECT_NAME | The name of the project. Using for prefixing containers names |
| ROOT_PATH | Root path for your application |
| MARIADB_DATABASE | Default database in `mariadb` container |
| MARIADB_PASSWORD | Default password in `mariadb` container |
| MARIADB_EXTERNAL_PORT | External port for `mariadb` container |

# Read logs

You can access Nginx logs in the following directory on your host machine:

* `logs/nginx`

# Use xdebug!

To use xdebug change the line `"docker.host:127.0.0.1"` in docker-compose.yml and replace 127.0.0.1 with your machine ip addres.
If your IDE default port is not set to 5902 you should do that, too.

# Code license

You are free to use the code in this repository under the terms of the 0-clause BSD license. LICENSE contains a copy of this license.