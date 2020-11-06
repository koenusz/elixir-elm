FROM ubuntu:20.04

LABEL maintainer="Koen van Dijk <kjw.vandijk@gmail.com>"

ENV ERLANG_VERSION=23.1 \
    ERLANG_SHA1="21a76dce89882c2ee43f256e3594f17573a0d412" 
    
RUN set -xe \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get -y install curl wget build-essential autoconf m4 libncurses5-dev libwxgtk3.0-gtk3-dev libgl1-mesa-dev libglu1-mesa-dev libpng-dev libssh-dev unixodbc-dev \
    && export ROOT=`pwd` \
    && wget http://www.erlang.org/download/otp_src_${ERLANG_VERSION}.tar.gz \
    && echo "${ERLANG_SHA1}  otp_src_${ERLANG_VERSION}.tar.gz" | sha1sum -c - \
    && tar -zxf otp_src_${ERLANG_VERSION}.tar.gz \
    && rm otp_src_${ERLANG_VERSION}.tar.gz \
    && cd otp_src_${ERLANG_VERSION} \
    && export ERL_TOP=`pwd` \
    && cd $ROOT \
    # make erlang
    && cd $ERL_TOP \
    && ./configure \
    && export LANG=C \
    && make \
    && make release_tests \
    && cd release/tests/test_server \
    && $ERL_TOP/bin/erl -s ts install -s ts smoke_test batch -s init stop \
    && cd $ERL_TOP \
    && make install \
    # cleanup
    && cd $ROOT \
    && rm -rf otp_src_${ERLANG_VERSION}



CMD ["erl"]

ENV REBAR3_VERSION="3.14.1" \
    REBAR3_DOWNLOAD_SHA256="b01275b6cbdb354dcf9ed686fce2b5f9dfdd58972ded9e970e31b9215a8521f2"

RUN set -xe \
    && REBAR3_DOWNLOAD_URL="https://github.com/erlang/rebar3/archive/${REBAR3_VERSION}.tar.gz" \
    && mkdir -p /usr/src/rebar3-src \
    && curl -fSL -o rebar3-src.tar.gz "$REBAR3_DOWNLOAD_URL" \
    && echo "$REBAR3_DOWNLOAD_SHA256 rebar3-src.tar.gz" | sha256sum -c - \
    && tar -xzf rebar3-src.tar.gz -C /usr/src/rebar3-src --strip-components=1 \
    && rm rebar3-src.tar.gz \
    && cd /usr/src/rebar3-src \
    && HOME=$PWD ./bootstrap \
    && install -v ./rebar3 /usr/local/bin/ \
    && rm -rf /usr/src/rebar3-src