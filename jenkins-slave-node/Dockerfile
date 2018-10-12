#
# Nasqueron - Jenkins slave Docker image for Node applications
#

FROM nasqueron/jenkins-slave-barebone
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#

RUN apt-get update && \
    apt-get install -y curl unzip git sudo python libssl-dev pkg-config build-essential \
                       cmake nano vim file wget && \
    curl -sL https://deb.nodesource.com/setup_9.x | bash && \
    apt-get install -y nodejs && \
    apt-get autoremove && apt-get clean && \
    npm install --unsafe-perm -g node-sass && \
    npm install --unsafe-perm -g spectacle-docs && \
    npm install -g yarn && \
    groupadd -r app -g 433 && \
    mkdir /home/app && \
    useradd -u 431 -r -g app -d /home/app -s /bin/sh -c "Default application account" app && \
    chown -R app:app /home/app && \
    chmod 711 /home/app
