# base
FROM debian:bookworm-slim
ENV DEBIAN_FRONTEND noninteractive

# set the github runner version
ARG RUNNER_VERSION="2.317.0"

RUN mkdir /home/docker

RUN apt-get update -y && apt-get install -y --no-install-suggests --no-install-recommends \
    curl \
    ca-certificates \
    jq \
    git \
    && rm -rf /var/lib/apt/lists/*

# Add Docker's official GPG key:
RUN install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc \
    && chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
RUN echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update \
    && apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin \
    && rm -rf /var/lib/apt/lists/*

# cd into the user directory, download and unzip the github actions runner
RUN cd /home/docker && mkdir actions-runner && cd actions-runner \
    && curl -O -L https://github.com/actions/runner/releases/download/v${RUNNER_VERSION}/actions-runner-linux-x64-${RUNNER_VERSION}.tar.gz \
    && tar xzf ./actions-runner-linux-x64-${RUNNER_VERSION}.tar.gz \
    && rm *.tar.gz

RUN /home/docker/actions-runner/bin/installdependencies.sh

# copy over the entrypoint.sh script
COPY entrypoint.sh entrypoint.sh

# make the script executable
RUN chmod +x entrypoint.sh

# set the entrypoint to the entrypoint.sh script
ENTRYPOINT ["./entrypoint.sh"]