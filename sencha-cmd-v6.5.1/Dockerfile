FROM ubuntu:latest

LABEL maintainer "Michael Outlaw"
LABEL Description="Used to compile ExtJS 6.5.1 applications"

RUN \
# Install dependencies
    apt-get update && apt-get install -y --no-install-recommends \
        unzip \
        zip \
        git \
        gulp \
        nodejs \
        npm \
        openjdk-8-jre-headless \
        openjdk-8-jdk && \
    npm install -g bower && \
# Remove cache
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Sencha Cmd
# This assumes that you've downloaded Sencha Cmd and it sits next to this Dockerfile.
COPY ./cmd-6.5.1-linux-64-no_jre.zip /tmp/.
WORKDIR /tmp
RUN unzip cmd-6.5.1-linux-64-no_jre.zip && \
    ./SenchaCmd-6.5.1.240-linux-amd64.sh -q && \
    rm /tmp/cmd-6.5.1-linux-64-no_jre.zip /tmp/SenchaCmd-6.5.1.240-linux-amd64.sh

# Sencha specific environment variables
ENV PATH ${PATH}:~/bin/Sencha/Cmd/6.5.1.240

# Set up access to the code
# Expecting a src mount point
VOLUME ["/src"]
WORKDIR /src

# Default CMD to run
CMD ["bash"]