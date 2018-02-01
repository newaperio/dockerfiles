# Dockerfiles

This repo contains the Dockerfiles we use at [NewAperio](https://newaperio.com).

## Elixir / CircleCI

[![DockerHub](https://img.shields.io/badge/dockerhub-latest-brightgreen.svg)](https://hub.docker.com/r/newaperio/elixir-circleci/)

An image for building Elixir apps on CircleCI.

* Sets `MIX_ENV` to `test`
* Includes Hex, Rebar
* Sets up Postgres CLI
* Installs CodeClimate reporter

To build:

```bash
docker build -t newaperio/elixir-circleci:1.6.0 --build-arg version=1.6.0 .
```

To publish:

```bash
docker push newaperio/elixir-circleci:1.6.0
```

_Note, Elixir version must be passed as the `version` build arg._

### Versions

Image is versioned equal to Elixir version starting with v1.6.0.

* 0.0.1 - Elixir 1.5.3
* 1.6.0 - Elixir 1.6.0
