FROM kjwvandijk/elixir-elm:erlang

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

ENV ELIXIR_VERSION=1.9.4

RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y locales \
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && dpkg-reconfigure --frontend=noninteractive locales \
    && update-locale LANG=en_US.UTF-8

ENV LANG en_US.UTF-8 
ENV LC_ALL en_US.UTF-8

RUN set -xe \
    && wget https://github.com/elixir-lang/elixir/archive/v${ELIXIR_VERSION}.tar.gz \
    && tar -xzf v${ELIXIR_VERSION}.tar.gz \
    && rm v${ELIXIR_VERSION}.tar.gz \
    && cd elixir-${ELIXIR_VERSION} \
    && make \
    && echo '\ export PATH=`pwd`/bin:$PATH' >> ~/.profile

CMD ["iex"]