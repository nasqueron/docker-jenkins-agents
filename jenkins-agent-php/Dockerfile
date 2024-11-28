#
# Nasqueron - Jenkins agent Docker image for PHP applications
#

FROM nasqueron/php-cli
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#

RUN apt-get update && \
    apt-get install -y ant openssh-server openssh-client locales \
            mercurial subversion \
            openjdk-17-jdk \
            --no-install-recommends && rm -r /var/lib/apt/lists/* && \
    cd /opt && wget -O phpunit.phar https://phar.phpunit.de/phpunit-10.2.phar && \
    chmod +x phpunit.phar && ln -s /opt/phpunit.phar /usr/local/bin/phpunit && \
    wget https://phar.phpunit.de/phpcpd.phar && \
    chmod +x phpcpd.phar && ln -s /opt/phpcpd.phar /usr/local/bin/phpcpd && \
    wget https://phar.phpunit.de/phploc.phar && \
    chmod +x phploc.phar && ln -s /opt/phploc.phar /usr/local/bin/phploc && \
    wget https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && \
    chmod +x phpcs.phar && ln -s /opt/phpcs.phar /usr/local/bin/phpcs && \
    git clone --depth 1 https://github.com/nasqueron/phpdox && \
    (cd phpdox && composer update) && ln -s /opt/phpdox/phpdox /usr/local/bin/phpdox && \
    wget https://github.com/pdepend/pdepend/releases/download/2.16.2/pdepend.phar && \
    chmod +x pdepend.phar && ln -s /opt/pdepend.phar /usr/local/bin/pdepend && \
    wget https://github.com/phpmd/phpmd/releases/download/2.15.0/phpmd.phar && \
    chmod +x /opt/phpmd.phar && ln -s /opt/phpmd.phar /usr/local/bin/phpmd && \
    wget https://github.com/phan/phan/releases/download/5.4.5/phan.phar && \
    chmod +x /opt/phan.phar && ln -s /opt/phan.phar /usr/local/bin/phan && \
    git clone https://github.com/phacility/arcanist.git && \
    ln -s /opt/arcanist/bin/arc /usr/local/bin/arc && \
    pecl install xdebug && \
    git clone https://github.com/nikic/php-ast.git && \
    cd /opt/php-ast && phpize && ./configure && make && make install && \
    curl -sL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g bower gulp csslint jsonlint jshint jscs eslint && \
    mkdir -p /var/run/sshd

COPY files /

#
# Docker properties
#

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
