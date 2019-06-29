FROM kjwvandijk/elixir-elm:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"


ENV NODE_VERSION=11

RUN set xe \
    && apt-get update \
    && apt-get install -y npm

CMD [ "npm" ]