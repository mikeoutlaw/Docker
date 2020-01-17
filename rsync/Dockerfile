FROM ubuntu:latest

LABEL maintainer "Michael Outlaw"
LABEL Description="Used to rsync directories"

RUN \
# Install dependencies
    apt-get update && apt-get install -y --no-install-recommends \
        ssh \
        rsync && \
# Remove cache
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Expecting a data mount point
VOLUME ["/data"]
WORKDIR /data

# Default CMD to run
CMD ["bash"]