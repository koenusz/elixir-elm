FROM elixir:1.8.2-otp-22

MAINTAINER Koen van Dijk <kjw.vandijk@gmail.com>

RUN curl -sL https://deb.nodesource.com/setup_11.x | bash - apt-get install -y nodejs \
    && npm install -g elm 
    
ENTRYPOINT ["elm"]
