#
# Nasqueron - Jenkins agent Docker image for Node applications
#

FROM nasqueron/jenkins-agent-barebone
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#

RUN apt-get update && \
    apt-get install -y curl unzip git sudo python libssl-dev pkg-config build-essential \
                       cmake nano vim file wget && \
    curl -sL https://deb.nodesource.com/setup_19.x | bash - && \
    apt-get install -y nodejs && \
    apt-get autoremove && apt-get clean && \
    npm install -g yarn && \
    cd /opt && git clone https://github.com/nasqueron/spectacle && cd spectacle && yarn install && \
    ln -s /opt/spectacle/bin/spectacle.js /usr/local/bin/spectacle && \
    groupadd -r app -g 433 && \
    mkdir /home/app && \
    useradd -u 431 -r -g app -d /home/app -s /bin/sh -c "Default application account" app && \
    chown -R app:app /home/app && \
    chmod 711 /home/app
