FROM kjwvandijk/elixir-elm:erlang

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

ENV ELIXIR_VERSION=1.11.2 \
    ELIXIR_SHA256="318f0a6cb372186b0cf45d2e9c9889b4c9e941643fd67ca0ab1ec32710ab6bf5"

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y locales \
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && dpkg-reconfigure --frontend=noninteractive locales \
    && update-locale LANG=en_US.UTF-8

ENV LANG en_US.UTF-8 
ENV LC_ALL en_US.UTF-8

RUN set -xe \
    && wget https://github.com/elixir-lang/elixir/archive/v${ELIXIR_VERSION}.tar.gz \
    && echo "$ELIXIR_SHA256 v${ELIXIR_VERSION}.tar.gz" | sha256sum -c - \
    && tar -xzf v${ELIXIR_VERSION}.tar.gz \
    && rm v${ELIXIR_VERSION}.tar.gz \
    && cd elixir-${ELIXIR_VERSION} \
    && make \
    && ln -s /elixir-${ELIXIR_VERSION}/bin/mix /usr/local/bin/mix \
    && ln -s /elixir-${ELIXIR_VERSION}/bin/iex /usr/local/bin/iex \
    && ln -s /elixir-${ELIXIR_VERSION}/bin/elixir /usr/local/bin/elixir \
    && ln -s /elixir-${ELIXIR_VERSION}/bin/elixirc /usr/local/bin/elixirc 

RUN mix local.hex --force
RUN mix local.rebar --force
 
CMD ["/bin/bash"]