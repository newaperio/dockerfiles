ARG version

FROM elixir:${version}

LABEL description="Image for running Elixir on CircleCI with reporting to \
  CodeClimate" \
  maintainer="NewAperio <hello@newaperio.com>" \
  vcs-url="https://github.com/newaperio/dockerfiles/" \
  vendor="NewAperio" \
  version=${version}

ENV DOCKERIZE_VERSION=v0.6.0
ENV MIX_ENV=test

# Install Hex and Rebar
RUN mix do local.hex --force, local.rebar

# Install Dockerize
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
  && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
  && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

# Install Postgres CLI
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" > /etc/apt/sources.list.d/pgdg.list
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN apt-get update; apt-get install -y postgresql-client-10

# Install CodeClimate reporter
ADD https://codeclimate.com/downloads/test-reporter/test-reporter-latest-linux-amd64 /usr/local/bin/cc-test-reporter
RUN chmod +x /usr/local/bin/cc-test-reporter
