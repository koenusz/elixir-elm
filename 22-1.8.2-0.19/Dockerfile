FROM elixir:1.8.2-otp-22

MAINTAINER Koen van Dijk <kjw.vandijk@gmail.com>

curl -sL https://deb.nodesource.com/setup_10.x | bash -
apt-get install -y nodejs



RUN curl -sL https://deb.nodesource.com/setup_11.x | bash - apt-get install -y nodejs \
    && npm install -g elm@0.19.0-bugfix2 \

ENTRYPOINT ["elm"]
