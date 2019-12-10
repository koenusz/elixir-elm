FROM kjwvandijk/elixir-elm:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"


ENV NODE_VERSION=12

RUN sudo apt-get install node-gyp
RUN set xe \
    && apt-get update \
    && apt-get install -y npm

CMD [ "/bin/bash" ]