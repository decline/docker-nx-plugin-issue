# Docker Nx plugin issue
When restarting a docker container with `docker compose restart`, it will keep hanging when running a `nx serve` command (without any log output).

This can be fixed by setting the environment variable `NX_ISOLATE_PLUGINS` to `false`.

## How to reproduce

1. Start docker container `docker compose up` and wait until app gets served.
2. Go to another terminal and run `docker compose restart`.
3. Go back to the first terminal => the application will hang

## How to fix

1. Stop docker container again with `docker compose down`
2. Uncomment environment variable `NX_ISOLATE_PLUGINS: false` in docker-compose.yml
3. Start docker container `docker compose up` and wait until app gets served.
4. Go to another terminal and run `docker compose restart`.
5. Go back to the first terminal => the application restarts successfully

