FROM kjwvandijk/elixir-elm:elixir

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

# replace shell with bash so we can source files
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# update the repository sources list
# and install dependencies
RUN apt-get update \
    && apt-get install -y curl git \
    && apt-get -y autoclean

RUN adduser --shell /bin/bash --home /asdf --disabled-password asdf
ENV PATH="${PATH}:/asdf/.asdf/shims:/asdf/.asdf/bin"

USER asdf
WORKDIR /asdf

ENV NODE_VERSION 12.13.1
ENV ELM_VERSION 0.19.1


RUN git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.5 && \
    echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc && \
    echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc && \
    source ~/.bashrc && \
    asdf current

RUN source ~/.bashrc && \
    asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git && \
    bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring && \
    asdf install nodejs $NODE_VERSION && \
    asdf global nodejs $NODE_VERSION 

RUN source ~/.bashrc && \
    asdf plugin-add elm && \
    asdf install elm $ELM_VERSION && \
    asdf global elm $ELM_VERSION

RUN source ~/.bashrc && \
    asdf current

# confirm installation
RUN source ~/.bashrc && \
    node -v && \
    npm -v && \
    elm --version

CMD [ "/bin/bash" ]