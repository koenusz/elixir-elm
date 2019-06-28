FROM kjwvandijk:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"


ENV NODE_VERSION=11

RUN set xe \
    && apt-get update \
    && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | sudo -E bash - \
    && apt-get install -y nodejs

CMD [ "node" ]