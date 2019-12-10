FROM kjwvandijk/elixir-elm:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"


ENV NODE_VERSION=12

RUN sudo apt-get install  nodejs-dev node-gyp libssl1.0-dev
RUN set xe \
    && apt-get update \
    && apt-get install -y npm

CMD [ "/bin/bash" ]