#
# Nasqueron - Jenkins slave Docker image for PHP applications
#

FROM nasqueron/php-cli
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#

RUN apt-get update && apt-get install -y \
            openjdk-7-jdk ant openssh-server openssh-client locales \
            mercurial subversion \
            --no-install-recommends && rm -r /var/lib/apt/lists/* && \
    cd /opt && wget https://phar.phpunit.de/phpunit.phar && \
    chmod +x phpunit.phar && ln -s /opt/phpunit.phar /usr/local/bin/phpunit && \
    wget https://phar.phpunit.de/phpcpd.phar && \
    chmod +x phpcpd.phar && ln -s /opt/phpcpd.phar /usr/local/bin/phpcpd && \
    wget https://phar.phpunit.de/phploc.phar && \
    chmod +x phploc.phar && ln -s /opt/phploc.phar /usr/local/bin/phploc && \
    wget https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && \
    chmod +x phpcs.phar && ln -s /opt/phpcs.phar /usr/local/bin/phpcs && \
    wget http://phpdox.de/releases/phpdox.phar && \
    chmod +x phpdox.phar && ln -s /opt/phpdox.phar /usr/local/bin/phpdox && \
    wget http://static.pdepend.org/php/latest/pdepend.phar && \
    chmod +x pdepend.phar && ln -s /opt/pdepend.phar /usr/local/bin/pdepend && \
    wget http://static.phpmd.org/php/latest/phpmd.phar && \
    chmod +x /opt/phpmd.phar && ln -s /opt/phpmd.phar /usr/local/bin/phpmd && \
    git clone https://github.com/phacility/libphutil.git && \
    git clone https://github.com/phacility/arcanist.git && \
    ln -s /opt/arcanist/bin/arc /usr/local/bin/arc && \
    mkdir -p /var/run/sshd && \
    sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    echo 'LANG="en_US.UTF-8"' > /etc/default/locale && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=en_US.UTF-8

#
# Docker properties
#

ENV LANG en_US.UTF-8

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
