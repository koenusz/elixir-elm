FROM kjwvandijk/elixir-elm:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

ENV NODE_VERSION=12

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN set xe \
    && apt update \
    && apt install -y nodejs

CMD [ "/bin/bash" ]