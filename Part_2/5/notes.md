# Notes
There's no need to supply commands for redis persistance
as defined in documentation in https://hub.docker.com/_/redis/
`$ docker run --name some-redis -d redis redis-server --appendonly yes`.
Command args that activates persistance is `redis-server` and it's included
in image CMD. We do leave out `--appendonly` to it's defaults so new changes
are probably overwriting.

Regardless, submitted docker-compose.yml in this directory will enable app
to respond to /slow within 1 second. The button in web-ui turns green too.
