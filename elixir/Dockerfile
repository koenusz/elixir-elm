FROM kjwvandijk:erlang

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

ENV ELIXIR_VERSION=1.9.0

RUN set -xe \
    && wget https://github.com/elixir-lang/elixir/archive/${ELIXIR_VERSION}.tar.gz \
    && tar -xzf \
    && cd ${ELIXIR_VERSION} \
    && make \
    && export PATH=`pwd`/bin:$PATH 



CMD ["iex"]