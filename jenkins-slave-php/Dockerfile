#
# Nasqueron - Jenkins slave Docker image for PHP applications
#

FROM nasqueron/php-cli
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#

RUN echo "deb http://http.debian.net/debian jessie-backports main" > /etc/apt/sources.list.d/jessie-backports.list && \
    apt-get update && apt-get install -y -t jessie-backports openjdk-8-jdk \
            --no-install-recommends && \
    apt-get install -y ant openssh-server openssh-client locales \
            mercurial subversion \
            --no-install-recommends && rm -r /var/lib/apt/lists/* && \
    cd /opt && wget -O phpunit.phar https://phar.phpunit.de/phpunit-5.7.phar && \
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
    wget https://github.com/etsy/phan/releases/download/0.7/phan.phar && \
    chmod +x /opt/phan.phar && ln -s /opt/phan.phar /usr/local/bin/phan && \
    git clone https://github.com/phacility/libphutil.git && \
    git clone https://github.com/phacility/arcanist.git && \
    ln -s /opt/arcanist/bin/arc /usr/local/bin/arc && \
    pecl install xdebug && \
    git clone https://github.com/nikic/php-ast.git && \
    cd /opt/php-ast && phpize && ./configure && make && make install && \
    curl -sL https://deb.nodesource.com/setup_4.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g bower gulp csslint jsonlint jshint jscs eslint phantomjs-prebuilt && \
    mkdir -p /var/run/sshd

COPY files /

#
# Docker properties
#

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
